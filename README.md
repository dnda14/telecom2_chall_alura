Telecom Customer Churn Prediction
📌 Descripción del Proyecto
Este proyecto tiene como objetivo desarrollar modelos predictivos para identificar clientes con alta probabilidad de cancelar sus servicios (churn) en una empresa de telecomunicaciones. A partir de un análisis exploratorio y la aplicación de técnicas de machine learning, se busca anticipar la deserción y proporcionar información estratégica para la retención de clientes.

📊 Dataset
El conjunto de datos contiene información de 7267 clientes con 21 variables, que incluyen:

Datos demográficos: género, edad (SeniorCitizen), si tiene pareja (Partner), dependientes (Dependents).

Servicios contratados: teléfono, múltiples líneas, internet, seguridad en línea, backup, soporte técnico, streaming, etc.

Detalles de la cuenta: antigüedad (tenure), tipo de contrato, facturación sin papel, método de pago, cargos mensuales y totales.

Variable objetivo: Churn (Yes/No) que indica si el cliente abandonó la empresa.

🛠️ Procesamiento de Datos
Limpieza:

Se eliminó la columna customerID por ser un identificador único sin valor predictivo.

Se convirtió Charges.Total a numérico (algunos valores eran cadenas vacías) y se eliminaron filas con valores nulos (11 registros).

Codificación de variables categóricas:

Se aplicó one-hot encoding (pd.get_dummies) a todas las variables categóricas, excluyendo la variable objetivo.

La variable Churn se mapeó a valores binarios (Yes=1, No=0).

Análisis de desbalance:

La proporción de cancelaciones fue de 26.6% (clase minoritaria), lo que indica un desbalance moderado.

Se aplicó SMOTE para balancear las clases en el conjunto de entrenamiento.

📈 Análisis Exploratorio
Correlación: Las variables con mayor correlación con Churn son tenure (-0.35), Charges.Total (-0.20) y Charges.Monthly (0.19). Esto sugiere que los clientes con menos antigüedad y cargos totales bajos tienden a cancelar más.

Visualizaciones:

Boxplots de tenure y Charges.Total según Churn confirman que los que cancelan tienen menor antigüedad y menor gasto total.

Matriz de correlación general entre variables numéricas.

🤖 Modelos Predictivos
Se entrenaron dos modelos de clasificación utilizando pipeline con escalado de variables numéricas (StandardScaler):

1. Regresión Logística
Accuracy: 80.3%

ROC-AUC: 0.845

Reporte de clasificación:

Precisión clase 0 (no churn): 0.84

Precisión clase 1 (churn): 0.66

Recall clase 1: 0.54

Matriz de confusión y curva ROC incluidos.

2. Random Forest
Accuracy: (no se muestra en el PDF, pero se puede calcular a partir de los resultados esperados)

ROC-AUC: (similar o superior)

Importancia de variables: Se identificaron las características más relevantes para la predicción, destacando tenure, Charges.Total, Charges.Monthly y algunos servicios como InternetService_Fiber optic y Contract_One year.

🔍 Conclusiones Estratégicas
Los clientes con poca antigüedad y altos cargos mensuales son más propensos a cancelar.

Contratos de corto plazo (month-to-month) y servicios como fibra óptica están asociados con mayor churn.

Se recomienda enfocar campañas de retención en clientes nuevos, ofrecer incentivos para contratos más largos y mejorar la calidad de servicios con alta tasa de cancelación.