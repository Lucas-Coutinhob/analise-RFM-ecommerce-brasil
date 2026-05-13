# Segmentação de Clientes com Análise RFM — E-Commerce Brasileiro 🇧🇷

Pipeline completo de Data Science: **Merge de 5 tabelas** → **EDA** → **Segmentação por Quartis** → **K-Means** → **Recomendações de Marketing**

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-green?logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3+-orange?logo=scikit-learn)
![Plotly](https://img.shields.io/badge/Plotly-5.15+-purple?logo=plotly)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## Contexto de Negócio

A **análise RFM** (Recency, Frequency, Monetary Value) é uma técnica de segmentação de clientes baseada em dados históricos de compras, amplamente utilizada em marketing para identificar perfis de clientes e direcionar ações estratégicas.

| Dimensão | Pergunta | Interpretação |
|----------|----------|---------------|
| **Recency (R)** | Quando foi a última compra? | Clientes recentes têm maior probabilidade de comprar novamente |
| **Frequency (F)** | Quantas vezes comprou? | Clientes frequentes são mais engajados e leais |
| **Monetary (M)** | Quanto gastou no total? | Clientes de alto valor merecem atenção diferenciada |

---

## Principais Resultados

### Números da Análise
- **93.357 clientes** segmentados ao longo de **773 dias** (Set/2016 — Ago/2018)
- **97% dos clientes** compraram apenas 1 vez — recorrência é o maior desafio do marketplace
- Valor total de transações: **R$ 15,4 milhões** | Ticket médio: **R$ 159,86**

### Segmentação (7 perfis)
| Segmento | % Base | % Receita | Ticket Médio | Ação Recomendada |
|----------|--------|-----------|-------------|------------------|
| **VIP** | 16,3% | 28,9% | R$ 292 | Programa de fidelidade exclusivo |
| **Leais Alto Valor** | 21,4% | 33,9% | R$ 262 | Upsell + programa de pontos |
| **Leais Frequentes** | 24,5% | 10,0% | R$ 67 | Cross-sell para aumentar ticket |
| **Novos Promissores** | 14,2% | 6,2% | R$ 72 | Cupom de 2ª compra + onboarding |
| **Precisam de Atenção** | 4,6% | 6,3% | R$ 224 | Reengajamento + pesquisa de satisfação |
| **Em Risco** | 13,0% | 5,0% | R$ 64 | Win-back com desconto agressivo |
| **Quase Perdidos** | 6,0% | 9,7% | R$ 270 | Última tentativa de reativação |

### Insight Principal
**VIP + Leais Alto Valor = 37,7% da base → 62,8% da receita.** O ticket médio dos VIP (R$ 292) é **4,6x maior** que o dos clientes Em Risco (R$ 64).

---

## Estrutura do Projeto

```
analise-rfm-ecommerce-brasil/
├── dados/                              # Datasets Olist (5 tabelas CSV)
├── notebooks/
│   └── analise_rfm_ecommerce_brasil.ipynb   # Notebook principal
├── outputs/
│   ├── rfm_segmentado.csv              # Dataset RFM com segmentos
│   └── perfil_segmentos.csv            # Perfil agregado por segmento
├── README.md
└── requirements.txt
```

---

## Pipeline Técnico

```
1. Setup e Carregamento (5 tabelas via API Kaggle)
2. Merge dos Datasets (agregação de payments e items + join sequencial)
3. EDA Completa
   ├── Conversão de tipos (datetime)
   ├── Filtro de pedidos válidos (97% delivered)
   ├── Análise de valores ausentes (msno + classificação)
   ├── Análise de outliers (IQR — decisão: manter)
   ├── Análise temporal (pedidos por mês e dia da semana)
   └── Análise geográfica (top 10 estados)
4. Feature Engineering — Cálculo de R, F e M
5. Segmentação por Quartis (7 segmentos + ações de marketing)
6. Segmentação por K-Means (k=2, Silhouette: 0.74)
7. Análise Comparativa (Quartis vs K-Means)
8. Recomendações de Marketing por Segmento
```

---

## Stack Tecnológica

| Ferramenta | Uso |
|-----------|-----|
| **Python 3.12** | Linguagem principal |
| **pandas** | Manipulação e agregação de dados |
| **NumPy** | Operações numéricas |
| **matplotlib / seaborn** | Visualizações estáticas |
| **Plotly** | Treemap e gráfico 3D interativos |
| **scikit-learn** | K-Means clustering, StandardScaler, Silhouette Score |
| **missingno** | Visualização de valores ausentes |
| **kagglehub** | Download do dataset via API |

---

## Dataset

**Olist Brazilian E-Commerce** — disponível publicamente no Kaggle.

- **Fonte:** [kaggle.com/datasets/olistbr/brazilian-ecommerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Tabelas utilizadas:** orders, order_payments, customers, order_items, products
- **Volume:** ~100k pedidos, ~96k clientes, ~113k itens
- **Período:** Setembro/2016 — Agosto/2018

---

## Como Reproduzir

### 1. Clonar o repositório
```bash
git clone https://github.com/Lucas-Coutinhob/analise-rfm-ecommerce-brasil.git
cd analise-rfm-ecommerce-brasil
```

### 2. Criar ambiente virtual
```bash
conda create -n rfm_ecommerce python=3.12 -y
conda activate rfm_ecommerce
pip install -r requirements.txt
```

### 3. Baixar o dataset
**Opção A — Via API (requer conta Kaggle):**
O notebook baixa automaticamente via `kagglehub`.

**Opção B — Manual:**
Baixe de [kaggle.com/datasets/olistbr/brazilian-ecommerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) e extraia os CSVs na pasta `dados/`.

### 4. Executar o notebook
Abra `notebooks/analise_rfm_ecommerce_brasil.ipynb` no VS Code ou Jupyter e execute célula por célula.

---

## Autor

**Lucas Coutinho Boros**
Cientista de Dados em Formação | Python, SQL, Power BI

- LinkedIn: [lucas-coutinho-boros](https://linkedin.com/in/lucas-coutinho-boros)
- GitHub: [Lucas-Coutinhob](https://github.com/Lucas-Coutinhob)
- Email: lucas.boros@live.com
