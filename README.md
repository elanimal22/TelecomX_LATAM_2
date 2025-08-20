# TelecomX_LATAM_2
# 📊 Telecom X - Parte 2: Predicción de Churn

## 🎯 Propósito del proyecto
Este proyecto forma parte del desafío **Telecom X - Parte 2**, cuyo objetivo principal es **predecir la cancelación de clientes (churn)** en base a variables relevantes de contrato, consumo y características demográficas.  
La predicción de churn es fundamental para que las empresas de telecomunicaciones puedan **anticipar la pérdida de clientes y diseñar estrategias de retención efectivas**.

---

## 📂 Estructura del proyecto
TelecomX_LATAM/
│── data/
│ └── telecom_clean.csv # Datos tratados y listos para análisis
│── notebook/
│ └── TelecomX_LATAM(1).ipynb # Cuaderno principal con ETL, EDA y modelado
│── README.md # Documentación del proyecto

---

## ⚙️ Proceso de preparación de datos

1. **Clasificación de variables**
   - *Categóricas*: tipo de contrato, servicio de internet, método de pago, género, etc.
   - *Numéricas*: tenure (meses de permanencia), cargos mensuales, cargos totales.

2. **Normalización y codificación**
   - Se expandieron columnas anidadas (`customer`, `phone`, `internet`, `account`) en nuevas variables.
   - Se aplicó **One-Hot Encoding** a las variables categóricas para hacerlas compatibles con algoritmos de machine learning.
   - Se imputaron valores faltantes en variables numéricas (mediana) y categóricas (moda).

3. **Separación de datos**
   - Dataset dividido en **train (80%)** y **test (20%)** con `stratify=y` para conservar la proporción de churn.
   - Target: `Churn` (Yes=1, No=0).

4. **Modelado**
   - Se utilizó **Regresión Logística** como modelo base.
   - Se aplicó `class_weight='balanced'` para mitigar el desbalance de clases.
   - Se evaluó con métricas de precisión, recall, F1-score y matriz de confusión.

---

## 📊 Análisis Exploratorio de Datos (EDA)

Durante la exploración se obtuvieron los siguientes **insights clave**:

- **Distribución de churn:**  
  Aproximadamente el 26% de los clientes cancelaron su servicio → dataset desbalanceado.

- **Contrato vs churn:**  
  Los clientes con contrato *mes a mes* presentan mayor tasa de churn.  
  En contraste, los contratos a 1 o 2 años muestran baja probabilidad de cancelación.

- **Cargos mensuales vs churn:**  
  Clientes con cargos mensuales más elevados tienen mayor tendencia a cancelar.  
  Los clientes de planes económicos son más estables.

- **Correlación entre variables numéricas:**  
  `tenure` (tiempo como cliente) está negativamente correlacionado con churn → a mayor antigüedad, menor probabilidad de cancelar.

---

## ▶️ Ejecución del proyecto

### Requisitos previos
Instalar Python 3.9+ y las siguientes librerías:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
