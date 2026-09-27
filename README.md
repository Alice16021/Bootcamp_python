# Bootcamp_python

# Detecção de Fraudes em Cartão de Crédito

Projeto desenvolvido para analisar e classificar transações financeiras suspeitas utilizando Machine Learning, lidando diretamente com o problema de classes altamente desbalanceadas.

## O Problema

Em bases de detecção de fraude, a imensa maioria das transações é legítima (apenas ~0.2% são fraudes). Usar **Acurácia** nesse tipo de cenário é um erro, pois um modelo simplista que chuta "tudo legítimo" teria quase 100% de acerto e não pegaria nenhuma fraude.

Por isso, a avaliação do projeto foi focada em:
- **Recall (Métrica principal):** Mede a capacidade do modelo de capturar as fraudes reais sem deixá-las passar.
- **Precisão:** Avalia a taxa de falsos alarmes para evitar bloquear clientes legítimos.
- **F1-Score:** Mede o equilíbrio entre Recall e Precisão.

##  Etapas

1. **Tratamento de Dados:**
   - Padronização das variáveis `Time` e `Amount` com `StandardScaler`.
   - Divisão dos dados em Treino (70%) e Teste (30%) mantendo a proporção de fraudes via `stratify`.

2. **Modelagem:**
   - Treino de **Regressão Logística** como baseline.
   - Treino de **XGBoost** ajustando o parâmetro `scale_pos_weight` para penalizar erros na classe minoritária.
   - Aplicação de **SMOTE** para oversampling e comparação com **Random Forest**.

3. **Explicabilidade:**
   - Utilização do **SHAP (SHapley Additive exPlanations)** para mapear quais variáveis (ex: componentes de PCA como `V1`, `V2`, etc.) mais influenciaram na classificação de uma transação como fraude.

## 📊 Resultados

| Modelo | Precisão (Fraude) | Recall (Fraude) | F1-Score |
| :--- | :---: | :---: | :---: |
| Regressão Logística | 0.85 | 0.88 | 0.86 |
| XGBoost | 0.92 | 0.90 | 0.91 |
| Random Forest + SMOTE | 0.89 | 0.89 | 0.89 |

## 🚀 Tecnologias Utilizadas

- Python
- Pandas & NumPy
- Scikit-Learn
- XGBoost
- Imbalanced-Learn (SMOTE)
- SHAP (Explicabilidade)
- Matplotlib & Seaborn

---
Desenvolvido como projeto prático de Machine Learning.
