# 🛡️ Detecção de Anomalias em Transações Financeiras

[![Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF)](https://www.kaggle.com/mlg-ulb/creditcardfraud)

## 📌 Visão Geral do Produto
Este projeto apresenta um pipeline analítico ponta a ponta para a identificação de fraudes em transações de cartão de crédito. Desenvolvido no Google Colab, o modelo foca em lidar com o desafio clássico de **desbalanceamento extremo de classes** (onde fraudes representam apenas ~0,17% do volume total), priorizando a detecção de anomalias com alta precisão para mitigar perdas financeiras sem impactar a experiência do usuário (falsos positivos).

## 🎯 Arquitetura e Escopo Técnico
A solução foi desenhada utilizando uma abordagem não supervisionada/semi-supervisionada, adequada para cenários onde a classe minoritária é escassa.

* **Linguagem & Ambiente:** Python, Google Colab.
* **Manipulação e Visualização:** Pandas, NumPy, Seaborn, Matplotlib.
* **Modelagem Preditiva:** `Isolation Forest` (Scikit-Learn).
* **Técnicas Aplicadas:** Padronização de escala de variáveis monetárias e temporais (`StandardScaler`), particionamento estratificado de dados e avaliação de métricas orientadas a negócio (Curva Precision-Recall).

## 🗄️ Governança e Qualidade de Dados
Alinhado com as melhores práticas de gestão de dados, o dataset utilizado requer atenção específica:
* **Privacidade e Segurança:** As variáveis de entrada (V1 a V28) passaram por uma transformação de Componentes Principais (PCA) para anonimização, garantindo a proteção das informações sensíveis dos clientes e conformidade com regulamentações de proteção de dados.
* **Profiling:** A etapa inicial do projeto garante a verificação de completude (ausência de valores nulos) e análise da distribuição original do ativo de dados antes da modelagem.

## 🚀 Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/SEU_USUARIO/nome-do-repositorio.git](https://github.com/SEU_USUARIO/nome-do-repositorio.git)
    cd nome-do-repositorio
    ```
2.  **Configuração do Ambiente:** * Abra o notebook `Anomaly_Detection_Transactions.ipynb` no Google Colab.
3.  **Credenciais do Kaggle:**
    * Certifique-se de ter o arquivo `kaggle.json` (gerado na sua conta Kaggle) para realizar a ingestão automatizada do dataset direto via API. Faça o upload do arquivo para o ambiente do Colab quando solicitado.
4.  **Execução:** * Rode as células sequencialmente para replicar a ingestão, transformação, treinamento e avaliação do modelo.

## 📊 Resultados e Métricas
Em contextos de alta assimetria, a métrica de Acurácia é descartada em favor de indicadores que refletem o impacto real no negócio. O modelo é avaliado principalmente pela **Curva Precision-Recall (PR AUC)** e pela **Matriz de Confusão**, buscando o melhor ponto de equilíbrio entre:
* **Recall:** Capacidade de não deixar transações fraudulentas passarem.
* **Precision:** Garantia de que os alertas gerados são reais, evitando bloqueios indevidos em cartões de clientes legítimos.

## 🛤️ Próximos Passos (Roadmap)
- [ ] Testar arquiteturas de *Deep Learning* (Ex: Autoencoders) para reconstrução de padrões e identificação de anomalias no erro de reconstrução.
- [ ] Implementar técnicas de *Oversampling/Undersampling* (SMOTE, ADASYN) em modelos supervisionados clássicos (XGBoost, Random Forest).
- [ ] Empacotar o modelo em uma API REST (usando FastAPI ou Flask) para simular inferências em tempo real.

---
*Desenvolvido com foco em produtos de dados e inteligência artificial.*
