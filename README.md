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
10. [Disclaimer](#sec_10)

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

## Cantidad de ventas por ubicación de tienda y tipo de tienda


<a id='sec_6'></a>

<a id='sec_10'></a>
## Disclaimer
El contenido de este repositorio está destinado únicamente para uso personal y no debe ser copiado o utilizado para fines de cualquier evaluación.
