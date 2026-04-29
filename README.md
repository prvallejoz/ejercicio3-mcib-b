# Tratamiento de Datos – Ejercicio Práctico Clase 3

## Grupo 7 – Análisis Predictivo de Cancelación de Reservas Hoteleras


# 1. Coordinación y Repositorio Central

El presente trabajo práctico fue desarrollado mediante un esquema de colaboración grupal utilizando GitHub como plataforma principal de gestión del proyecto. Para ello, se designó una persona coordinadora encargada de crear el repositorio central, organizar la estructura inicial del proyecto y supervisar la integración final de los avances realizados por cada integrante.

Con el objetivo de mantener un flujo de trabajo ordenado, cada miembro trabajó en ramas independientes de desarrollo:

* `dev_brazuero`
* `dev_prvallejo`

Cada mejora, corrección o bloque de análisis fue desarrollado de forma aislada y posteriormente integrado a la rama principal mediante **Pull Requests**, permitiendo revisar cambios antes de su aprobación. Esta metodología permitió evitar conflictos entre versiones, mantener trazabilidad de modificaciones, dividir responsabilidades y trabajar de manera similar a un entorno profesional de desarrollo colaborativo.

El uso de control de versiones también permitió conservar historial de cambios, retroceder versiones si era necesario y documentar adecuadamente la evolución del proyecto.


# 2. Selección del Dataset

Para el desarrollo del presente ejercicio se seleccionó el dataset **Hotel Booking Demand**, disponible públicamente en Kaggle. Este conjunto de datos contiene información histórica de reservas realizadas en hoteles urbanos y resorts, convirtiéndose en una fuente ideal para aplicar técnicas de análisis de datos orientadas al negocio.

El dataset incluye variables operativas y comerciales altamente relevantes, entre ellas:

* Tipo de hotel
* Fecha de llegada
* Tiempo de anticipación de la reserva (`lead_time`)
* Número de noches de estadía
* Número de adultos, niños y bebés
* País de origen del cliente
* Segmento de mercado
* Canal de distribución
* Tipo de habitación reservada
* Tipo de depósito
* Solicitudes especiales
* Precio promedio diario (`ADR`)
* Estado final de la reserva (`is_canceled`)

El archivo utilizado fue:

```python id="a1028x"
hotel_bookings.csv
```


## Justificación de la elección

Este dataset fue seleccionado debido a que representa una problemática real dentro del sector hotelero: las cancelaciones de reservas. Dichas cancelaciones afectan ingresos, planificación operativa, asignación de habitaciones y proyección de demanda.

A través de este dataset es posible responder preguntas estratégicas como:

* ¿Qué variables aumentan la probabilidad de cancelación?
* ¿Existen perfiles de clientes con mayor riesgo?
* ¿Es posible anticipar cancelaciones futuras con Machine Learning?
* ¿Qué decisiones comerciales podrían reducir pérdidas?

Además, el volumen de datos y la variedad de variables lo convierten en una excelente base para aplicar limpieza de datos, visualización, análisis exploratorio y modelos predictivos.


# 3. Objetivo del Proyecto

El objetivo principal del proyecto fue analizar el comportamiento histórico de las reservas hoteleras para identificar patrones asociados a la cancelación de reservas y comprender qué factores explican dicho fenómeno.

Como objetivo adicional, se desarrollaron modelos de Machine Learning capaces de predecir si una reserva futura será cancelada o no, con la finalidad de generar información útil para la toma de decisiones del negocio hotelero.

En términos prácticos, este proyecto busca transformar datos históricos en herramientas de gestión predictiva.


# 4. Procesamiento y Limpieza de Datos

Antes de cualquier análisis, fue necesario realizar un proceso riguroso de preparación del dataset. Esta etapa es fundamental, ya que la calidad de los resultados depende directamente de la calidad de los datos utilizados.

## 4.1 Importación de librerías

Se utilizaron librerías estándar del ecosistema de análisis de datos en Python:

* **Pandas:** manipulación de datos tabulares.
* **NumPy:** operaciones numéricas.
* **Matplotlib:** visualización básica.
* **Seaborn:** gráficos estadísticos avanzados.
* **Scikit-learn:** Machine Learning y preprocesamiento.

## 4.2 Carga de datos

Se importó el archivo `hotel_bookings.csv`, dejando el notebook preparado para ejecutarse tanto en Google Colab como en entornos locales como VSCode o Jupyter Notebook.

