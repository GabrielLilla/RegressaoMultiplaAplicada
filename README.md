# 📊 Regressão Linear Múltipla — Estimativa de Custo SaaS

> **Atividade Dirigida 2 · CP2** — Construção e análise de modelos de regressão linear múltipla para prever o custo mensal de infraestrutura de clientes em uma plataforma SaaS.

---

## 📋 Contexto

Uma empresa de tecnologia deseja estimar o **custo mensal de infraestrutura** de seus clientes com base em características operacionais da conta. O objetivo é construir modelos preditivos que auxiliem no planejamento de recursos e precificação do serviço.

---

## 🗂️ Dataset

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

## 🎯 Objetivo

Construir e comparar modelos de regressão linear múltipla para prever `custo_mensal_infra`, avaliando o impacto de diferentes combinações de variáveis na qualidade do modelo.

---

## 🔬 Sequência da Atividade

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

## 🛠️ Tecnologias

- **Python 3** (Google Colab)
- `pandas` — manipulação de dados
- `numpy` — operações numéricas
- `scikit-learn` — modelos de regressão e métricas
- `matplotlib` / `seaborn` — visualizações 2D e mapa de calor
- `mpl_toolkits.mplot3d` — visualização 3D

---

## 🚀 Como Executar

1. Acesse o notebook no [Google Colab](https://colab.research.google.com/drive/1_hIEe-0aUExc1vjp3lOdJ5_ZxNMpqio2?authuser=1#scrollTo=f5e0e746)
2. Faça o upload ou monte o Google Drive com o arquivo `dataset_saas.csv`
3. Ajuste o caminho do arquivo na **Célula 2** se necessário:
   ```python
   df = pd.read_csv('/content/drive/MyDrive/dataset_saas.csv')
   ```
4. Execute as células em ordem

---

## 📁 Estrutura do Projeto

```
├── RegressãoMultiplaAplicada.ipynb   # Notebook principal
├── dataset_saas.csv                  # Dataset (baixar separadamente)
└── README.md                         # Este arquivo
```
