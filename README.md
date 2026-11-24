# Sistema de Transporte Público — API Olho Vivo

Projeto acadêmico desenvolvido em Python e Jupyter Notebook para recomendar viagens diretas de ônibus na cidade de São Paulo.

O sistema utiliza dados GTFS e a API Olho Vivo da SPTrans para identificar pontos próximos, localizar linhas que atendem à viagem e consultar previsões de chegada dos veículos, quando disponíveis.

## Arquivos do projeto

- `Sistema_Transporte_Olho_Vivo_ENTREGA_ATUALIZADO.ipynb` — notebook principal com o código, processamento dos dados e visualização.
- `_gtfs.zip` — base de dados GTFS utilizada pelo projeto.
- `requirements.txt` — bibliotecas necessárias para execução.

## Funcionalidades

- Validação das coordenadas de origem e destino.
- Identificação de pontos de ônibus próximos.
- Busca de linhas e trajetos diretos, sem baldeação.
- Cálculo de distâncias entre os pontos.
- Identificação dos pontos de embarque e desembarque.
- Consulta à previsão de chegada pela API Olho Vivo.
- Visualização do trajeto em mapa interativo.
- Tratamento de erros e situações sem resultados.

## API Olho Vivo

O projeto utiliza a API Olho Vivo da SPTrans. Para consultar as previsões, é necessário informar um token válido.

O token deve ser inserido durante a execução do notebook e **não deve ser publicado no GitHub**.

A consulta de previsão depende da disponibilidade de correspondência entre os pontos do GTFS e os códigos oficiais de parada retornados pela API. Algumas paradas podem não estar disponíveis na consulta da categoria Paradas.

## Como executar

1. Baixe ou clone este repositório.
2. Instale as dependências:

   `pip install -r requirements.txt`

3. Abra o notebook no Jupyter.
4. Execute as células na ordem apresentada.
5. Quando solicitado, informe o token da API Olho Vivo.

## Tecnologias utilizadas

- Python
- Jupyter Notebook
- Pandas
- Requests
- Folium
- GTFS
- API Olho Vivo — SPTrans
