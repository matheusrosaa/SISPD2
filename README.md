# Classificação de Tumores de Mama com Machine Learning

Atividade de Machine Learning do curso de **Sistemas de Informação – Univille**.

O projeto usa aprendizado supervisionado para classificar nódulos mamários como **malignos** ou **benignos**, a partir de características extraídas de exames de punção aspirativa (PAAF).

## Base de dados

**Breast Cancer Wisconsin (Diagnostic)**, do [repositório UCI](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic), que vem embutida no scikit-learn.

- 569 amostras: 357 benignas e 212 malignas
- 30 atributos numéricos (raio, textura, perímetro, área, concavidade etc.)
- Sem valores ausentes

## Tipo de análise

- **Tarefa:** classificação binária supervisionada
- **Modelos comparados:** Regressão Logística, KNN, SVM (RBF) e Random Forest
- **Validação:** divisão estratificada 80/20 e validação cruzada estratificada de 5 folds
- **Métrica prioritária:** recall da classe maligna, porque o falso negativo é o erro mais grave

## Etapas

1. Análise exploratória (distribuição das classes, escala dos atributos, correlações)
2. Comparação dos modelos com validação cruzada, usando pipelines com padronização
3. Ajuste de hiperparâmetros com `GridSearchCV`
4. Avaliação no conjunto de teste (matriz de confusão e curva ROC)
5. Importância dos atributos
6. Ajuste do limiar de decisão

## Principais resultados

| Modelo | Acurácia (CV) | Recall (CV) | F1 (CV) | ROC-AUC (CV) |
|---|---|---|---|---|
| **Regressão Logística** | **0,974** | **0,953** | **0,964** | **0,996** |
| SVM (RBF) | 0,971 | 0,947 | 0,961 | 0,995 |
| Random Forest | 0,965 | 0,941 | 0,952 | 0,989 |
| KNN | 0,965 | 0,918 | 0,951 | 0,987 |

No conjunto de teste, a Regressão Logística chegou a **96,5% de acurácia** e **ROC-AUC de 0,996**, e detectou 39 dos 42 tumores malignos. Com o limiar de decisão em 0,3, o recall da classe maligna subiu para **97,6%**.


