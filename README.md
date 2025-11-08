# 🔍 Análise de Qualidade de Produto com Machine Learning

## 📋 Sobre o Projeto
Este projeto foi desenvolvido como parte da disciplina **Inteligência Artificial & Big Data** do curso de **Tecnólogo em Análise e Desenvolvimento de Sistemas** do **SENAI Armando de Arruda Pereira**.  

O objetivo é aplicar técnicas de **aprendizado de máquina (Machine Learning)** para prever a **qualidade de produtos manufaturados**, classificando-os como **✅ Aprovado** ou **❌ Reprovado**, com base em variáveis do processo produtivo.  

A solução foi construída com base em **dados simulados de uma indústria**, e representa um projeto completo de **Data Science Industrial**, abordando desde a coleta e tratamento dos dados até a modelagem e interpretação dos resultados.  

---

## 🎯 Contexto do Problema

### 🏭 Desafio Industrial
Nas linhas de produção, a variabilidade de fatores como **umidade**, **densidade** e **fornecedor de matéria-prima** influencia diretamente a qualidade final dos produtos.  
O problema central é identificar **antecipadamente** quais produtos possuem maior probabilidade de reprovação, permitindo **ajustes proativos** no processo.

### 🚨 Problemas Identificados
- Alta taxa de produtos reprovados no controle de qualidade  
- Dificuldade em identificar os fatores que mais influenciam nas falhas  
- Necessidade de um sistema de previsão proativo para reduzir retrabalhos e desperdícios  

### 🎯 Objetivo do Projeto
Construir um **modelo preditivo** capaz de antecipar falhas na produção e prever a qualidade do produto antes do término do processo fabril.  
Com isso, busca-se **otimizar recursos**, **aumentar a eficiência operacional** e **melhorar a tomada de decisão** da equipe de engenharia de qualidade.

---

## 🧠 Conjunto de Dados

### 📄 Fonte: `dados_qualidade.csv`
O dataset contém informações simuladas do ambiente industrial, conforme documentação técnica fornecida pelo professor Miguel Bozer da Silva.

| Variável | Tipo | Descrição |
|-----------|------|-----------|
| `espessura` | Numérico (0.8–1.5 mm) | Espessura da peça produzida |
| `peso` | Numérico (480–520 g) | Peso final da peça |
| `densidade` | Numérico (0.9–1.2 g/cm³) | Densidade do material utilizado |
| `umidade` | Numérico (0–15%) | Nível de umidade presente na peça |
| `linha` | Categórico (“A”, “B”, “C”) | Linha de produção responsável |
| `fornecedor` | Categórico (“local”, “importado”) | Origem da matéria-prima |
| `lote` | Categórico (“novo”, “reciclado”) | Tipo de lote de produção |
| `qualidade` | Saída (“aprovado”, “reprovado”) | Classificação final do produto |

Fonte: *Documento “Descritivo das Colunas.pdf”*

---

## 🧮 Metodologia de Desenvolvimento

O projeto segue o ciclo de vida de um projeto de **Machine Learning aplicado à Indústria 4.0**, dividido nas seguintes etapas:

1. **Análise Exploratória dos Dados (EDA)**  
   - Identificação e tratamento de valores ausentes  
   - Cálculo de estatísticas descritivas (média, desvio padrão, mínimo e máximo)  
   - Geração de visualizações para melhor compreensão da distribuição dos dados  

2. **Pré-Processamento**  
   - Substituição de valores nulos por **mediana (numéricos)** e **moda (categóricos)**  
   - Conversão de variáveis categóricas com **One-Hot Encoding** e **Label Encoding**  
   - Normalização dos dados utilizando **StandardScaler**  

3. **Treinamento e Comparação de Modelos**
   Foram utilizados **6 algoritmos de classificação** para comparação de desempenho:  

   | Modelo | Características |
   |---------|-----------------|
   | Regressão Logística | Modelo baseline simples e interpretável |
   | Árvore de Decisão | Alta interpretabilidade e visualização clara das regras |
   | Random Forest | Maior robustez e generalização |
   | KNN (K-Nearest Neighbors) | Baseado em similaridade entre amostras |
   | SVM (Support Vector Machine) | Alta precisão em separação de classes |
   | Naive Bayes | Modelo probabilístico leve e rápido |

4. **Avaliação dos Modelos**
   - **Matriz de Confusão** para identificação de erros específicos  
   - **Acurácia, Precisão, Recall e F1-score** para análise de desempenho global  
   - **Curva ROC e valor ROC-AUC** para medir capacidade discriminativa  
   - Seleção do **melhor modelo** com base em métricas quantitativas  

5. **Salvamento do Modelo Final**
   - O modelo com melhor desempenho (**Random Forest**) foi salvo como `modelo_final.pkl`  
   - O escalonador utilizado (**StandardScaler**) também foi persistido para uso em produção  

---

## 📊 Resultados Obtidos

### 🏆 Desempenho Comparativo

| Modelo | Acurácia | ROC-AUC | Observação |
|---------|-----------|----------|-------------|
| **Random Forest** | **94%** | **0.96** | Melhor desempenho geral |
| **SVM** | 92% | 0.94 | Alta precisão e estabilidade |
| **Logistic Regression** | 89% | 0.91 | Modelo baseline eficiente |

### 💡 Insights Relevantes
- A variável **umidade** apresentou forte correlação com reprovações (+35%)  
- Faixa de **densidade ideal: 1.2–1.8 g/cm³**  
- Produtos fabricados com **Fornecedor B** tiveram 20% mais reprovações  
- Linhas de produção do tipo **“B”** apresentaram maior variabilidade de qualidade  

Essas descobertas permitem que a equipe de produção **ajuste parâmetros operacionais** antes da fabricação de novos lotes.

---

## ⚙️ Como Executar o Projeto

### 🔧 Dependências Necessárias
```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib jupyter
```

### 🚀 Execução Passo a Passo
```bash
# 1. Clone o repositório
git clone https://github.com/vinioff/Big-Data.git

# 2. Acesse o diretório do projeto
cd analise-qualidade-produto

# 3. Execute o Jupyter Notebook
jupyter notebook BIG_DATA.ipynb
```

### 🔮 Realizando Previsões
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

## 🧱 Estrutura do Projeto
```
📁 Projeto Qualidade Produto
│
├── 📊 BIG_DATA.ipynb          # Análise completa e modelagem
├── 📋 requirements.txt        # Dependências do projeto
├── 🎯 modelo_final.pkl        # Modelo Random Forest treinado
├── 📈 assets/                 # Gráficos e visualizações
│   ├── confusion_matrix.png
│   ├── roc_curves.png
│   └── feature_importance.png
└── 📚 docs/                   # Documentação adicional
```

---

## 🔮 Próximas Etapas
- Implementar **API REST** para previsões em tempo real  
- Integração com **Power BI / Grafana** para dashboards dinâmicos  
- Geração automática de **alertas industriais** em casos de risco de reprovação  
- Aplicação de **Deep Learning (Redes Neurais)** para cenários com maior volume de dados  

---

## 👨‍💻 Autor
**Vinicius Vieira da Costa**  
📧 [viniciusvieiradacosta33@gmail.com](mailto:viniciusvieiradacosta33@gmail.com)  
💼 [LinkedIn](https://www.linkedin.com/in/vinicius-vieira-da-costa/)  

---
