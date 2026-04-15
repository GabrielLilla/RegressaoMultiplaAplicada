# Regressão Linear Múltipla — Estimativa de Custo SaaS

> Construção e análise de modelos de regressão linear múltipla para prever o custo mensal de infraestrutura de clientes em uma plataforma SaaS.

---

## Contexto

Uma empresa de tecnologia deseja estimar o **custo mensal de infraestrutura** de seus clientes com base em características operacionais da conta. O objetivo é construir modelos preditivos que auxiliem no planejamento de recursos e precificação do serviço.

---

## Dataset

**Arquivo:** `dataset_saas.csv` — 1.338 registros, 7 variáveis

| Variável | Tipo | Descrição |
|---|---|---|
| `tempo_operacao_meses` | Numérica | Tempo de uso da plataforma, em meses |
| `tipo_conta` | Categórica | Categoria da conta (`corporativa` / `individual`) |
| `carga_media_diaria_horas` | Numérica | Média diária de horas de uso |
| `num_integracoes` | Numérica | Quantidade de integrações ativas |
| `pico_noturno` | Categórica | Indica se há pico de uso noturno (`sim` / `nao`) |
| `regiao_cluster` | Categórica | Cluster de infraestrutura onde a conta está alocada |
| `custo_mensal_infra` | Numérica | **Variável alvo** — custo mensal estimado de infraestrutura |

---

##  Objetivo

Construir e comparar modelos de regressão linear múltipla para prever `custo_mensal_infra`, avaliando o impacto de diferentes combinações de variáveis na qualidade do modelo.

---

##  Sequência da Atividade

### 1. Mapa de Calor de Correlações
Geração de heatmap para identificar as correlações entre todas as variáveis numéricas, orientando a seleção das features mais promissoras.

### 2. Seleção de Variáveis
Escolha das variáveis com maior correlação absoluta com a variável alvo para construção dos modelos progressivos.

### 3. Comparação de Modelos
Treinamento e avaliação de três modelos com complexidade crescente:

| Modelo | Variáveis | Métrica |
|---|---|---|
| Modelo 1 | 1 variável (maior correlação) | R², RMSE |
| Modelo 2 | 2 variáveis (top 2 correlações) | R², RMSE |
| Modelo 3 | Todas as variáveis (completo) | R², RMSE |

### 4. Visualização 3D
Plot 3D do plano de regressão com as duas variáveis mais correlacionadas, sobreposto aos pontos reais do dataset.

### Bônus — Análise de Resíduos
Verificação da qualidade do modelo completo via gráfico de resíduos vs. valores previstos e histograma da distribuição dos resíduos.

---

## Tecnologias

- **Python 3**
- `pandas` — manipulação de dados
- `numpy` — operações numéricas
- `scikit-learn` — modelos de regressão e métricas
- `matplotlib` / `seaborn` — visualizações 2D e mapa de calor
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
jupyter notebook RegressãoMultiplaAplicada.ipynb
```

Na **Célula 2**, substitua o trecho de montagem do Drive pelo caminho local do CSV:

```python
# Remova as linhas do drive.mount e use:
df = pd.read_csv('dataset_saas.csv')
```

### Opção 2 — Google Colab

1. Acesse o notebook em [Google Colab](https://colab.research.google.com/drive/1SkenM0SRgRmhHCm8QlFRkJqxysWCcddc?usp=sharing)
2. Monte o Google Drive com o arquivo `dataset_saas.csv` na raiz
3. Execute as células em ordem

---

## Estrutura do Projeto

```
├── RegressãoMultiplaAplicada.ipynb   # Notebook principal
├── dataset_saas.csv                  # Dataset
└── README.md                         # Este arquivo
```
