# 🛡️ Deteção de Anomalias em Transações Financeiras

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)
[![Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF)](https://www.kaggle.com/mlg-ulb/creditcardfraud)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Visão Geral do Produto
Este projeto apresenta um pipeline analítico de ponta a ponta para a identificação de fraudes em transações de cartão de crédito. O modelo foca em lidar com o desafio clássico de **desbalanceamento extremo de classes** (onde as fraudes representam apenas ~0,17% do volume total), priorizando a deteção de anomalias com alta precisão para mitigar perdas financeiras sem impactar a experiência do utilizador (falsos positivos).

## 🎯 Arquitetura e Âmbito Técnico
A solução foi desenhada utilizando uma abordagem não supervisionada/semi-supervisionada, adequada para cenários onde a classe minoritária é escassa.

* **Linguagem:** Python.
* **Manipulação e Visualização:** Pandas, NumPy, Seaborn, Matplotlib.
* **Modelação Preditiva:** `Isolation Forest` (Scikit-Learn).
* **Técnicas Aplicadas:** Padronização de escala de variáveis monetárias e temporais (`StandardScaler`), particionamento estratificado de dados e avaliação de métricas orientadas ao negócio (Curva Precision-Recall).

## 🗄️ Governança e Qualidade de Dados
Alinhado com as melhores práticas de gestão de dados, o dataset utilizado requer atenção específica:
* **Privacidade e Segurança:** As variáveis de entrada (V1 a V28) passaram por uma transformação de Componentes Principais (PCA) para anonimização, garantindo a proteção das informações sensíveis dos clientes e a conformidade com as regulamentações de proteção de dados.
* **Profiling:** A etapa inicial do projeto garante a verificação de completude (ausência de valores nulos) e a análise da distribuição original do ativo de dados antes da modelação.

## 🚀 Como Executar o Projeto (Localmente)

1.  **Clonar o repositório:**
    ```bash
    git clone [https://github.com/arctecnologia/NOME_DO_REPOSITORIO.git](https://github.com/arctecnologia/NOME_DO_REPOSITORIO.git)
    cd NOME_DO_REPOSITORIO
    ```
    *(Nota: Substitua `NOME_DO_REPOSITORIO` pelo nome exato deste repositório)*

2.  **Configuração do Ambiente Virtual (Recomendado):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows use: venv\Scripts\activate
    ```

3.  **Instalação de Dependências:**
    Certifique-se de instalar as bibliotecas necessárias para executar o notebook:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn jupyter
    ```

4.  **Download do Dataset:**
    * Aceda à página do dataset no Kaggle: [Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud).
    * Faça o download do ficheiro, extraia-o e coloque o ficheiro `creditcard.csv` na mesma pasta do seu ficheiro `.ipynb`.

5.  **Execução:**
    * Inicie o Jupyter Notebook (ou abra o projeto no VS Code):
    ```bash
    jupyter notebook
    ```
    * Abra o ficheiro `AIFraudDetection.ipynb` e execute as células sequencialmente.

## 📊 Resultados e Métricas
Em contextos de alta assimetria, a métrica de Exatidão (Accuracy) é descartada em favor de indicadores que refletem o impacto real no negócio. O modelo é avaliado principalmente pela **Curva Precision-Recall (PR AUC)** e pela **Matriz de Confusão**, procurando o melhor ponto de equilíbrio entre:
* **Recall:** Capacidade de não deixar passar transações fraudulentas.
* **Precision:** Garantia de que os alertas gerados são reais, evitando bloque
