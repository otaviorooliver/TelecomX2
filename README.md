# TelecomX2
# 🤖 Telecom X - Parte 2: Prevendo Churn com Machine Learning

Nesta segunda etapa do projeto Telecom X, o foco mudou da Análise Exploratória de Dados (EDA) para a construção de um pipeline de Machine Learning completo. O objetivo foi desenvolver modelos preditivos capazes de antecipar a evasão de clientes (Churn) e extrair a importância de cada variável para embasar decisões de negócio.

## 🛠️ Pipeline de Pré-Processamento de Dados
Para garantir que os algoritmos de Machine Learning pudessem interpretar os dados corretamente, as seguintes etapas foram executadas:

* **Remoção de Identificadores:** A coluna `customerid` foi descartada para evitar *overfitting*, garantindo que o modelo aprendesse padrões de comportamento e não apenas memorizasse usuários específicos.
* **Codificação de Categóricas (Encoding):** Utilizamos o `OneHotEncoder` (Scikit-Learn) para transformar variáveis de texto (como tipo de contrato e serviço de internet) em matrizes numéricas binárias (0 e 1), mantendo o pipeline robusto para dados futuros.
* **Análise de Proporção e Balanceamento:** Identificou-se um desbalanceamento na variável alvo (73% de permanência vs 27% de evasão). A técnica **SMOTE** foi aplicada apenas nos dados de treino para gerar clientes sintéticos da classe minoritária, evitando viés no aprendizado.
* **Padronização de Escalas:** Variáveis contínuas de tempo e dinheiro (`customer_tenure`, `account_charges_monthly`, `account_charges_total`) foram padronizadas com o `StandardScaler` para que o modelo de Regressão Logística não atribuísse peso excessivo a grandezas maiores.

## 📊 Análise de Correlação e Padrões
* **Correlação Direcionada:** Foi plotado um gráfico de barras focado exclusivamente na correlação das features com o `churn`, isolando rapidamente o que impulsiona e o que retém o cliente.
* **Análise Visual:** Boxplots e gráficos de dispersão confirmaram que o tempo de contrato (`customer_tenure`) e os gastos acumulados têm forte poder de separação entre as classes de evasão e permanência.

## 🧠 Modelagem e Machine Learning
Os dados foram divididos em **80% para treino e 20% para teste** (com estratificação para manter a proporção original das classes). Dois modelos foram escolhidos e treinados:

1. **Regressão Logística:** Escolhida como *baseline* pela sua alta capacidade de explicabilidade (interpretação de coeficientes).
2. **Random Forest:** Escolhido pela sua robustez em lidar com relações complexas e não-lineares através de múltiplas árvores de decisão.

## 🏆 Avaliação e Resultados
Ambos os modelos foram avaliados usando métricas de Acurácia, Precisão, Recall, F1-Score e Matriz de Confusão nos dados de teste.

* O modelo **Random Forest** obteve o melhor desempenho preditivo, alcançando uma **acurácia de ~85,8%** e **F1-Score de ~85,6%**, provando excelente capacidade de generalização.
* O modelo de **Regressão Logística** obteve um resultado sólido (**acurácia de ~81,8%**) e foi crucial para a extração de inteligência de negócio através dos seus coeficientes.
* Não foram detectados indícios de *underfitting* ou *overfitting* nas métricas de teste.

## 💡 Conclusões Estratégicas e Importância das Variáveis
Abrindo a "caixa preta" dos modelos (Feature Importance e Coeficientes), as seguintes conclusões de negócio foram extraídas:

* **Tempo e Dinheiro são cruciais:** As variáveis `customer_tenure` e `account_charges_monthly` dominam a tomada de decisão das árvores.
* **Vilões da Evasão:** Contratos na modalidade **Mensal** e pag
