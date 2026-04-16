# Regressão Linear Múltipla com Gradiente Descendente — Eficiência Térmica

**Atividade Dirigida 2 · CP2** — Construção e comparação de modelos de regressão linear múltipla para estimar a eficiência térmica de um trocador de calor industrial, utilizando tanto a abordagem analítica (sklearn) quanto o gradiente descendente implementado manualmente.

---

## Contexto

Uma equipe de monitoramento industrial deseja estimar a eficiência térmica de um trocador de calor a partir de variáveis medidas no processo. O objetivo é transformar o conjunto de dados em um problema de predição supervisionada, onde cada variável de entrada recebe um peso ajustado pelo modelo. O gradiente descendente ajusta esses pesos iterativamente para minimizar o erro de predição.

---

## Dataset

**Arquivo:** `heat_exchanger.csv`

| Coluna | Legenda | Descrição |
|---|---|---|
| `timestamp` | Data do registro | Data da medição. Convertida em `indice_tempo` (dias desde o primeiro registro) |
| `water_inlet_temperature` | Temperatura de entrada da água | Temperatura da água na entrada do trocador |
| `glycol_inlet_temperature` | Temperatura de entrada do glicol | Temperatura do glicol na entrada do sistema |
| `out_glycol_temperature` | Temperatura de saída do glicol | Temperatura do glicol na saída do trocador |
| `out_water_temperature` | Temperatura de saída da água | Temperatura da água na saída do trocador |
| `heat_efficiency` | Eficiência térmica | **Variável alvo** — valor a ser previsto pelo modelo |
| `indice_tempo` | Índice de tempo | Variável criada pelo grupo a partir do `timestamp` |

---

## Objetivo

Construir modelos de regressão linear múltipla para prever `heat_efficiency` e comparar os resultados obtidos via mínimos quadrados ordinários (sklearn) com os obtidos via gradiente descendente implementado manualmente.

---

## Sequência da Atividade

### 1. Mapa de Calor de Correlações
Geração de heatmap para identificar as correlações entre todas as variáveis numéricas, orientando a seleção das features mais promissoras.

### 2. Seleção de Variáveis
Escolha das variáveis com maior correlação absoluta com a variável alvo para construção dos modelos progressivos.

### 3. Comparação de Modelos (sklearn)
Treinamento e avaliação de três modelos com complexidade crescente:

| Modelo | Variáveis | Métrica |
|---|---|---|
| Modelo 1 | 1 variável (maior correlação) | R², RMSE |
| Modelo 2 | 2 variáveis (top 2 correlações) | R², RMSE |
| Modelo 3 | Todas as variáveis (completo) | R², RMSE |

### 4. Gradiente Descendente Manual
Implementação do algoritmo do zero com normalização via `StandardScaler`, loop de épocas, cálculo do gradiente e curva de aprendizado. Comparação dos resultados com o Modelo 3 do sklearn.

### 5. Visualização 3D
Plot 3D do plano de regressão com as duas variáveis mais correlacionadas, sobreposto aos pontos reais do dataset.

---

## Tecnologias

- Python 3
- `pandas` — manipulação de dados
- `numpy` — operações numéricas e implementação do gradiente descendente
- `scikit-learn` — modelos de regressão, métricas e normalização
- `matplotlib` / `seaborn` — visualizações 2D, mapa de calor e curva de aprendizado
- `mpl_toolkits.mplot3d` — visualização 3D

---

## Como Executar

### Opção 1 — Localmente (Jupyter / VS Code)

```bash
# 1. Clone o repositório
git clone https://github.com/GabrielLilla/RegressaoMultiplaAplicada.git
cd RegressaoMultiplaAplicada

# 2. Instale as dependências
pip install pandas numpy matplotlib seaborn scikit-learn

# 3. Abra o notebook
jupyter notebook HeatExchanger.ipynb
```

Na Célula 2, use o carregamento local:

```python
df = pd.read_csv('heat_exchanger.csv')
```

### Opção 2 — Google Colab

```python
from google.colab import drive
drive.mount('/content/drive')
df = pd.read_csv('/content/drive/MyDrive/heat_exchanger.csv')
```

---

## Estrutura do Projeto

```
├── HeatExchanger.ipynb       # Notebook principal
├── heat_exchanger.csv        # Dataset
└── README.md                 # Este arquivo
```