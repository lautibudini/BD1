
### Parte 1 - Datos abiertos

#### Ejercicio 1

Investigar y mencionar 3 sitios de datos abiertos donde se puedan obtener datasets relevantes para diferentes análisis a realizar. Describa el tipo de datos que se puede encontrar en cada uno. 

Respuesta : 

En `datos.org.ar` el cual es un portal oficial de datos abiertos de Argentina. 
- Tipo de dato : Educación, transporte, salud, economia, medio ambiente, estadisticas publicas, etc. 
En `data.gob` el cual es un portal de datos abiertos del gobierno de EEUU
- Tipo de dato : Energia, agricultura, clima, defensa, empleo, demografia, tecnologia. 
En `data.europa.eu` el cual es un portal europeo de datos abiertos. 
- Tipo de dato : Economía, ciencia, transporte, salud publica, etc. 

#### Ejercicio 2

¿Cuál es la diferencia entre datos públicos y datos abiertos? Proporciona un ejemplo de cada tipo. 

Respuesta : 

Los *Datos Públicos* son aquellos generados o administrados por el gobierno, pero no necesariamente accesibles o reutilizables por cualquiera. 
Ej : Puede ser un informe estadístico anual publicado en PDF por un ministerio. 

Los *Datos Abiertos* son datos públicos (o privados) que pueden ser accedidos, usados y compartidos libremente, con atribución y bajo una licencia abierta. 
Ej : Un dataset en formato CSV con los resultantes del censo, publicado en un portal.

> Todos los datos abiertos pueden ser públicos, pero no todos los datos públicos son abiertos.

#### Ejercicio 3

Mencione 3 tipos de licencias que pueden tener los datos abiertos, describiendo diferencias entre ellas. 

Respuesta : 

| **Licencia**                                                      | **Condiciones principales**                                                     | **Diferencias clave**                 |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------- |
| **Open Data Commons Public Domain Dedication and License (PDDL)** | Permite usar, copiar y redistribuir los datos sin restricciones.                | Es la más libre: no exige atribución. |
| **Open Data Commons Attribution License (ODC-By)**                | Permite reutilizar los datos siempre que se reconozca la autoría.               | Requiere **atribución obligatoria**.  |
| **Open Database License (ODbL)**                                  | Permite usar los datos, pero las obras derivadas deben compartirse con la misma |                                       |

#### Ejercicio 4

Suponga que tiene acceso a un dataset abierto sobre los niveles de contaminación del aire en diferentes ciudades del país. ¿Qué tipos de análisis podría realizar para obtener información útil? 

Respuesta : 

Se podrían hacer varios análisis útiles como : 
- Comparativo entre ciudades (Identificar cuales presentan mayor nivel de contaminación)
- Evolución temporal (Analizar como varia la calidad del aire a lo largo del tiempo)
- Alertas ambientales (Detectar picos de contaminación que superan los niveles recomendados)

> Estos análisis responden a uno de los beneficios de los datos abiertos que es mejorar la toma de decisiones basadas en evidencias empíricas. 

#### Ejercicio 5

¿Cuáles son las condiciones de la licencia creative commons? 

Respuesta : 

La *Creative commons* permite copiar, distribuir y adaptar los datos para cualquier propósito, incluso comercial, siempre que se cumplan ciertas condiciones.
Las cuales son : 
1. Atribución (Debe citarse la fuente)
2. No comercial (Algunos tipos de CC incluyen la restricción de no usar los datos con fines comercial)
3. Sin obras derivadas (Puede prohibirse modificar el material original)
4.  Compartir igual (Si se crean obras derivadas, deben distribuirse bajo la misma licencia)

#### Ejercicio 6

¿Qué significa tener datos IA-ready? 

Respuesta : 

Tener datos IA- READY significa que los datos estan tecnica y estructuralmente para ser utilizados eficazmente por sistemas de inteligencia artificial.
Debe cumplir con : 
- Completitud
- Ausencia de errores o inconsistencias
- Uso de formas adecuadas y estructuras homogeneas
- Metadatos claros y contexto suficiente
- Licencias claras
>El objetivo es que los modelos de IA se entrenen con datos de calidad, sin sesgos ni errores  que afectan los resultados. 


#### Ejercicio 7

¿Cuáles son los principios FAIR-R y sus requisitos?

Respuesta : 

Los **principios FAIR-R** amplían los principios FAIR tradicionales (Findable, Accessible, Interoperable, Reusable) agregando la “R” de _Ready for AI_.

- **Findable (Fácil de encontrar):** los datos deben tener metadatos y un identificador único.
- **Accessible (Accesibles):** disponibles mediante protocolos abiertos, con licencias claras.
- **Interoperable:** compatibles con otros sistemas y formatos estándar.
- **Reusable (Reutilizables):** con información suficiente sobre su origen, licencias y calidad.