## 4.3 Inspección inicial

Se revisaron aspectos clave como:

* Número de filas y columnas.
* Tipos de variables.
* Valores faltantes.
* Registros duplicados.
* Variables categóricas y numéricas.
* Coherencia general de la información.

## 4.4 Limpieza aplicada

Durante esta etapa se realizaron las siguientes acciones:

* Eliminación de registros duplicados para evitar sesgos estadísticos.

* Tratamiento de valores nulos.

* Imputación de valores faltantes en variables como:

  * `children`
  * `country`

* Eliminación de columnas con excesivos nulos o baja utilidad analítica.

* Corrección de formatos de datos cuando fue necesario.

## 4.5 Ingeniería de Variables

Se construyeron nuevas variables con valor analítico:

* `total_guests` = total de personas en la reserva.
* `total_nights` = noches totales reservadas.
* `is_family` = indicador de reserva familiar.

Estas variables permitieron enriquecer el análisis y mejorar la capacidad predictiva de los modelos.

## 4.6 Validación final

Una vez finalizado el proceso, se verificó que los datos se encuentren listos para análisis y modelado sin errores críticos ni valores faltantes relevantes.


# 5. Análisis Exploratorio de Datos (EDA)

Se desarrolló un análisis exploratorio profundo con el objetivo de comprender cómo se comportan las reservas y detectar patrones relevantes antes de construir modelos predictivos.

## Principales análisis realizados

### 5.1 Balance de clases

Se analizó la proporción entre reservas canceladas y no canceladas. Esto permitió identificar que el problema presenta cierto desbalance, aspecto importante para interpretar métricas de Machine Learning.

### 5.2 Cancelaciones por tipo de hotel

Se comparó el comportamiento entre hoteles urbanos y resorts, observando diferencias en tasas de cancelación según tipo de establecimiento.

### 5.3 Tipo de depósito

Se analizó cómo influyen políticas de prepago o depósitos iniciales sobre la decisión final del cliente.

### 5.4 Lead Time

Se estudió el tiempo de anticipación entre la reserva y la llegada. Esta variable mostró una relación clara con las cancelaciones.

### 5.5 Precio promedio diario (`ADR`)

Se exploró si el precio de la reserva tiene impacto en la probabilidad de cancelar.

### 5.6 Segmento de mercado

Se analizaron canales de reserva como agencias online, corporativo, directo, grupos, entre otros.

### 5.7 Clientes repetitivos

Se evaluó si clientes frecuentes presentan menor probabilidad de cancelar.

### 5.8 Outliers

Se detectaron valores extremos en precio, número de noches y otras variables relevantes.

### 5.9 Correlaciones

Se generó matriz de correlación para detectar relaciones lineales entre variables numéricas.

Este análisis permitió llegar al modelado con mayor entendimiento del problema.


# 6. Visualización de Datos

La visualización fue utilizada como herramienta principal para comunicar resultados de forma clara, intuitiva y profesional.

Se aplicaron gráficos desarrollados con Matplotlib y Seaborn, entre ellos:

* Histogramas para distribuciones.
* Boxplots para detección de outliers.
* Barras comparativas para proporciones.
* Heatmaps para correlaciones.
* Scatter plots para relaciones numéricas.
* Violin plots para comparar distribuciones.
* Matrices de confusión para modelos predictivos.
* Barras de importancia de variables.

El uso de gráficos permitió no solo validar hipótesis estadísticas, sino también facilitar la interpretación para usuarios no técnicos.


# 7. Principales Hallazgos del Proyecto

El análisis permitió identificar patrones consistentes y de alto valor para el negocio hotelero. Las reservas canceladas fueron realizadas, en promedio, con mucha mayor anticipación que las reservas efectivamente concretadas, lo cual sugiere que mientras más tiempo transcurre entre la reserva y la fecha de llegada, mayor es la probabilidad de cambio de planes por parte del cliente. También se observó que las reservas sin depósito inicial presentan tasas significativamente superiores de cancelación, lo que evidencia que compromisos financieros tempranos reducen el abandono. Adicionalmente, canales digitales como agencias online concentraron una proporción importante de cancelaciones, mientras que clientes con historial previo de cancelaciones mostraron mayor reincidencia. Finalmente, variables económicas como el precio promedio diario (`ADR`) también mostraron influencia, confirmando que decisiones comerciales y sensibilidad al precio forman parte del comportamiento del consumidor.


