# Detecção de Incêndio (Fire Alarm Detection)
## Aplicação de Cross Validation em um Modelo de Classificação

O presente projeto visa desenvolver e avaliar um modelo de Machine Learning capaz de prever a ocorrência de um incêndio (Fire Alarm) com base em diversas variáveis ambientais coletadas por sensores IoT. A principal técnica de avaliação utilizada é a **Validação Cruzada (Cross-Validation)**, que garante uma avaliação robusta da performance e da capacidade de generalização do modelo.

---

### 🎯 Objetivo

O objetivo central é aplicar a técnica de validação cruzada para avaliar a performance de um modelo de **Classificação Logística (Logistic Regression)** na previsão binária da ocorrência de um incêndio (variável alvo `Fire Alarm`).

---

### 📊 Conjunto de Dados

O projeto utiliza o conjunto de dados `smoke_detection_iot.csv`, que contém medições ambientais de sensores.

**Variável Alvo (Target):**
* `Fire Alarm`: Indicador binário de incêndio (1 se houver incêndio, 0 caso contrário).

**Variáveis Preditivas (Features):**
As variáveis incluem leituras de sensores ambientais, como:
* `Temperature[C]`: Temperatura do Ar (em graus Celsius)
* `Humidity[%]`: Umidade do Ar (em porcentagem)
* `TVOC[ppb]`: Total de Compostos Orgânicos Voláteis (em partes por bilhão)
* `eCO2[ppm]`: Concentração equivalente de CO2 (em partes por milhão)
* `Raw H2`: Hidrogênio molecular bruto
* `Raw Ethanol`: Etanol gasoso bruto
* `Pressure[hPA]`: Pressão do Ar (em hectopascais)
* `PM1.0`, `PM2.5`: Material Particulado
* `NC0.5`, `NC1.0`, `NC2.5`: Concentração Numérica de Material Particulado
* `CNT`: Contador de amostras

***Nota:** As colunas `Unnamed: 0` e `UTC` foram descartadas por não serem úteis para a modelagem preditiva.*

---

### 🛠️ Metodologia

1.  **Pré-processamento:** Carregamento do dataset e verificação da ausência de dados nulos.
2.  **Modelo:** Foi utilizada a **Regressão Logística** (`LogisticRegression` da `scikit-learn`) para o problema de classificação binária.
3.  **Avaliação:** O modelo foi avaliado utilizando **K-Fold Cross-Validation** (com $k=10$) para obter uma estimativa de performance mais estável e confiável.

---

### 📈 Resultados

O modelo de Regressão Logística demonstrou uma performance elevada na tarefa de detecção de incêndio.

#### Acurácia por Validação Cruzada (10 Folds)

A acurácia média obtida durante a validação cruzada foi de **0.9303**.

| Fold | Acurácia |
| :---: | :---: |
| 1 | 0.8170 |
| 2 | 0.8218 |
| 3 | 1.0000 |
| 4 | 0.9483 |
| 5 | 0.9106 |
| 6 | 0.9941 |
| 7 | 0.9682 |
| 8 | 1.0000 |
| 9 | 0.9994 |
| 10 | 0.8438 |

#### Relatório de Classificação (Exemplo)

Um relatório de classificação em um conjunto de teste separado mostrou as seguintes métricas:

| Classe | Precision | Recall | F1-Score |
| :---: | :---: | :---: | :---: |
| No Fire (0) | 0.96 | 0.99 | 0.97 |
| Fire (1) | 1.00 | 0.98 | 0.99 |
| **Acurácia Geral** | | | **0.98** |

Os resultados indicam que o modelo é altamente eficaz, especialmente na previsão de incêndios (Classe 1), atingindo uma precisão de 100%.

---