### Parte 2 - Visualización de datos

Responda las siguientes preguntas sobre visualización de datos: 

#### Ejercicio 1

Explique que es una medida y una dimensión 

Respuesta : 

Una *Dimensión* es un atributo descriptivo o categórico que se usa para dividir o agrupar los datos. 
Ej : Ciudad, mes, tipo de combustible, sexo, categoría, etc. 

Una *Medida* es un valor numérico que se puede calcular o agregar (sumar, promediar, contar)
Ej : Cantidad de ventas, Nivel de contaminación, Temperatura promedio, etc. 

> En una visualización, las dimensiones suelen estar en los ejes o etiquetas, y las medidas se grafican como valores (barras, líneas, etc.).


#### Ejercicio 2

Explique la diferencia entre un dato discreto y un dato continuo 

Respuesta : 

Un *Dato Discreto* toma valores enteros y finitos, no puede dividirse en partes más pequeñas significativas. 
Ej : Cantidad de autos, numero de personas, cantidad de accidentes. 

>Se representan con gráficos de barras o columnas. 

Un *Dato Continuo*  puede tomar cualquier valor dentro de un rango, incluyendo decimales. 
Ej : Temperatura, peso, nivel de contaminación, etc. 

> Se representan con gráficos de líneas o histogramas. 


#### Ejercicio 3

¿Por qué es importante preparar los datos?

Respuesta : 

Preparar los datos es clave antes de analizarlos o visualizarlos ya que : 
- Evita errores
- Asegura calidad
- Facilita el análisis
- Mejora la interpretación 
- Optimiza el rendimiento

> Preparar los datos es **como limpiar y ordenar la información antes de visualizarla**, para que lo que se muestre sea correcto y útil.

#### Parte practica 

Dadas las situaciones que se presentan a continuación, decidir qué tipo de gráfico utilizaría para visualizar la información de manera clara y efectiva. Justifique su elección indicando por qué ese tipo de gráfico es el más adecuado para cada caso.

#### A - Comparación de suscripciones anuales por región geográfica 

Se cuenta con un conjunto de datos de las suscripciones anuales de una empresa de telefonía celular en distintas regiones (Norte, Sur, Este, Oeste) durante los últimos 5 años. ¿Qué tipo de gráfico utilizaría para comparar las ventas entre las regiones durante los 5 años?

Respuesta : 

Dimensiones : Región y año.
Medida : Cantidad de suscripciones (Numérica). 
Objetivo : Comparar las regiones y ver como evolucionaron en el tiempo. 

Grafico : De barras agrupadas

Utilizaría un grafico de barras, cada grupo de barra representa un año especifico (2021, 2022...) y dentro de cada grupo hay 4 barras que representan las ventas por cada región (sur,este,....). 

#### B - Análisis de la distribución de las edades de clientes 

Se tiene un dataset con datos de los clientes de una tienda virtual, entre ellos, la edad. El objetivo es entender cómo se distribuyen las edades de los clientes. ¿Qué tipo de gráfico utilizará para representar la distribución de las edades de los clientes?

Respuesta : 

El dato *Edad* es un dato numerico continuo ya que puede tomar muchos valores dentro de un rango.
Es una medida.

Nos interesa ver como esta distribuida las edades de los clientes, mostrar ese porcentaje de cada uno. 

Grafico : Grafico de barras
Usaría un **gráfico de barras** (con rangos de edad como categorías en el eje X).



#### C - Relación entre el precio y la puntuación otorgada por el cliente 

Se tiene información sobre el precio de diferentes servicios ofrecidos y la calificación otorgada por los clientes. ¿Qué tipo de gráfico usaría para analizar si existe una relación entre el precio del producto y la puntuación marcada por el cliente?

Respuesta : 

Precio -> Variable numerica continua 
Puntuacion del cliente -> Tambien una variable numerica continua

Como queremos saber como se relacionan dos variables numericas continuas lo ideal es mostrar un grafico que muestre pares de valores (x,y)

Grafico : Dispersion 
Cada punto representa un servicio:
- El eje **X** muestra el **precio**.
- El eje **Y** muestra la **puntuación**.
Así podés observar si hay alguna tendencia (por ejemplo, que los servicios más caros tienen mejor puntuación o no)

El **gráfico de dispersión** permite visualizar la relación entre dos variables numéricas.  
En este caso, muestra si existe una correlación entre el **precio del servicio** y la **puntuación otorgada por los clientes**.  
Si los puntos siguen una línea ascendente, hay una relación positiva; si desciende, negativa; si están dispersos sin patrón, no hay relación.

#### D - Análisis de los préstamos de libros por género 

Se cuenta con el registro de los préstamos de una biblioteca escolar. Entre los datos de cada uno de estos se tiene el género del libro (narrativa, poesía, cuento, novela y biografía). ¿Qué gráfico es adecuado para visualizar la proporción de préstamos de cada género?

