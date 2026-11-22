# Sistema de Recomendação de Transporte Público — API Olho Vivo

Projeto acadêmico em Python e Jupyter Notebook para recomendar uma viagem direta de ônibus entre duas coordenadas, utilizando a base GTFS e a API Olho Vivo da SPTrans.

## Arquivos
- `Sistema_Transporte_Olho_Vivo.ipynb`: notebook principal.
- `_gtfs.zip`: base de dados GTFS utilizada pelo projeto.
- `requirements.txt`: bibliotecas Python necessárias.
- `.env.example`: exemplo de configuração do token da SPTrans.
- `.gitignore`: evita publicar credenciais e arquivos temporários.

## Requisitos
- Python 3.10 ou superior.
- Jupyter Notebook.
- Token de acesso à API Olho Vivo da SPTrans.

## Instalação
Na pasta do projeto, execute:

```bash
py -m pip install -r requirements.txt
```

Crie um arquivo chamado `.env` a partir de `.env.example` e coloque seu token nele:

```text
SPTRANS_TOKEN=SEU_TOKEN_AQUI
```

**Nunca publique o arquivo `.env` nem compartilhe seu token.** O `.gitignore` está configurado para ignorar `.env`.

## Como executar
1. Abra o Jupyter Notebook na pasta do projeto.
2. Abra `Sistema_Transporte_Olho_Vivo.ipynb`.
3. Na seção **Configuração da consulta**, confira e substitua as coordenadas de exemplo pelas coordenadas definidas pelo grupo.
4. Escolha um raio de busca entre 1 e 1.000 metros.
5. Execute as células na ordem, de cima para baixo, ou use `Kernel > Restart & Run All`.
6. Confira a recomendação, a resposta da API e o mapa.

## Como o sistema funciona
- Carrega a base GTFS.
- Localiza paradas próximas da origem e do destino usando distância geográfica.
- Identifica viagens diretas cruzando `trip_id` e sequência de paradas.
- Classifica alternativas pela distância total a pé.
- Consulta a API Olho Vivo para validar informações operacionais e obter previsão oficial quando disponível.
- Exibe o trajeto em mapa interativo.

A previsão em tempo real depende da disponibilidade e da correspondência dos dados retornados pela API. O sistema não deve apresentar horários de tabela GTFS como se fossem previsões em tempo real.

## Documentação da API
https://www.sptrans.com.br/desenvolvedores/api-do-olho-vivo-guia-de-referencia/documentacao-api/

## Segurança
Não envie `.env`, tokens, senhas ou outras credenciais ao GitHub. Antes de publicar, confirme que o arquivo `.env` não está selecionado para envio.
