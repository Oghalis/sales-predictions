# :chart_with_upwards_trend: Predicción de Ventas de Productos Alimenticios en Tiendas - Big Mart Sales Prediction
---
![SALES PREDICTION](https://github.com/Oghalis/sales-predictions/assets/148403071/dd96e169-d0c0-472d-ba2d-b6b01c5e3424)
* Este repositorio forma parte de uno de los proyectos presentados durante el curso de Análisis de Datos impartido por Coding Dojo.
# :clipboard: Tabla de contenidos
1. [Resumen del Proyecto](#sec_1)
2. [Objetivos del Proyecto](#sec_2)
3. [Dataset/ Diccionario de datos](#sec_3)
4. [Análisis Exploratorio de Datos (EDA)](#sec_4)
5. [Preprocesamiento](#sec_5)
6. [Modelos de Machine Learning](#sec_6)
7. [Evaluación de Modelos](#sec_7)
8. [Resultados y Conclusiones](#sec_8)
9. [Disclaimer](#sec_9)

<a id='sec_1'></a>
# :bookmark_tabs: Resumen del Proyecto
Este proyecto se enfoca en la predicción de ventas de productos alimenticios en varias tiendas utilizando el conjunto de datos "Big Mart Sales Prediction". Mediante técnicas de ciencia de datos y aprendizaje automático, se analizan las características de los productos y los puntos de venta para identificar factores que influyen en el aumento de las ventas. El objetivo es proporcionar a los minoristas herramientas predictivas para comprender mejor el comportamiento del mercado y optimizar sus estrategias comerciales.

<a id='sec_2'></a>
# :dart: Objetivos del Proyecto
## Objetivo Principal
Desarrollar modelos predictivos precisos para estimar las ventas de productos alimenticios en tiendas utilizando el conjunto de datos "Big Mart Sales Prediction".
## Objetivos Secundarios
1. Identificar las características clave de los productos que afectan las ventas, como el peso del artículo, el contenido de grasa, el tipo de artículo y el precio MRP (Maximum Retail Price).
2. Analizar la influencia de las características del punto de venta, como el tamaño del establecimiento, la ubicación y el tipo de tienda, en las ventas de productos.
3. Proporcionar a los minoristas una comprensión detallada de los factores que impulsan las ventas y sugerir estrategias para mejorar el rendimiento de ventas.
4. Documentar el proceso de desarrollo del modelo y compartir el código en un repositorio público en GitHub para su revisión, colaboración y uso como referencia para futuras investigaciones y análisis relacionados con el proyecto.

<a id='sec_3'></a>
# :floppy_disk: Dataset / Diccionario de datos
El dataset utilizado en este proyecto consta de 8523 entradas y 12 columnas. 
A continuación se detallan las columnas presentes en el dataset:

| Columna                     | Tipo    | Descripción                                                                  |
|-----------------------------|---------|------------------------------------------------------------------------------|
| Item_Identifier             | Objeto  | Identificador único para cada artículo.                                      |
| Item_Weight                 | Float   | Peso del artículo.                                                           |
| Item_Fat_Content            | Objeto  | Contenido de grasa del artículo.                                              |
| Item_Visibility             | Float   | La proporción de área de escaparate del producto en la tienda.                |
| Item_Type                   | Objeto  | Categoría del artículo.                                                       |
| Item_MRP                    | Float   | Precio máximo de venta del artículo.                                          |
| Outlet_Identifier           | Objeto  | Identificador único para cada tienda.                                         |
| Outlet_Establishment_Year   | Int     | Año de establecimiento de la tienda.                                          |
| Outlet_Size                 | Objeto  | Tamaño de la tienda.                                                          |
| Outlet_Location_Type        | Objeto  | Tipo de ubicación de la tienda.                                               |
| Outlet_Type                 | Objeto  | Tipo de tienda.                                                               |
| Item_Outlet_Sales           | Float   | Ventas del artículo en la tienda.                                             |


El dataset presenta valores faltantes en las columnas Item_Weight y Outlet_Size, que serán tratados durante el análisis exploratorio de datos. Además, se observa una variedad de los mismos, incluyendo variables categóricas y numéricas, que serán consideradas tanto durante el mismo análisis exploratorio de datos como en la construcción de modelos de machine learning.

<a id='sec_4'></a>
# :bar_chart: Análisis Exploratorio de Datos (EDA)
![descarga (9)](https://github.com/Oghalis/sales-predictions/assets/148403071/470d001f-7737-436a-8c18-34ef383d5b7e)

<a id='sec_9'></a>
## Disclaimer
El contenido de este repositorio está destinado únicamente para uso personal y no debe ser copiado o utilizado para fines de cualquier evaluación.
