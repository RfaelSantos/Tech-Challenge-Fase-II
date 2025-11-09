# 📈 Análise Preditiva do Ibovespa — PósTech FIAP

> Projeto desenvolvido como parte da Pós-Graduação em **Data Analytics** da **FIAP**, com o objetivo de construir um modelo de **machine learning** capaz de prever a tendência diária do índice **Ibovespa**.

---

## 🎯 Objetivo

O desafio consiste em prever se o **fechamento do Ibovespa do dia seguinte** será **maior ou menor** que o do dia atual — ou seja, identificar a **tendência (↑ ou ↓)** com uma **acurácia mínima de 75%** em um conjunto de teste composto pelos **30 dias mais recentes**.

O modelo foi construído com base em **20 anos de dados históricos** e utiliza técnicas modernas de **aprendizado de máquina**, engenharia de atributos e validação temporal.

---

## 🧠 Contexto e Motivação

No mercado financeiro, mesmo uma **pequena vantagem estatística** pode significar a diferença entre **lucro e prejuízo**.  
Este projeto buscou responder à pergunta:

> “É possível prever, com dados históricos e ciência de dados, a direção diária do Ibovespa?”

Durante o processo, foram exploradas múltiplas abordagens para encontrar o equilíbrio entre **acurácia** e **generalização**, evitando o **overfitting** e garantindo um modelo realmente funcional.

---

## 🧩 Metodologia

### 1️⃣ Coleta e Pré-processamento de Dados
- Fonte: Dados históricos do **Ibovespa** (20 anos).
- Tratamento de valores ausentes, normalização e ordenação cronológica.
- Criação de colunas derivadas para análise temporal.

### 2️⃣ Engenharia de Atributos
Principais *features* utilizadas no modelo:
- `Vol.` — Volume financeiro negociado  
- `RSI` — Índice de força relativa (*momentum*)  
- `Volatility_30` — Volatilidade móvel de 30 dias  
- `Lag_Retorno_1` a `Lag_Retorno_5` — Retornos defasados  
- `Price_vs_SMA30` — Distância do preço para a média móvel de 30 dias  
- `MACD_Signal`, `RSI_Diff_3D`, `SP500_Lag_1` — indicadores de momentum e referência externa  

### 3️⃣ Modelagem Preditiva
- Algoritmo principal: **LightGBM (LGBMClassifier)**  
- Validação com **TimeSeriesSplit (5 folds)** respeitando a ordem temporal  
- Otimização de hiperparâmetros com **GridSearchCV**  
- Métricas analisadas: **Acurácia, Matriz de Confusão e Relatório de Classificação**

### 4️⃣ Definição do Target
Para reduzir ruído, o alvo foi definido como:
> Alta significativa = variação acima de **+0,5%** no fechamento do dia seguinte.  
Isso permitiu focar em movimentos de mercado realmente relevantes.

---

## 🤖 Resultados

| Métrica | Resultado |
|----------|------------|
| **Acurácia (teste)** | **83,3%** |
| **Meta mínima** | 75% |
| **Período de teste** | Últimos 30 dias |

O modelo demonstrou:
- Alta precisão ao identificar dias de **baixa** (92% de acerto);
- Capacidade de sinalizar **altas relevantes** com 50% de acerto;
- Forte equilíbrio entre desempenho e robustez.

💡 **Conclusão:**  
O modelo não é uma “bola de cristal”, mas sim uma **ferramenta de apoio à decisão** com vantagem estatística real, capaz de gerar *insights* valiosos para estratégias quantitativas.

---

## ⚙️ Stack Tecnológica

| Categoria | Tecnologias |
|------------|--------------|
| Linguagem | Python 3.12 |
| Bibliotecas | pandas, numpy, scikit-learn, lightgbm, matplotlib, seaborn |
| Ambiente | Jupyter Notebook / VSCode |
| Visualização | Matplotlib, Seaborn |
| Controle de Versão | Git + GitHub |

---

## 📁 Estrutura do Projeto

```
📂 Tech-Challenge-Fase-I/
├── 📄 Analise_ibovespa.ipynb       # Notebook principal com EDA e modelagem
├── 📄 dados_processados.csv        # Base tratada (se aplicável)
├── 📄 README.md                    # Documentação do projeto
├── 📄 .gitignore                   # Arquivos e pastas ignorados
└── 📁 data/                        # (opcional) Pasta de dados brutos
```

---

## 💻 Requisitos

Crie um ambiente virtual e instale as dependências abaixo:

```bash
pip install pandas numpy scikit-learn lightgbm matplotlib seaborn jupyter
```

Ou instale diretamente via arquivo `requirements.txt` (se disponível):

```bash
pip install -r requirements.txt
```

---

## 🚀 Como Executar o Projeto

### 1️⃣ Clonar o repositório
```bash
git clone https://github.com/RfaelSantos/Tech-Challenge-Fase-I.git
cd Tech-Challenge-Fase-I
```

### 2️⃣ Criar e ativar o ambiente virtual
```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows
```

### 3️⃣ Instalar as dependências
```bash
pip install -r requirements.txt
```

### 4️⃣ Executar o notebook
```bash
jupyter notebook Analise_ibovespa.ipynb
```

---

## 📊 Visualizações

O notebook contém diversas visualizações, incluindo:

- Distribuição dos retornos e volatilidade  
- Correlação entre *features*  
- Matriz de confusão do modelo final  
- Evolução temporal das previsões e acertos  

Esses gráficos podem ser visualizados diretamente no **Jupyter Notebook** ou exportados como **HTML** com o comando:

```bash
jupyter nbconvert --to html Analise_ibovespa.ipynb
```

---

## 🧭 Próximos Passos

- Implementar **métricas financeiras adicionais** (ex: Sharpe Ratio, retorno simulado)  
- Testar **modelos híbridos** (LightGBM + LSTM)  
- Integrar com API para **atualização diária automática**  
- Criar **dashboard interativo** em Streamlit ou Power BI  

---

## 👨‍💻 Autor

**Rafael Antunes dos Santos**  
Analista de Dados | PósTech FIAP – Data Analytics  
📍 Ribeirão Pires, SP  
🔗 [LinkedIn](https://www.linkedin.com/in/rafael-antunes-dos-santos)  
✉️ ra.antunes.santos@gmail.com  

---

## 🏛️ Licença

Este projeto é de uso educacional, desenvolvido no contexto da PósTech FIAP.  
© 2025 Rafael Antunes dos Santos. Todos os direitos reservados.
