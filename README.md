# Tratamiento de Datos Ejercicio 3 - Grupo 7 - Análisis de datos

## 1. Coordinación y repositorio central.

El presente ejercicio se desarrolló en este repositorio de Github, creando las ramas de desarrollo dev_brazuero y dev_prvallejo, para el trabaio colaborativo y una vez revisados los avances se procedió a realizar el respectivo pull request para unirlo a la rama principal.

## 2. Selección del dataset

Para el desarrollo del presente ejercicio partimos de un data set de Kaggle, denominado Hotel booking demand, el cual contiene datos de reservas de hoteles y resorts e incluye información de fechas, días de estancia, número de adultas, niños y/o bebés y si se requieren lugares de estacionamiento entre otras variables.

Este dataset no contiene datos personales de los usuarios, y está contenido en el archivo 'hotel_bookings.csv'

Con este ejercicio se pretende describir la relación entre las variables y la confirmación o cancelación de las reservas realizadas.

## 3. Procesamiento de datos

3.1  El primer paso es la importación de librerías necesarias, en este caso emplearemos pandas, numpy, matplotlib, seaborn y scikit.

3.2  Luego se procede con la carga del data set. Para el desarrollo se toma en cuenta la ejecución del código tanto en VSCode como en Google Colab, para lo cual se debe tomar en cuenta la ruta de acceso del dataset es decir del archivo 'hotel_bookings.csv' según se indica en los comentarios colocados el el código, sección '2. CARGA DEL DATA SET'

3.3  Se procede con la limpieza de los datos, primeramente analizando el contenido y se eliminan registros duplicados.

3.4. Se analiza la data resultante.

3.5  Se eliminan ciertas columnas del data ser que contienen la mayor cantidad de elementos nulos.

3.6  Se analizan los valores nulos de las columnas que especifican niños y el país de origen, y se rellenan valores faltantes.

3.7  Se valida que no existan valores nulos luego de la limpieza de datos.

## 4. Análisis Exploratorio de Datos (EDA)

4.1  Se calcula la matriz de correlación, para identificar que variables están más relacionadas con las cancelaciones de las reservas.

4.2  Revisamos el balance de clases de la variable objetivo que en este caso es la cancelación o no de la reserva realizada.

4.3  Analizamos el porcentaje de cancelaciones por tipo de hotel, si es hotel de ciudad o un resort.

4.4  Se analiza el porcentaje de cancelaciones por tipo de depósito para reserva.

4.5  Analizamos los datos de cancelaciones respecto a los días de anticipación de la reserva.

4.6  Comparativa de las reservas canceladas y no canceladas respecto a los tiempos de anticipación.

4.7  Revisamos si el precio es una variable influyente en las cancelaciones.

4.8  Detectamos Outliers(Valores Extermos)

4.9  Creamos nuevas variables útiles para el análisis, para determinar si las reservas se realizan por una familia o por personas solas.

4.10  Analizamos los datos de cancelaciones por familia.

4.11  Analizamos las cancelaciones por segmento de mercado.

4.12  Análisis de Insights.

4.13  Ralizamos una matriz de correlación entre las variables numéricas.

## 5. Visualización de datos

5.1  Todos los pasos previos en el apartado '4. Análisis Exploratorio de Datos (EDA)' se han acompañado de gráficos tanto de barras, box plots e histogramas según corresponda.

5.2  Graficamos la matriz de correlación mediante un Heat Map.

5.3  Realizamos un scatter plot de la relación entre los días de estadía y el precio promedio.

5.4  Graficamos la relación de días de estadía y precio promedio mediante un plot de violín.

5.5  Para los modelos de machine learning se grafican las matrices de confusión.

## 6. Principales Hallásgos del Análisis - Conclusiones

6.1  Las reservas que terminan cancelándose fueron hechas, en promedio, con más anticipación que las reservas no canceladas, esto sugiere que mientras más tiempo pasa entre la reserva y la fecha de llegada, mayor puede ser la probabilidad de cancelación, posiblemente porque los clientes cambian planes, encuentran mejores opciones o modifican su viaje.

6.2  La variable lead_time o anticipación de la reserva parece ser un factor importante para predecir cancelaciones, por lo que se espera que tenga peso relevante en los modelos de Machine Learning.

6.3  La variable de precio también posee una relación importante aunque no la mayor respecto a las cancelaciones.

6.4  Otro hallazgo interesante es que dentro de la variable depósito inicial, las reservas que se realizan sin depósito inicial tienden a cancelarse con más frecuencia que aquellas que se realizan con un depósito previo.

## 7. Implementación de Análisis Machine Learning

7.1   Para este proyecto empleamos scikit para implementar dos modelos de machine learning, Regresión Logística y Random Forest.

7.2.  Modelo de Regresión Logística.- El modelo de Regresión Logística fue utilizada como modelo base para establecer una referencia inicial. El entrenamiento se completó correctamente y el modelo quedó listo para evaluar su capacidad predictiva sobre nuevas reservas. Se construye la matriz de confusión y se calcula una precisión de 79%. La Regresión Logística logró una precisión general aceptable (79%), pero su capacidad para detectar cancelaciones reales fue limitada, con un recall de 48%. Esto indica que funciona como modelo base, aunque sería recomendable probar modelos más avanzados para mejorar la detección de reservas canceladas.

7.3  Modelo Random Forest.- El modelo identifica muy bien las reservas normales, pero pierde una gran cantidad de cancelaciones reales (3501 casos). El modelo Random Forest logró una precisión general aceptable (79%) y una alta precisión al predecir cancelaciones, pero su capacidad para detectar cancelaciones reales fue muy baja, con un recall de solo 27%. Esto indica que el modelo es demasiado conservador al identificar cancelaciones y, en este caso, tuvo un desempeño inferior a la Regresión Logística para el objetivo principal del proyecto.

El análisis de importancia de variables mostró que lead_time fue la característica más influyente en la predicción de cancelaciones, indicando que las reservas realizadas con mucha anticipación tienen mayor riesgo de cancelarse. También destacaron variables como market_segment_Online TA, deposit_type, adr y previous_cancellations, lo que confirma que el canal de reserva, las políticas de pago, el precio y el historial del cliente son factores relevantes. Estos resultados coinciden con el análisis exploratorio previo y aportan valor de negocio, ya que permiten enfocar estrategias preventivas en reservas de mayor riesgo.
      