# 8. Machine Learning

Con el objetivo de agregar valor predictivo al proyecto, se implementaron modelos supervisados capaces de anticipar si una reserva futura será cancelada.

Variable objetivo:

```python id="mz9y6k"
is_canceled
```

Donde:

* `1` = Reserva cancelada
* `0` = Reserva concretada

Se compararon dos enfoques distintos.


## 8.1 Modelo Base: Regresión Logística

Se utilizó como modelo inicial debido a su rapidez, facilidad de interpretación y buen desempeño en problemas de clasificación binaria.

### Resultados

* Accuracy: **79%**
* Precision clase 1: **68%**
* Recall clase 1: **48%**
* F1-score clase 1: **56%**

### Interpretación

El modelo logró una precisión general aceptable, clasificando correctamente la mayoría de los casos. Sin embargo, solo detectó cerca de la mitad de las cancelaciones reales. Aun así, mostró un equilibrio razonable entre precisión y recall, convirtiéndose en una base sólida de comparación.


## 8.2 Modelo Random Forest

Posteriormente se aplicó un Random Forest, modelo compuesto por múltiples árboles de decisión capaces de capturar relaciones no lineales entre variables.

### Resultados

* Accuracy: **79%**
* Precision clase 1: **86%**
* Recall clase 1: **27%**
* F1-score clase 1: **41%**

### Interpretación

Aunque el modelo mostró alta precisión al predecir cancelaciones, detectó pocas cancelaciones reales. Esto significa que fue demasiado conservador y solo marcó como cancelación aquellos casos muy evidentes. Para el objetivo principal del proyecto, tuvo menor utilidad que la Regresión Logística.


## 8.3 Importancia de Variables

El Random Forest identificó como variables más relevantes:

1. `lead_time`
2. `market_segment_Online TA`
3. `country`
4. `total_of_special_requests`
5. `deposit_type`
6. `adr`
7. `previous_cancellations`

### Interpretación

Estos resultados validan el análisis exploratorio y muestran que la cancelación depende de factores temporales, comerciales, históricos y económicos.


# 9. Conclusiones Finales

El proyecto demostró que los datos históricos pueden transformarse en información estratégica para mejorar la gestión hotelera. Se comprobó que las cancelaciones no ocurren al azar, sino que responden a patrones identificables relacionados con el tiempo de anticipación, el tipo de depósito, el canal de reserva, el historial del cliente y variables económicas. Desde el punto de vista predictivo, la Regresión Logística presentó el mejor equilibrio entre desempeño general y capacidad de detectar cancelaciones reales, mientras que Random Forest fue más restrictivo. Esto evidencia que modelos simples, correctamente implementados, pueden generar gran valor. En términos empresariales, un hotel podría utilizar estos hallazgos para anticipar pérdidas, ajustar políticas comerciales, mejorar proyecciones de ocupación y focalizar acciones preventivas sobre reservas de alto riesgo.


# 10. Valor Agregado del Proyecto

Además de cumplir los requisitos solicitados, el proyecto incorporó valor adicional mediante trabajo colaborativo con GitHub, uso de ramas y Pull Requests, documentación técnica ordenada, ingeniería de variables, implementación de modelos predictivos, interpretación orientada al negocio y una narrativa clara que conecta datos con decisiones reales.


# 11. Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook
* GitHub


# 12. Recomendaciones Futuras

Como línea de mejora futura, se recomienda profundizar el modelado predictivo mediante algoritmos más robustos como XGBoost, LightGBM o CatBoost, los cuales suelen ofrecer mejores resultados en datos tabulares. También sería conveniente aplicar técnicas de balanceo de clases como SMOTE para mejorar la detección de cancelaciones reales. Otra mejora importante sería realizar optimización automática de hiperparámetros mediante GridSearchCV o RandomizedSearchCV. Desde el punto de vista empresarial, sería valioso construir dashboards interactivos en Power BI o Streamlit para monitorear cancelaciones en tiempo real y desplegar un sistema de scoring que clasifique nuevas reservas según nivel de riesgo. Finalmente, integrar datos externos como clima, temporadas vacacionales, eventos locales o precios de competidores podría aumentar significativamente la capacidad predictiva del modelo.
