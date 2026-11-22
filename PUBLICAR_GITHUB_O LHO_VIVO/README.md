# Sistema de Transporte Público — API Olho Vivo

Este projeto foi desenvolvido como atividade acadêmica e tem como objetivo encontrar opções de viagens de ônibus entre dois pontos da cidade de São Paulo.

O sistema utiliza Python, Jupyter Notebook, dados GTFS e a API Olho Vivo da SPTrans para localizar pontos de ônibus próximos, identificar linhas que fazem o trajeto direto e consultar informações sobre a previsão de chegada dos veículos.

## Arquivos do projeto

- `Sistema_Transporte_Olho_Vivo.ipynb` — arquivo principal, onde está o código do projeto.
- `_gtfs.zip` — base de dados utilizada para consultar linhas, viagens e pontos de ônibus.
- `requirements.txt` — lista das bibliotecas necessárias.
- `.env.example` — modelo para configurar o acesso à API.
- `.gitignore` — arquivo para evitar o envio de arquivos desnecessários e informações confidenciais.

## Como executar

É necessário ter Python e Jupyter Notebook instalados.

1. Baixe os arquivos do repositório.
2. Instale as bibliotecas com o comando:

```bash
py -m pip install -r requirements.txt
```

3. Configure o acesso à API Olho Vivo utilizando seu token em um arquivo `.env`.
4. Abra o notebook no Jupyter.
5. Informe as coordenadas de origem e destino.
6. Execute as células na ordem apresentada.

## O que o sistema faz

- Busca pontos de ônibus próximos à origem e ao destino.
- Verifica quais viagens permitem realizar o percurso sem baldeação.
- Identifica a linha e os pontos de embarque e desembarque.
- Consulta a API Olho Vivo para obter informações da linha e previsão de chegada, quando disponível.
- Apresenta o trajeto em um mapa.

## Observação

A previsão de chegada depende da disponibilidade das informações fornecidas pela API da SPTrans. Caso não haja dados disponíveis, o sistema informa essa condição.

## API utilizada

SPTrans — Olho Vivo:  
https://www.sptrans.com.br/desenvolvedores/api-do-olho-vivo-guia-de-referencia/documentacao-api/
