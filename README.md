# insurance-regression
# Análisis de Datos para la Predicción de Costos de Seguro Médico

Este repositorio contiene el desarrollo completo de un análisis de datos orientado a comprender y modelar los factores asociados al costo de un seguro médico, utilizando el "Medical Insurance Cost Dataset" proveniente de la plataforma Kaggle. El proyecto se centra en técnicas de exploración, limpieza, transformación y partición de datos como paso previo a la construcción de un modelo de regresión.

---

## 1. Introducción

Los costos de los seguros médicos representan una de las variables más relevantes dentro del sector salud y constituyen un indicador económico clave tanto para aseguradoras como para usuarios. Comprender qué factores están asociados al incremento de dichos costos permite diseñar modelos predictivos útiles para estimar el gasto futuro y facilitar procesos de evaluación de riesgos.

Este proyecto tiene como finalidad analizar el comportamiento del costo del seguro médico en función de variables demográficas, hábitos y características corporales, con el propósito de preparar un conjunto de datos adecuado para la construcción de un modelo de regresión.

---

## 2. Objetivos del Proyecto

**Objetivo general**
- Analizar y preparar el dataset para identificar los factores que influyen en el costo del seguro médico y generar particiones de datos que puedan ser utilizadas en un modelo predictivo de regresión.

**Objetivos específicos**
1. Realizar una exploración inicial del dataset para comprender su estructura y contenido.
2. Examinar la distribución de variables numéricas y categóricas mediante un análisis univariante.
3. Identificar valores atípicos y aplicar una metodología de filtrado basada en rangos intercuartílicos (IQR).
4. Evaluar la necesidad de transformar la variable objetivo debido a su distribución.
5. Analizar las relaciones entre las variables independientes y el costo del seguro.
6. Construir una matriz de correlación para determinar las variables más relevantes.
7. Dividir el dataset en conjuntos de entrenamiento y prueba bajo un esquema estratificado.
8. Guardar los datasets procesados en archivos independientes para su posterior uso en modelos de regresión.

---

## 3. Descripción del Dataset

- **Nombre:** Medical Insurance Cost Dataset  
- **Fuente:** Kaggle  
- **Número de registros:** 1,338 filas  
- **Número de variables:** 7 columnas  

**Variables incluidas:**
- `age`: Edad del beneficiario.
- `sex`: Género del beneficiario.
- `bmi`: Índice de masa corporal.
- `children`: Número de hijos o dependientes.
- `smoker`: Indica si la persona fuma.
- `region`: Región geográfica de residencia.
- `charges`: Costo del seguro médico (variable objetivo).

Estas variables permiten evaluar tanto características fisiológicas como hábitos y factores sociodemográficos, lo que aporta una visión integral del comportamiento del costo asegurado.

---

## 4. Metodología del Análisis

El análisis se desarrolló siguiendo las siguientes etapas:

### 4.1 Exploración Inicial
Se evaluó la estructura del dataset, los tipos de datos presentes y la existencia de valores faltantes. No se encontraron datos nulos, lo que permitió avanzar sin imputaciones adicionales.

### 4.2 Análisis Univariante
Se estudió cada variable de forma individual para identificar su distribución, rangos y comportamiento general. Entre los hallazgos, se observó que:
- La variable `bmi` se concentra en valores altos, lo que puede relacionarse con sobrepeso u obesidad.
- La variable `charges` presenta una distribución altamente sesgada hacia valores elevados, lo que indica la presencia de valores extremos.

### 4.3 Filtrado de Outliers mediante IQR
Dada la asimetría de `charges` y la existencia de valores atípicos, se aplicó el método de rangos intercuartílicos (IQR) con el objetivo de eliminar registros extremos que podrían distorsionar el desempeño de un futuro modelo de regresión.

### 4.4 Evaluación de la Variable Objetivo
Debido al sesgo notable en la distribución de `charges`, se consideró la creación de una variable transformada mediante logaritmo natural con el fin de estabilizar la varianza y mejorar la interpretabilidad en el contexto de modelado.

### 4.5 Análisis Bivariante
Se examinaron las relaciones entre `charges` y cada variable independiente a través de gráficos comparativos. Este análisis permitió identificar relaciones destacadas, especialmente con el hábito de fumar y con valores altos de `bmi`.

### 4.6 Matriz de Correlación
Se generó una matriz de correlación para identificar las variables con mayor influencia sobre `charges`. Las variables relacionadas con el hábito de fumar, el índice de masa corporal y la edad mostraron correlaciones positivas más significativas, mientras que la región y el género presentaron correlaciones muy bajas.

### 4.7 División del Dataset
El dataset final, una vez filtrado, fue dividido en:
- **80%** datos de entrenamiento.
- **20%** datos de prueba.

La partición se realizó bajo un criterio estratificado mediante agrupación por rangos de `charges`, con el objetivo de mantener proporciones similares entre los conjuntos.

---

## 5. Resultados Principales

- La condición de fumador es el factor con mayor influencia sobre el costo del seguro.
- El índice de masa corporal y la edad también tienen un impacto considerable.
- Variables como el género y la región tienen contribuciones mínimas.
- El filtrado mediante IQR permitió reducir la presencia de valores extremos sin comprometer la integridad del dataset.

---

## 6. Estructura del Repositorio

insurance-regression/
│
├── Analisis_regresion_seguro_medico.ipynb # Notebook con el análisis completo
├── train_insurance.csv # Conjunto de datos para entrenamiento
├── test_insurance.csv # Conjunto de datos para prueba
└── README.md # Documentación detallada del proyecto


---

## 7. Conclusiones

El análisis permitió identificar factores determinantes en el costo del seguro médico y preparar un conjunto de datos adecuado para la construcción de un modelo de regresión. La presencia de valores extremos, la distribución sesgada de la variable objetivo y la alta influencia de ciertos hábitos, como fumar, sugieren la necesidad de aplicar estrategias de transformación y selección de variables en futuros modelos predictivos.

Este repositorio constituye la base inicial para desarrollar modelos regresivos que permitan estimar costos de manera más precisa y fundamentada.

---

## 8. Próximas Etapas

- Implementación de modelos de regresión lineal y modelos basados en árboles.
- Evaluación de métricas como MAE, RMSE y R².
- Generación de un sistema de predicción a partir de nuevos datos.
- Publicación de resultados y visualizaciones adicionales.

---

## 9. Autoría

Proyecto realizado con fines académicos para el análisis y preparación de datos en el contexto de regresión aplicada al costo de seguros médicos.

