# Sistema de Recomendação de Transporte Público

Projeto em Python/Jupyter para encontrar uma viagem direta entre dois locais, usando GTFS e API Olho Vivo da SPTrans.

## Arquivos

- `notebooks/sistema_recomendacao.ipynb`: notebook principal, com o código do sistema.
- `dados/gtfs_sptrans.zip`: base GTFS utilizada.
- `mapas/`: local onde o mapa final será salvo.
- `.env.example`: modelo para configurar o token.
- `requirements.txt`: bibliotecas necessárias.
- `fluxograma.svg`: fluxo de funcionamento.

## 1. Preparar o ambiente no Windows

Instale o Python 3.10 ou superior e o Visual Studio Code com a extensão **Python** e **Jupyter**. Abra a pasta do projeto no VS Code.

No terminal do VS Code, execute: 

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Se o PowerShell bloquear a ativação do ambiente, use o terminal `Command Prompt` e execute `.venv\Scripts\activate.bat`.

## 2. Configurar o token

Copie `.env.example`, renomeie a cópia para `.env` e coloque o token da sua aplicação SPTrans: 

```text
SPTRANS_TOKEN=SEU_TOKEN
```

Não use aspas. Não envie o `.env` ao GitHub. O `.gitignore` já está preparado para ignorá-lo.

## 3. Executar no VS Code

1. Abra `notebooks/sistema_recomendacao.ipynb`.
2. No canto superior direito, selecione o kernel Python do ambiente `.venv`.
3. Execute as células na ordem.
4. Na seção de seleção, escolha **Origem** e clique no mapa. Depois escolha **Destino** e clique no segundo local.
5. Execute a célula seguinte para obter a recomendação e o mapa final.

Para usar endereços em vez do mapa, altere `MODO_ENTRADA` para `endereco` e edite `ENDERECO_ORIGEM` e `ENDERECO_DESTINO`. Para digitar coordenadas, use `MODO_ENTRADA = "coordenadas"` e preencha as duas variáveis de coordenadas.

O raio padrão é 500 metros. Pode ser alterado em `RAIO_BUSCA_METROS`, respeitando o intervalo de 1 a 1.000 metros.

## 4. Resultado

O notebook mostra a linha, o sentido, o embarque, o desembarque, as paradas intermediárias, as distâncias e a previsão quando a API disponibilizar o ponto correspondente. O mapa é exibido no notebook e salvo em `mapas/rota_recomendada.html`.

O traçado é retirado de `shapes.txt`. Se a forma não corresponder ao trecho na direção correta, o sistema não desenha um percurso aproximado como se fosse o real.

## 5. Limitações da API

A API Olho Vivo documenta a busca de linhas, paradas, previsão e posição dos veículos. A documentação informa que a categoria de paradas contempla atualmente apenas pontos de corredores. Por isso, uma linha pode ser localizada e ainda assim a previsão ficar indisponível quando o ponto de embarque não tiver correspondência na API. Nesse caso, o notebook informa que a previsão está indisponível.

Documentação: https://www.sptrans.com.br/desenvolvedores/api-do-olho-vivo-guia-de-referencia/documentacao-api/