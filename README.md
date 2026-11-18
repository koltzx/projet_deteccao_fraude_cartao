# Detecção de Fraudes em Cartões de Crédito com Machine Learning Explicável

Este projeto desenvolve um pipeline completo de Ciência de Dados para identificar transações fraudulentas em cartões de crédito utilizando dados reais anonimizados (284.807 transações, sendo apenas **0,173% fraudes**).

## Objetivo e Desafio de Negócio
Em problemas de fraude financeira, o desbalanceamento extremo faz com que a **acurácia seja uma métrica enganosa** (um modelo que ignora todas as fraudes atinge 99,83% de acurácia). O foco deste projeto foi:
1. Priorizar o **Recall** (capturar o máximo de fraudes reais) e a área sob a curva **PR-AUC**.
2. Evitar vazamento de dados (*Data Leakage*) durante o pré-processamento.
3. Ajustar o **limiar de decisão (Threshold)** para equilibrar perdas financeiras com o atrito causado por falsos positivos.
4. Garantir transparência regulatória e de negócio explicando as decisões do modelo com **SHAP**.

## Tecnologias Utilizadas
* **Python 3.10+**
* **Pandas & NumPy** (Manipulação e análise exploratória)
* **Scikit-Learn** (Pré-processamento com `RobustScaler`, divisão estratificada, Regressão Logística, Random Forest e métricas)
* **XGBoost** (Modelo baseado em *Gradient Boosting* otimizado para classes desbalanceadas)
* **SHAP** (Explicabilidade global e local das previsões)

## Etapas do Projeto
1. **Análise Exploratória (EDA):** Verificação do desbalanceamento de classes e distribuição de valores (`Amount`).
2. **Pré-processamento:** Divisão estratificada (80/20) e escalonamento robusto ajustado exclusivamente nos dados de treino.
3. **Modelagem e Comparação:** Avaliação comparativa entre *Regressão Logística*, *Random Forest* e *XGBoost* utilizando ponderação de classes (`class_weight` e `scale_pos_weight`).
4. **Threshold Tuning:** Análise da curva *Precision-Recall* para escolha estratégica do ponto de corte de probabilidade.
5. **Interpretabilidade (SHAP):** Identificação das principais variáveis que impulsionam o risco de fraude e auditoria individual de transações.

## Como Executar
1. Clone este repositório e acesse a pasta do projeto.
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
3. Abra e execute o notebook `deteccao_fraude_cartao.ipynb` no Jupyter Notebook ou Google Colab.
