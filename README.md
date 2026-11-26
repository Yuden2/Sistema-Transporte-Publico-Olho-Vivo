# Sistema de Recomendação de Transporte Público

Projeto em Python/Jupyter para localizar uma viagem direta de ônibus em São Paulo usando a base GTFS e a API Olho Vivo da SPTrans.

## Arquivos

- `notebooks/sistema_recomendacao.ipynb`: notebook principal.
- `dados/gtfs_sptrans.zip`: base GTFS fornecida para o projeto.
- `mapas/`: pasta onde o notebook salva o mapa final em HTML.
- `requirements.txt`: bibliotecas necessárias.
- `.env.example`: modelo do token da API.
- `fluxograma.svg`: fluxograma do algoritmo.

## Preparar no Windows / VS Code

1. Extraia o ZIP e abra a pasta do projeto no VS Code.
2. No terminal do VS Code, execute:

```powershell
py -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

3. Copie `.env.example`, renomeie a cópia para `.env` e informe um token novo da SPTrans:

```text
SPTRANS_TOKEN=SEU_TOKEN
```

4. Abra `notebooks/sistema_recomendacao.ipynb`, selecione o kernel `.venv` e execute as células de cima para baixo.

## Como usar

Na seção de entrada, escolha endereço, coordenadas ou seleção no mapa. O controle **Raio (m)** começa em 500 e permite escolher qualquer valor entre 1 e 1.000 metros. Depois execute a seção de recomendação.

O programa procura uma viagem da mesma linha e viagem GTFS, verifica a ordem das paradas e usa `shapes.txt` para desenhar o trecho geográfico no sentido correto. O mapa final é exibido no notebook e salvo em `mapas/rota_recomendada.html`.

A recomendação estática vem do GTFS. A confirmação operacional, as posições e as previsões são consultadas na API. A previsão só é mostrada quando a API retorna uma parada oficial compatível; nenhum horário é inventado.

## Token

O arquivo `.env` não deve ser enviado ao GitHub. O `.gitignore` já o exclui. Como credenciais compartilhadas em conversas devem ser consideradas expostas, revogue o token anterior e use um novo gerado no portal SPTrans.

## Observação sobre as paradas da API

A documentação oficial informa que a busca de paradas da Olho Vivo contempla atualmente apenas paradas de corredores. Assim, pode existir uma linha GTFS válida sem correspondência de parada oficial para previsão. Nessa situação, o sistema mantém o resultado GTFS identificado como tal e informa que a previsão está indisponível.

Documentação: https://www.sptrans.com.br/desenvolvedores/api-do-olho-vivo-guia-de-referencia/documentacao-api/