Respuesta : 

Ya que se desea mostrar una proporción de prestamos según el genero de los libros. 
Donde el tipo de dato son las 5 categorías. 

El grafico más adecuado es el grafico *De Torta* ya que nos permite ver claramente porcentajes según las categorías de datos sobre el total. 

#### E - Se han almacenado datos de registro de la temperatura promedio del mar, a partir de mediciones diarias frente a la costa de Las Toninas, un kilómetro mar adentro. Esta medición se viene realizando durante los últimos 7 años para estudios del comportamiento de la fauna del lugar. 
Dado el siguiente esquema de la base de datos: 

TipoGradoTemp(#tipoGradoTemp, descripcionTipoGrado) 
TemperaturaRegistrada(#registroTemp, fecha, hora, valorTemp, #tipoGradoTemp) 
TemperaturasPromedio(#registroProm, fecha, valorProm) 

a) ¿Qué tipo de gráfico utilizará para mostrar los cambios de la temperatura promedio a lo largo del tiempo? 
b) ¿Cuáles tablas son relevantes para presentar el análisis?

Además, el dataset muestra la cantidad de especies que se identificaron en el mar en las 5 distintas categorías (Moluscos, Artrópodos, Cnidarios, Peces y Mamíferos marinos).

Respuesta : 

Datos : temperatura promedio 
Objetivo : Mostrar como cambia a lo largo del tiempo . 

Grafico : **líneas**, porque muestran claramente la evolución temporal y permiten ver tendencias, subidas y bajadas..

Las tabla relevante es TemperaturasPromedio, ya que contiene la fecha y el valor promedio de temperatura diario.

> Para la cantidad de especies que se identificaron en el mar (las cuales son 5) utilizaría un grafico de torta ya que nos permite ver fácilmente el porcentaje que representa cada categoría sobre el total de las especies. 


#### F - Dado el siguiente esquema de la base de datos:

CategoriaEspecie (#cat_especie, cat_nombre ) 
EspecieIdentfificada (#especie, #cat_especie, nombre_especie, cantidad) 

c) ¿Qué gráfico utilizaría si se quiere visualizar la proporción de especies de cada categoría? 
d) De todas las tablas propuestas, indicar cuál o cuáles son relevantes para presentar el análisis

Respuesta : 

Si se quiere visualizar la proporción de especies de cada categoria utilizaria un grafico de torta?? no se si hay otra opcion mejor de las que me dan

Utilizaria la tabla EspecieIdentificada, ya que uso los atributos especie y cat_especie. Si se desea mostrar el nombre utilizaria CategoriaEspecie para mostrar el nombre de la misma en lugar de su id.

#### G - Visualización de las estadísticas de una cadena de supermercados 

Una cadena de supermercados quiere contar con estadísticas de las ventas por sucursal y por tipo de producto a lo largo del último año (mes a mes). Se quiere identificar las sucursales con mayores ventas y los tipos de productos que generan más ingresos. 
Esta cadena de supermercados quiere visualizar: 
-  La cantidad de productos vendidos de cada categoría para todas las sucursales, para conocer qué tipo de producto es el que más se vende. 
- El total ingresos de la sucursal número 10, mes a mes, durante los últimos 12 meses, para determinar si hubo o no un incremento de los ingresos. 

Para ello dispone de una base de datos con el siguiente esquema: 

Venta (id_venta, fecha_venta, id_sucursal, monto_total) 
Item_Venta (id_venta, id_producto, cant) 
Sucursal (id_sucursal, ubicación, cant_empleados) 
Producto (id_producto, nombre_producto, desc_producto ,precio_unit, categoria) 
Cliente (id_cliente, nombre_cliente, apellido_cliente, tipo_cliente) 

Determine qué tipo de gráfico podría utilizar y justifique su elección. Con los esquemas proporcionados, elegir cuáles -con sus atributos- son relevantes para presentar el análisis visual propuesto anteriormente. 

Respuesta : 

Para visualizar la cantidad de productos vendidos de cada categoría para todas sus sucursales (Queriendo saber que producto es el que más se vende).
Utilizaría un grafico de *Barras* donde mostremos la cantidad vendida por cada categoría el cual nos sirve para comparar esto mencionado. 
Los atributos serian : 
De Venta saco el id_venta, de Item_Venta usaria id_producto y cant, para luego sacar de Producto categoría. 

Para visualizar el total de ingresos de la sucursal n10, mes a mes durante los ultimos 12 meses (Para determinar si hubo o no un incremento de los ingresos). 
Utilizaría un grafico *Lineas* donde el tiempo seria de 12 meses viendo cada mes el total de ingresos que tuvo y poder tener un grafico donde pueda verse el crecimiento.
Los atributos serian : 
Me quedo con el id de la sucursal N10 y las ventas de esa sucursal (monto)

