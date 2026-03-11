# Telecom Customer Churn Prediction 📡

## 📌 Descripción del Proyecto
Este proyecto tiene como objetivo desarrollar modelos predictivos para identificar clientes con alta probabilidad de cancelar sus servicios (**churn**) en una empresa de telecomunicaciones. Mediante un análisis exploratorio de datos (EDA) y la aplicación de técnicas de **Machine Learning**, se busca anticipar la deserción y proporcionar información estratégica para la retención de clientes.

## 📊 Dataset
El conjunto de datos contiene información de **7,267 clientes** con 21 variables, clasificadas en:

* **Datos demográficos:** Género, edad (`SeniorCitizen`), si tiene pareja (`Partner`), dependientes (`Dependents`).
* **Servicios contratados:** Teléfono, múltiples líneas, internet, seguridad en línea, backup, soporte técnico, streaming, etc.
* **Detalles de la cuenta:** Antigüedad (`tenure`), tipo de contrato, facturación sin papel, método de pago, cargos mensuales y totales.
* **Variable objetivo:** `Churn` (Yes/No) indica si el cliente abandonó la empresa.

---

## 🛠️ Procesamiento de Datos

### 1. Limpieza
* **Eliminación de Identificadores:** Se eliminó la columna `customerID` por no aportar valor predictivo.
* **Corrección de Tipos:** Se convirtió `TotalCharges` a numérico (manejando cadenas vacías) y se eliminaron 11 filas con valores nulos resultantes.

### 2. Codificación y Balanceo
* **Variables Categóricas:** Aplicación de *One-Hot Encoding* (`pd.get_dummies`) excluyendo la variable objetivo.
* **Variable Objetivo:** Mapeo binario (`Yes=1`, `No=0`).
* **SMOTE:** Se utilizó la técnica de sobremuestreo para balancear la clase minoritaria (**26.6%** de churn original).

---

## 📈 Análisis Exploratorio (EDA)

* **Correlación:** Las variables con mayor impacto en el Churn son `tenure` (-0.35), `TotalCharges` (-0.20) y `MonthlyCharges` (0.19).
* **Insights:** * Clientes con menor antigüedad y cargos totales bajos tienden a cancelar más.
    * Los contratos de mes a mes y el servicio de fibra óptica presentan mayores tasas de deserción.



---

## 🤖 Modelos Predictivos
Se utilizaron pipelines con escalado de variables (`StandardScaler`) para entrenar los siguientes modelos:

### 1. Regresión Logística
* **Accuracy:** 80.3%
* **ROC-AUC:** 0.845
* **Métricas Clase Churn:** Precisión 0.66, Recall 0.54.

### 2. Random Forest
* **Importancia de Variables:** Identificó a `tenure`, `TotalCharges` y `MonthlyCharges` como los predictores más relevantes.
* **Performance:** Proporcionó una clasificación robusta ideal para identificar patrones no lineales.



---

## 🔍 Conclusiones Estratégicas
1.  **Segmento Crítico:** Clientes con poca antigüedad y cargos mensuales altos.
2.  **Riesgo por Contrato:** Los contratos *month-to-month* son los más volátiles.
3.  **Recomendaciones:**
    * Enfocar campañas de lealtad en clientes nuevos (primeros 6-12 meses).
    * Ofrecer incentivos para migrar de contratos mensuales a anuales.
    * Monitorear la calidad del servicio en usuarios de fibra óptica.

---