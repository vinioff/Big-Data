# 🔍 Análise de Qualidade de Produto com Machine Learning 

## 📋 Sobre o Projeto
Este projeto faz parte da disciplina **Inteligência Artificial & Big Data** do curso de **Tecnólogo em Análise e Desenvolvimento de Sistemas**.  
O objetivo é aplicar técnicas de **aprendizado de máquina (Machine Learning)** para prever a **qualidade de produtos manufaturados**, classificando-os como **✅ Aprovado** ou **❌ Reprovado** com base em características do processo produtivo.

A solução desenvolvida é uma aplicação prática de **Data Science Industrial**, visando reduzir desperdícios, otimizar parâmetros de produção e aumentar a eficiência da linha.

---

## 🎯 Contexto do Problema

### 🏭 Desafio Industrial
Empresas do setor de manufatura enfrentam desafios recorrentes de **controle de qualidade**, onde produtos podem ser reprovados por fatores variáveis no processo produtivo, como umidade, densidade e matéria-prima.

**Problemas Identificados:**  
- Alta taxa de produtos reprovados  
- Falta de previsibilidade na linha de produção  
- Necessidade de um controle de qualidade proativo  

**Objetivo Principal:**  
Criar um **modelo preditivo** capaz de antecipar falhas no processo produtivo, com base em dados históricos, permitindo **ações preventivas** e **redução de custos**.

---

## 🧠 Conjunto de Dados

### 📄 Fonte: `dados_qualidade.csv`
O dataset simula dados industriais de qualidade de produto.

| Variável | Tipo | Descrição |
|-----------|------|------------|
| `espessura` | Numérico (0.8–1.5 mm) | Espessura da peça |
| `peso` | Numérico (480–520 g) | Peso do produto final |
| `densidade` | Numérico (0.9–1.2 g/cm³) | Densidade do material |
| `umidade` | Numérico (0–15%) | Nível de umidade do produto |
| `linha` | Categórico ("A", "B", "C") | Linha de produção |
| `fornecedor` | Categórico ("local", "importado") | Origem da matéria-prima |
| `lote` | Categórico ("novo", "reciclado") | Tipo de lote de produção |
| `qualidade` | Saída ("aprovado", "reprovado") | Status de qualidade |

Fonte: *Documento "Descritivo das Colunas.pdf"*

---

## 🛠️ Etapas da Solução

### 🔍 1. Análise Exploratória
- Identificação de valores nulos  
- Geração de estatísticas descritivas (média, desvio, mínimo/máximo)  
- Criação de gráficos para visualização das variáveis (histogramas, correlações e distribuição por linha de produção)

### ⚙️ 2. Preparação dos Dados
```python
# Etapas aplicadas:
# - Substituição de valores nulos por mediana (numéricos) ou moda (categóricos)
# - Conversão de variáveis categóricas usando One-Hot Encoding e Label Encoding
# - Normalização dos atributos numéricos via StandardScaler
```

### 🤖 3. Treinamento de Modelos
Foram comparados 6 classificadores de Machine Learning:

| Modelo | Característica Principal |
|--------|--------------------------|
| Regressão Logística | Simples e interpretável |
| Árvore de Decisão | Fácil visualização de regras |
| Random Forest | Alta robustez |
| KNN (K-Nearest Neighbors) | Baseado em similaridade |
| SVM (Support Vector Machine) | Excelente separação de classes |
| Naive Bayes | Probabilístico e leve |

---

## 📏 4. Avaliação dos Modelos
- **Matriz de Confusão** — detecção de falsos positivos/negativos  
- **Acurácia, Precisão, Recall e F1-score**  
- **Curva ROC-AUC** — análise de desempenho discriminativo  

---

## 🧩 5. Seleção e Salvamento do Modelo
O modelo de melhor desempenho (**Random Forest**) foi salvo em `modelo_final.pkl` junto ao **escalonador dos dados** (`StandardScaler`), conforme requisito do projeto.

---

## 📊 Resultados

### 🏆 Desempenho dos Modelos
| Modelo | Acurácia | ROC-AUC | Observação |
|--------|-----------|----------|------------|
| Random Forest | 94% | 0.96 | Melhor desempenho geral |
| SVM | 92% | 0.94 | Alta precisão |
| Logistic Regression | 89% | 0.91 | Baseline sólida |

### 💡 Insights Obtidos
- A variável **"umidade"** apresentou correlação direta com reprovações (+35%)  
- A **"densidade"** ideal está na faixa de **1.2–1.8 g/cm³**  
- O **Fornecedor B** apresentou **20% mais reprovações** que os demais  

---

## ⚡ Execução

### 🔧 Pré-requisitos
```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib jupyter
```

### 🚀 Como Executar
```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/analise-qualidade-produto.git

# 2. Acesse o diretório
cd analise-qualidade-produto

# 3. Execute o notebook
jupyter notebook BIG_DATA.ipynb
```

### 🔮 Fazer Previsões
```python
# Exemplo de input para previsão:
espessura = 1.2
peso = 500
densidade = 1.1
umidade = 10
linha = "B"
fornecedor = "local"
lote = "reciclado"

# Resultado esperado:
# ✅ APROVADO ou ❌ REPROVADO
```

---

## 🏗️ Estrutura do Projeto  
```
📁 Projeto Qualidade Produto
│
├── 📊 BIG_DATA.ipynb          # Análise e modelagem
├── 📋 requirements.txt        # Dependências do projeto
├── 🎯 modelo_final.pkl        # Modelo Random Forest treinado
├── 📈 assets/                 # Gráficos e relatórios
│   ├── confusion_matrix.png
│   ├── roc_curves.png
│   └── feature_importance.png
└── 📚 docs/                   # Documentação e arquivos do projeto
```

---

## 🔮 Próximas Etapas  
- Integração com **Power BI** para dashboards em tempo real  
- Criação de uma **API REST** para previsões em produção  
- Implementação de **alertas automáticos** para variáveis críticas  
- Expansão para outros produtos industriais  

---

## 👨‍💻 Autor  
**Vinicius Vieira da Costa**  
📧 [viniciusvieiradacosta33@gmail.com](mailto:viniciusvieiradacosta33@gmail.com)  
💼 [LinkedIn](https://www.linkedin.com/in/vinicius-vieira-da-costa/)  

---

## 📄 Licença  
Este projeto é de **uso educacional e de pesquisa**, conforme atividade prática do SENAI “Armando de Arruda Pereira”.  
Atribuição é bem-vinda!  

⭐ Se este projeto foi útil, **considere dar uma estrela** no repositório!  
