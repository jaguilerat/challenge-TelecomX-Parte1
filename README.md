# challenge-TelecomX-Parte1
Proyecto de Ciencia de datos asociado a ETL con Python
📊 Análisis de Churn de Clientes – Telecom X
📌 Descripción del Proyecto

Este proyecto tiene como objetivo analizar el comportamiento de los clientes de una empresa de telecomunicaciones para identificar los factores asociados al abandono del servicio (Churn).

La empresa Telecom X enfrenta una alta tasa de cancelación de clientes y necesita comprender qué variables influyen en la decisión de abandono.

A través de un análisis exploratorio de datos (EDA) realizado en Python, se busca identificar patrones que permitan al equipo de Data Science desarrollar posteriormente modelos predictivos y estrategias para reducir la pérdida de clientes.

🎯 Objetivos del Proyecto

Analizar el comportamiento de los clientes de Telecom X.

Identificar los factores asociados al churn de clientes.

Realizar limpieza y transformación de datos.

Desarrollar un análisis exploratorio de datos (EDA).

Generar visualizaciones que permitan identificar patrones de abandono.

Proveer información útil para futuros modelos predictivos de churn.

📂 Fuente de Datos

El dataset es obtenido desde una API pública en formato JSON:

https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json

El dataset contiene información sobre:

Datos demográficos del cliente

Tipo de contrato

Servicios contratados

Métodos de pago

Costos mensuales y totales

Antigüedad del cliente

Estado de abandono (Churn)

🧰 Tecnologías Utilizadas

Las principales librerías utilizadas en este proyecto son:

Python 3

Pandas → Manipulación y análisis de datos

NumPy → Cálculos numéricos

Requests → Consumo de API

JSON → Procesamiento de datos estructurados

Matplotlib → Visualización de datos

Seaborn → Visualización estadística

Plotly → Visualizaciones interactivas

📊 Proceso del Análisis

El análisis se desarrolló en las siguientes etapas:

1️⃣ Extracción de Datos

Los datos fueron obtenidos desde una API pública en formato JSON utilizando la librería requests.

url = 'https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json'
response = requests.get(url)
df = pd.json_normalize(data=json.loads(response.text))
2️⃣ Exploración Inicial del Dataset

Se revisó la estructura del dataset para comprender:

Tipos de datos

Cantidad de registros

Columnas disponibles

Valores únicos

df.info()

El dataset contiene aproximadamente 7.000 clientes con 21 variables relacionadas con servicios, perfil del cliente y facturación.

3️⃣ Limpieza y Transformación de Datos

Durante esta etapa se realizaron los siguientes procesos:

Renombrar columnas para mejorar la legibilidad

Conversión de variables a tipos adecuados

Eliminación de registros con valores inconsistentes

Creación de nuevas variables derivadas

Ejemplo:

df_columnas['Charges_Total'] = pd.to_numeric(df_columnas['Charges_Total'], errors='coerce')

También se creó una nueva variable:

Costo diario del servicio

df_columnas['Charges_Day'] = df_columnas['Charges_Monthly'] / 30
📈 Análisis Exploratorio de Datos (EDA)

Se realizaron distintos análisis para comprender el comportamiento de los clientes.

Distribución de abandono de clientes

Permite visualizar la proporción de clientes que cancelaron el servicio.

sns.countplot(data=df_columnas, x='Churn')
Distribución de variables numéricas

Se analizaron variables como:

Antigüedad del cliente (tenure)

Costo mensual (Charges_Monthly)

Costo total (Charges_Total)

Costo diario (Charges_Day)

Utilizando:

Histogramas

Boxplots

Análisis del perfil del cliente

Se evaluaron características demográficas como:

Género

Adulto mayor

Dependientes

Estado civil

Ejemplo:

df_columnas['gender'].value_counts()
Análisis de abandono por antigüedad

Uno de los hallazgos más importantes fue que:

📉 Los clientes que cancelan el servicio tienden a hacerlo en etapas tempranas de su relación con la empresa.

Esto se analizó mediante boxplots de antigüedad vs churn.

Análisis por variables demográficas

También se evaluó el churn según:

Género

Perfil etario

Tipo de contrato

Servicios contratados

Método de pago

Utilizando gráficos como:

Histogramas

Countplots

Gráficos de torta

Visualizaciones interactivas con Plotly

🔍 Insights Claves
📉 Churn temprano como fenómeno crítico

La mayoría de las cancelaciones ocurren en los primeros meses de contrato, lo que indica que la experiencia inicial del cliente es determinante.

💳 Métodos de pago manuales

Los clientes que utilizan cheques electrónicos o pagos manuales presentan una mayor probabilidad de abandono.

📃 Tipo de contrato

Los contratos mensuales (Month-to-Month) presentan mayores tasas de churn en comparación con contratos anuales.

👥 Perfil del cliente

Se identificaron diferencias en el comportamiento de abandono según características demográficas y servicios contratados.

📊 Visualizaciones Generadas

El análisis incluye gráficos como:

Distribución de churn

Histogramas de variables numéricas

Boxplots comparativos

Análisis de churn por género

Análisis de churn por perfil etario

Relación entre antigüedad y abandono

🚀 Próximos Pasos

Este análisis puede ampliarse con:

Feature Engineering

Balanceo de clases

Modelos de Machine Learning

Por ejemplo:

Regresión logística

Random Forest

Gradient Boosting

XGBoost

Con el objetivo de predecir qué clientes tienen mayor probabilidad de abandonar el servicio.

📁 Estructura del Proyecto
telecom-churn-analysis
│
├── telecom_churn_analysis.ipynb
├── README.md
└── dataset/
👨‍💻 Autor

Johnnatan Aguilera

Profesional con experiencia en Business Intelligence, análisis de datos y optimización de procesos, enfocado en generar insights que apoyen la toma de decisiones estratégicas.
