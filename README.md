🌤️ Projeto de Coleta de Dados — Clima das Capitais Brasileiras

Projeto desenvolvido para a disciplina Introdução à Ciência de Dados, com o objetivo de coletar, limpar, processar e analisar dados meteorológicos atuais de 12 capitais brasileiras utilizando a API pública Open-Meteo.

🎯 Objetivo

Coletar informações meteorológicas de diferentes capitais brasileiras, utilizando Python para realizar o consumo de uma API, tratamento dos dados, análise exploratória e visualização gráfica.

O projeto busca identificar diferenças nas condições climáticas entre as cidades e regiões do Brasil, considerando temperatura, umidade relativa do ar e velocidade do vento.

🛠️ Tecnologias utilizadas

* Python: linguagem utilizada no desenvolvimento.
* Requests: realização de requisições HTTP para consumo da API.
* Pandas: manipulação, limpeza e organização dos dados.
* NumPy: processamento e classificação dos dados.
* Matplotlib: criação de gráficos e visualizações.
* Jupyter Notebook: desenvolvimento e documentação do projeto.
* Open-Meteo API: fonte dos dados meteorológicos.

🌎 Fonte de dados

Os dados foram obtidos por meio da API pública da Open-Meteo.

Foram coletadas informações de 12 capitais brasileiras:

* São Paulo
* Rio de Janeiro
* Belo Horizonte
* Brasília
* Curitiba
* Porto Alegre
* Salvador
* Recife
* Fortaleza
* Manaus
* Belém
* Goiânia

Variáveis coletadas

Variável	Descrição	Unidade
Temperatura	Temperatura do ar a 2 metros	°C
Umidade	Umidade relativa do ar	%
Vento	Velocidade do vento a 10 metros	km/h

⚙️ Etapas do projeto

O desenvolvimento foi dividido nas seguintes etapas:

1. Configuração

* Importação das bibliotecas.
* Definição do endpoint da API.
* Configuração das cidades e coordenadas geográficas.

2. Coleta de dados

* Requisições HTTP utilizando a biblioteca Requests.
* Consulta individual para cada capital.
* Armazenamento dos dados brutos em CSV.

3. Limpeza dos dados

* Verificação de valores ausentes.
* Conversão de tipos de dados.
* Remoção de duplicatas.
* Filtragem de valores inconsistentes.
* Padronização dos nomes das colunas.

4. Processamento

* Classificação das cidades por região brasileira.
* Criação de faixas de temperatura: Fria, Amena, Quente e Muito Quente.
* Organização das colunas do dataset final.

5. Análise exploratória

* Estatísticas descritivas.
* Cálculo de médias por região.
* Identificação das cidades com maiores e menores temperaturas.
* Análise da relação entre temperatura e umidade.

6. Visualização

* Gráfico de temperatura por capital.
* Gráfico de dispersão entre temperatura e umidade.

7. Documentação

* Geração automática de documentação em Markdown.
* Registro das estatísticas, características do dataset e principais insights.

📊 Visualizações

O projeto gera dois gráficos principais:

Temperatura atual por capital brasileira

Relação entre temperatura e umidade relativa

📁 Estrutura do repositório

projeto_coleta_clima/
│
├── projeto_coleta_clima.ipynb
├── clima_bruto.csv
├── dataset_clima_brasil.csv
├── documentacao.md
├── grafico_temperatura.png
├── grafico_temp_umidade.png
└── README.md

📈 Resultados

Ao final do processamento, o projeto disponibiliza um dataset estruturado contendo informações meteorológicas das capitais analisadas.

A análise permite:

* Comparar as temperaturas entre as capitais.
* Identificar diferenças climáticas entre as regiões.
* Observar a relação entre temperatura e umidade.
* Identificar as cidades com maior velocidade do vento.

Os resultados e estatísticas detalhadas podem ser consultados no arquivo documentacao.md e no notebook do projeto.

⚠️ Limitações

* Os dados representam as condições meteorológicas de um único instante de coleta.
* A análise considera apenas 12 capitais brasileiras.
* Os dados são provenientes de modelos meteorológicos disponibilizados pela Open-Meteo, não necessariamente de estações físicas localizadas em cada capital.

🚀 Próximos passos

* Automatizar coletas periódicas para construir uma série histórica.
* Incorporar dados meteorológicos de dias anteriores.
* Ampliar a quantidade de cidades analisadas.
* Desenvolver novas visualizações e análises comparativas.

📚 Referências

* Open-Meteo API Documentation
* Pandas Documentation
* Matplotlib Documentation

⸻

Autor: Rendell Leão da Costa Arruda
Disciplina: Introdução à Ciência de Dados
Data: Novembro de 2026