# PROJETO DE COLETA DE DADOS
## Clima atual das capitais brasileiras (Open-Meteo)

**Autor:** Rendell Leão da Costa Arruda
**Data da coleta:** 09/11/2026
**Disciplina:** Introdução à Ciência de Dados

---

## 1. OBJETIVO
Coletar dados meteorológicos atuais (temperatura, umidade e vento) de 12 capitais brasileiras por meio de uma API pública, organizá-los em um dataset limpo e explorar as diferenças entre cidades e regiões do país.

## 2. FONTES DE DADOS
| Fonte | URL | Método | Dados Coletados |
|-------|-----|--------|-----------------|
| Open-Meteo | https://open-meteo.com | API | Temperatura, umidade relativa e velocidade do vento atuais |

## 3. METODOLOGIA
### 3.1 Coleta
Uma requisição GET por cidade ao endpoint `https://api.open-meteo.com/v1/forecast`, com latitude, longitude e as variáveis `temperature_2m,relative_humidity_2m,wind_speed_10m`, usando a biblioteca `requests`. O código usa `try/except`, `raise_for_status()` e uma pausa de 0,5 s entre as requisições. Os dados originais foram salvos em `clima_bruto.csv` antes de qualquer limpeza.

### 3.2 Limpeza
Verificação de valores ausentes, conversão de tipos (`to_numeric` e `to_datetime`), remoção de linhas sem medições, remoção de duplicatas (mesma cidade e horário), renomeação das colunas e filtro de plausibilidade (temperatura entre -60 e 60 °C, umidade entre 0 e 100 %, vento maior ou igual a zero). Registros: 12 coletados, 12 após a limpeza.

### 3.3 Processamento
Criação das colunas `regiao` (mapeamento manual de cada capital) e `faixa_temperatura` (classificação com `pd.cut`).

## 4. DATASET FINAL
- **Total de registros:** 12
- **Total de colunas:** 10
- **Período:** 09/11/2026 06:00 a 09/11/2026 06:00
- **Tamanho do arquivo:** 1.2 KB (`dataset_clima_brasil.csv`)

### Colunas:
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| cidade | str | Nome da capital |
| regiao | str | Região do Brasil |
| latitude | float64 | Latitude usada na consulta |
| longitude | float64 | Longitude usada na consulta |
| data_hora | datetime64[us] | Horário da medição (Brasília) |
| temperatura_c | float64 | Temperatura do ar a 2 m (°C) |
| umidade_pct | int64 | Umidade relativa a 2 m (%) |
| vento_kmh | float64 | Velocidade do vento a 10 m (km/h) |
| faixa_temperatura | category | Faixa: Fria (até 18), Amena, Quente (25-30), Muito quente (acima de 30) |
| coletado_em | datetime64[us] | Momento em que o script coletou o dado |

## 5. ANÁLISE EXPLORATÓRIA
### 5.1 Estatísticas Descritivas
```
       temperatura_c  umidade_pct  vento_kmh
count          12.00        12.00      12.00
mean           20.48        88.33       7.71
std             6.12         6.60       3.44
min            10.50        75.00       2.10
25%            15.38        85.00       4.58
50%            20.60        89.00       8.85
75%            26.45        93.25      10.22
max            27.60        97.00      12.50
```

Temperatura média por região (°C):
```
regiao
Nordeste        27.1
Norte           25.5
Centro-Oeste    20.6
Sudeste         16.2
Sul             11.8
```

### 5.2 Visualizações
- `grafico_temperatura.png`: barras com a temperatura de cada capital.
- `grafico_temp_umidade.png`: dispersão entre temperatura e umidade.

## 6. INSIGHTS
1. A capital mais quente da coleta foi Recife (27.6 °C) e a mais fria foi Curitiba (10.5 °C), uma amplitude de 17.1 °C.
2. A região com maior temperatura média foi Nordeste (27.1 °C) e a de menor foi Sul (11.8 °C).
3. A correlação entre temperatura e umidade foi de -0.59, negativa: nas cidades mais quentes a umidade tende a ser menor neste instante. O vento mais forte foi em Rio de Janeiro (12.5 km/h).

## 7. LIMITAÇÕES
- Os dados são uma fotografia de um único instante, então não mostram variação ao longo do dia ou da semana.
- Foram usadas 12 capitais, uma amostra que não representa todo o país.
- Os valores são estimativas de modelos meteorológicos agregados pela Open-Meteo, e não medições de uma estação física em cada cidade.

## 8. PRÓXIMOS PASSOS
- Repetir a coleta em intervalos regulares (por exemplo, com `schedule`) para formar uma série temporal.
- Incluir previsão e histórico de dias anteriores e mais cidades.
- Publicar o projeto no GitHub com README.

## 9. CÓDIGO
Notebook `projeto_coleta_clima.ipynb`. Repositório no GitHub: [colar o link aqui, se publicar]

## 10. REFERÊNCIAS
- Open-Meteo, documentação da API: https://open-meteo.com/en/docs
- Documentação do pandas: https://pandas.pydata.org/docs/
- Slides da Aula 4.2 (Processamento e Coleta de Dados), Prof. Danilo César Pereira
