# :chart_with_upwards_trend: Predicción de Ventas de Productos Alimenticios en Tiendas - Big Mart Sales Prediction
---
![SALES PREDICTION](https://github.com/Oghalis/sales-predictions/assets/148403071/dd96e169-d0c0-472d-ba2d-b6b01c5e3424)
* Este repositorio forma parte de uno de los proyectos presentados durante el curso de Análisis de Datos impartido por Coding Dojo.
# :clipboard: Tabla de contenidos
1. [Resumen del Proyecto](#sec_1)
2. [Objetivos del Proyecto](#sec_2)
3. [Dataset/ Diccionario de datos](#sec_3)
4. [Análisis Exploratorio de Datos (EDA)](#sec_4)
5. [Análisis Explicativo de Datos](#sec_5)
6. [Preprocesamiento](#sec_6)
7. [Modelos de Machine Learning](#sec_7)
8. [Evaluación de Modelos](#sec_8)
9. [Resultados y Conclusiones](#sec_9)
10. [Presentación](#sec_10)
11. [Disclaimer](#sec_11)

<a id='sec_1'></a>
# :bookmark_tabs: Resumen del Proyecto
Este proyecto se enfoca en la predicción de ventas de productos alimenticios en varias tiendas utilizando el conjunto de datos "Big Mart Sales Prediction". Mediante técnicas de ciencia de datos y aprendizaje automático, se analizan las características de los productos y los puntos de venta para identificar factores que influyen en el aumento de las ventas. El objetivo es proporcionar a los minoristas herramientas predictivas para comprender mejor el comportamiento del mercado y optimizar sus estrategias comerciales.

<a id='sec_2'></a>
# :dart: Objetivos del Proyecto
## Objetivo Principal
Desarrollar modelos predictivos precisos para estimar las ventas de productos alimenticios en tiendas utilizando el conjunto de datos "Big Mart Sales Prediction".
## Objetivos Secundarios
1. Identificar las características clave de los productos que afectan las ventas, como el peso del producto, el contenido de grasa, el tipo de producto y el precio MRP (Maximum Retail Price).
2. Analizar la influencia de las características del punto de venta, como el tamaño del establecimiento, la ubicación y el tipo de tienda, en las ventas de productos.
3. Proporcionar a los minoristas una comprensión detallada de los factores que impulsan las ventas y sugerir estrategias para mejorar el rendimiento de ventas.
4. Documentar el proceso de desarrollo del modelo y compartir el código en un repositorio público en GitHub para su revisión, colaboración y uso como referencia para futuras investigaciones y análisis relacionados con el proyecto.

<a id='sec_3'></a>
# :floppy_disk: Dataset / Diccionario de datos
El dataset utilizado en este proyecto consta de 8523 entradas y 12 columnas. Se agregó la característica adicional "Cantidades_vendidas" para poder realizar un mejor análisis. A continuación se detallan las columnas presentes en el dataset:

| Columna                     | Tipo    | Descripción                                                                  |
|-----------------------------|---------|------------------------------------------------------------------------------|
| Item_Identifier             | Objeto  | Identificador único para cada producto.                                      |
| Item_Weight                 | Float   | Peso del producto.                                                           |
| Item_Fat_Content            | Objeto  | Contenido de grasa del producto.                                              |
| Item_Visibility             | Float   | La proporción de área de escaparate del producto en la tienda.                |
| Item_Type                   | Objeto  | Categoría del producto.                                                       |
| Item_MRP                    | Float   | Precio máximo de venta del producto.                                          |
| Outlet_Identifier           | Objeto  | Identificador único para cada tienda.                                         |
| Outlet_Establishment_Year   | Int     | Año de establecimiento de la tienda.                                          |
| Outlet_Size                 | Objeto  | Tamaño de la tienda.                                                          |
| Outlet_Location_Type        | Objeto  | Tipo de área en el que se ubica la tienda.                                    |
| Outlet_Type                 | Objeto  | Tipo de tienda.                                                               |
| Item_Outlet_Sales           | Float   | Ventas del artículo en la tienda.                                             |

| Columna añadida             | Tipo    | Descripción                                                                  |
|-----------------------------|---------|------------------------------------------------------------------------------|
| Cantidades_vendidas         | Objeto  | Total de unidades vendidas por cada producto según tienda.                   |

El dataset presenta valores faltantes en las columnas Item_Weight y Outlet_Size. Se completaron los valores faltantes de Item_Weight asociando los datos de Item_Identifier con sus respectivos pesos. Se eliminaron cuatro registros de productos no identificados. Para Outlet_Size se reemplazó los datos nulos utilizando la moda, considerando la agrupación según Outlet_Type.

<a id='sec_4'></a>
# :mag_right: Análisis Exploratorio de Datos (EDA)
## Histograma del dataset
![descarga](https://github.com/Oghalis/sales-predictions/assets/148403071/ad1c7448-94b3-4873-9811-a408c5ea5ce1)
A continuación, se presentan las conclusiones preliminares basadas en los histogramas generados para cada característica. Se ha excluido Item_Identifier ya que es un identificador único para cada artículo y no aporta información sustancial sobre las características o el comportamiento del ítem en sí.

| Variable                     | Descripción                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Item_Weight**              | La mayoría de los productos pesan entre 5 y 12.5 unidades. Existe un pico alrededor del valor 12.5, lo que sugiere que algunos productos son más pesados que otros. |
| **Item_Fat_Content**         | La mayoría de los productos son bajos en grasa, seguido por productos con nivel regular de grasa.                             |
| **Item_Visibility**          | La mayoría de los productos tienen una visibilidad cercana a 0, es decir, no son muy visibles en tiendas.                                 |
| **Item_Type**                | Hay más cantidad de frutas y verduras, seguido por productos en presentación de snack.                                                    |
| **Item_MRP** | Hay picos notables en ciertos rangos de precios, alrededor de 100 y alrededor de 180.                                                                     |
| **Outlet_Identifier**  | Existe una cantidad similar de productos según los tipos de tiendas, excepto OUT010 y OUT019, que muestran una menor cantidad.                  |
| **Outlet_Establishment_Year**  | La mayor cantidad de productos se comercializan en las tiendas del año 1985.                                                            |
| **Outlet_Size**    | La mayoría de los productos se comercializan en tiendas pequeñas, seguido de una proporción menor de tiendas de tamaño mediano, mientras que un número reducido se comercializa en tiendas grandes. |
| **Outlet_Location_Type** | La mayoría de los productos están distribuidos en las tiendas ubicadas en el Tier 3. Se tiene igual cantidad de productos del Tier 1 y Tier 2, con una diferencia mínima entre ambas.   |
| **Outlet_Type** | La mayoría de los productos están distribuidos en los Supermarket Type 1. En menor medida y con igual distribución de productos se encuentran las tiendas del tipo Supermarket Type 2, Grocery Store y Supermarket Type 3.            |
| **Item_Outlet_Sales**    | La mayor cantidad de ventas totales por producto según tipo de tienda se concentra en el rango de 0 a 2000.                                   |
| **Cantidades_Vendidas**    | La mediana del valor de las unidades totales vendidas por producto y por tienda se sitúa alrededor de 15.                                   |

## Contenido de grasa
![boxplot](https://github.com/Oghalis/sales-predictions/assets/148403071/77e40124-e5c1-4ab8-bca6-86c1a7bcef40)
Las tiendas venden en un 64.7% productos bajos en grasa y en un 35.3% productos regulares. Sin embargo, que existan más productos bajos en grasa no es prevalente en las cantidades vendidas. Asimismo, ambos tipos de productos tienen distribuciones de precios similares.
## RPM y Visibilidad del producto
![correlacion](https://github.com/Oghalis/sales-predictions/assets/148403071/2137e94f-d95b-4d89-b7b7-500c4573dcd4)
Los producto con menor RPM (Precio máximo de venta del producto) concentran mayor cantidad de ventas, especialmente en el rango de 100 a 200 u.m. RPM. Por otro lado, los productos con menor visibilidad tienden a tener mayores ventas, por tanto se entiende que son familiares para el cliente y/o son populares.

<a id='sec_5'></a>
# :bar_chart: Análisis Explicativo de Datos
## Ventas según año de creación de establecimiento
![scater](https://github.com/Oghalis/sales-predictions/assets/148403071/373f3d2a-9c07-4d3f-8670-65f4cec7acc9)
Existe una tienda por año, excepto en 1985, cuando se adjudicaron/crearon 2 tiendas. Las cantidades vendidas por cada una de ellas es bastante similar, excepto por la tienda adjudicada/creada en el año 2009 que se encuentra por debajo del resto, y muy por debajo la tienda creada en 1998, con cantidades y volumenes de venta 10 veces menores al resto.

## Rango de MRP por categoría, ordenado por ventas descendentes
![boxplot2](https://github.com/Oghalis/sales-predictions/assets/148403071/6eed0d37-ff4a-4878-8132-e4a7baf555de)
La mayor parte de los productos tiene un MRP entre 100 y 200, siendo las categorías más vendidas: Frutas y Vegetales, Snacks y Artículos para el hogar. Las dos categorias de productos menos vendidos, productos relacionados con el Desayuno y Mariscos, tienen menos variabilidad de precios.

<a id='sec_6'></a>
# :wrench: Preprocesamiento
Mediante el uso de tuberías y la librería scikit-learn, se empleó la técnica de SimpleImputer para gestionar los valores faltantes en las características numéricas utilizando la media, y la mediana para las características nominales. Además, se aplicó el escalado estándar mediante StandardScaler a las características numéricas, normalizándolas para que estuvieran centradas alrededor de cero y con una desviación estándar de uno. Por último, se utilizó la codificación One-Hot mediante OneHotEncoder para convertir las características categóricas en vectores binarios.

![Captura](https://github.com/Oghalis/sales-predictions/assets/148403071/d7995a70-0bb9-45b4-bd26-64bb62a96101)

<a id='sec_7'></a>
# :control_knobs: Modelos de Machine Learning

En este proyecto, se implementó y optimizó un modelo de regresión de bosque aleatorio usando RandomForestRegressor. Tras dividir los datos en conjuntos de entrenamiento y prueba (70/30), el modelo inicial con 100 árboles demostró una alta precisión, que se mejoró aún más mediante la optimización de hiperparámetros con GridSearchCV, aumentando el número de árboles a 500. Además, se exploró la reducción de dimensionalidad mediante PCA, buscando mejorar la eficiencia del modelo sin comprometer su rendimiento. Las métricas clave, como MSE, MAE, y R^2, indicaron una precisión significativa tanto en los datos de entrenamiento como de prueba, aunque se identificó la necesidad de futuras mejoras para reducir los errores de predicción.



<a id='sec_8'></a>
# :microscope: Resumen de los resultados del modelo

| Métrica                      | Modelo Inicial | Modelo Optimizado |
|------------------------------|----------------|-------------------|
| **Accuracy (train)**         | 0.99977        | 0.99981           |
| **Accuracy (test)**          | 0.99861        | 0.99871           |
| **MSE**                      | 3897.59        | 3610.50           |
| **MAE**                      | 22.94          | 21.81             |
| **RMSE**                     | 62.43          | 60.09             |
| **R² (Coef. de Determinación)** | 0.99861        | 0.99871           |

![modelo](https://github.com/Oghalis/sales-predictions/assets/148403071/814bc46f-87ba-4c7d-9af4-1109f38916f2)


La optimización del modelo de Random Forest mediante Grid Search ha mejorado la precisión y reducido los errores en la predicción de datos, como demuestra la ligera mejora en las métricas de precisión tanto en los conjuntos de entrenamiento como de prueba, así como una notable reducción en el MSE, MAE, y RMSE. Aunque el coeficiente de determinación (R²) aumentó sutilmente, sugiriendo un mejor ajuste del modelo, persisten algunas discrepancias en la predicción de valores altos, lo que indica la necesidad de futuras investigaciones para afinar aún más el modelo y abordar estos desafíos específicos.

<a id='sec_9'></a>
# :books: Conclusiones y Recomendaciomes
* El público objetivo de la empresa son clientes habituales orientados a productos mayormente saludables, y que conocen bien a los productos.
* Los productos bajos en grasa son el 64.7%, sin embargo no predominan en las ventas. Se podria diversificar los productos, aumentado a mas productos regulares, y por otro lado realizar campañas enfocadas a mostrar los beneficios de consumir productos bajos en grasa.
* Aunque los productos de bajo costo dominan las ventas, explorar el potencial de introducir productos con mayor valor añadido puede ayudar a aumentar los márgenes de ganancia. Para ello es ideal considerar un MRP  menor a 200 como precio de entrada.
* Se debe aumentar la visibilidad y publicidad de aquellos productos con menores ventas, a fin de poder captar a nuevos clientes.
* Las categorias que representan menores ventas (tales como Breakfast y Seafood), deben ser ofertadas en parquetes de productos que combinen articulos de alta rotacion de ventas.
* Realizar un análisis más profundo de las tiendas inauguradas en 1998 y 2009 para identificar causas de su bajo rendimiento y desarrollar estrategias de recuperación.

<a id='sec_10'></a>
## :movie_camera: Presentación

<a id='sec_11'></a>
## :information_source: Disclaimer
El contenido de este repositorio está destinado únicamente para uso personal y no debe ser copiado o utilizado para fines de cualquier evaluación.
