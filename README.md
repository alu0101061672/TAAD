

Máster Universitario en Ciberseguridad e Inteligencia de Datos

Sistemas recomendadores

Técnicas Avanzadas de Análisis de Datos

Sonia Díaz Santos





Máster Universitario en Ciberseguridad e Inteligencia de Datos

**Índice**

**Introducción**

Objetivo

**3**

3

3

4

Metodología

Resultados esperados

**Análisis Exploratorio de Datos**

Instalación de librerías

Preprocesado de datos

Lectura de ficheros

**5**

5

5

5

5

8

Limpieza de datos

Unión de ambos documentos

**Creación de la tabla**

Índice del término y término

TF-IDF

**9**

9

11

**Similaridad del coseno**

**Resultados y conclusiones**

**Referencias**

**12**

**14**

**16**

2





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Introducción

A continuación se va a describir el trabajo realizado, comenzando con el objetivo general del

proyecto, la metodología que se ha seguido y los resultados esperados.

Objetivo

El objetivo de este proyecto es implementar un sistema de recomendación basado en

contenido, que nos permita recomendar los mejores documentos para un cliente, mediante

el algoritmo de clasificación KNN.

Metodología

Crear un software que reciba un archivo de texto plano con extensión .txt, que contenga el

conjunto de posibles documentos a recomendar al usuario final. Cada documento viene

representado en una línea del archivo.

En este caso, el fichero de texto plano con los posibles documentos a recomendar al

usuario final es el siguiente:

3





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Se ha generado un fichero de texto con algunos documentos que le han gustado a dicho

usuario como se puede observar en la siguiente figura:

Resultados esperados

El software debe proporcionar como salida lo siguiente:

● Para cada documento, tabla con las siguientes columnas:

○

○

○

○

Índice del término.

Término.

TF.

IDF.

○ TF-IDF.

● Similaridad coseno entre cada par de documentos.

4





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Análisis Exploratorio de Datos

En esta sección se va a llevar a cabo el análisis exploratorio de datos, incluyendo la

instalación de las librerías necesarias, el preprocesado de los datos para leer los ficheros, la

limpieza de dichos datos y la unión de los posibles documentos a recomendar con los que le

han gustado al usuario.

Instalación de librerías

Se procede a instalar las librerías necesarias para llevar a cabo este proyecto:

Preprocesado de datos

A continuación, se van a leer los ficheros de los posibles documentos a recomendar y los

documentos que le han gustado al usuario. Posteriormente, se van a limpiar los datos y a

unir ambos documentos.

Lectura de ficheros

En este apartado se van a leer los documentos necesarios para la realización de este

proyecto. El fichero de los documentos a recomendar al usuario y el fichero de los

documentos que le han gustado al usuario.

Limpieza de datos

Ahora se van a limpiar los datos leídos anteriormente:

5





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Como resultado se obtiene el siguiente resultado:

El próximo paso es crear un bucle para recorrer los documentos y realizar dos funciones. La

primera es crear un array de índices idx en el que se almacenan los números de los

documentos, para posteriormente generar una columna con los números de los

documentos. La segunda es eliminar de la columna de documentos el número y el punto al

inicio de cada uno. También se quita el punto final de cada documento:

Obteniendo el array de índices idx:

6





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Se ordena el *dataframe* por los valores de los números de documentos de valor más bajo al

más alto:

Se coloca como índice el número del documento:

Los documentos que le han gustado al usuario son los siguientes:

7





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Unión de ambos documentos

El siguiente paso es unir los posibles documentos a recomendar y los documentos que le

han gustado al usuario.

8





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Creación de la tabla

Ahora se va a crear la tabla de documentos que cuenta con el índice del término, el término

y el TF-IDF de cada uno de los documentos, tanto de los posibles a recomendar como los

que le han gustado al usuario.

Para ello, se crea un nuevo *dataframe* que cuenta con las mismas filas que números de

documentos y con las columnas correspondientes: Índice del término, Término y TF-IDF:

Índice del término y término

En esta sección se van a calcular los datos de las columnas índice del término y término.

El resultado obtenido es el que se muestra en la siguiente imagen:

9





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Se muestra el primer documento en la columna término como un array de todos los

términos del documento:

Se verifica que se ha realizado correctamente:

10





Máster Universitario en Ciberseguridad e Inteligencia de Datos

TF-IDF

En esta sección se van a calcular los datos de la columna TF-IDF. TF-IDF es una

abreviatura de Term Frequency-Inverse Document Frequency. Este es un algoritmo muy

común para transformar el texto en una representación significativa de números que se

utiliza para ajustar el algoritmo de la máquina para la predicción. Se genera la matriz TF-IDF

y se añaden los valores a la tabla como una matriz densa.

Para ello, se crea un array con todos los documentos, se crea el vector TF-IDF para cada

uno y se asigna el resultado a la tabla creada anteriormente:

En la siguiente imagen se puede observar todos los términos del documento y su ubicación

en el documento:

11





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Se genera con éxito la matriz TF-IDF en la tabla:

Similaridad del coseno

Primero, se calcula la matriz TF-IDF de todos los documentos:

Como resultado se genera la siguiente matriz de similaridad del coseno:

12





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Como para la siguiente función el índice tiene que empezar en 0, se genera una lista de los

índices de la tabla restándole un valor. De esta manera, el documento 0 realmente es el

documento 1 y el documento 9 es el documento 10:

Se obtiene como resultado las medidas de similaridad entre documentos en forma de

matriz:

Como en la matriz se tienen los mismos valores en el triángulo superior como inferior se va

a obtener solamente el inferior:

13





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Resultados y conclusiones

Para obtener los resultados se realiza la siguiente función:

En esta función recorre el triángulo inferior de las medidas de similaridad entre documentos

con los índices desde el 0 hasta el 9, que corresponde a un documento respecto al resto de

los documentos. Posteriormente se recorre internamente cada uno de los documentos

respecto a ese documento. Se ha optado por recomendar aquellos documentos que tengan

un valor superior al 0,6 y menor a 1 (el documento consigo mismo).

Se obtiene como resultado las siguientes recomendaciones:

Se pueden comprobar los resultados con la matriz anteriormente creada o con el triángulo

inferior, en este caso se verá con la matriz. Hay que tener en cuenta que en la función se le

sumó un valor al índice, así que los documentos que se recomiendan realmente hay que

restar un valor al índice. Con estas consideraciones se pueden verificar los resultados:

14





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Se puede concluir que se ha construido un sistema recomendador que, con dos ficheros de

entrada, uno con los posibles documentos a recomendar al usuario con un formato

específico y otro con los documentos que le han gustado al usuario, puede recomendar

aquellos que tengan una similitud de al menos 0,6. Con lo que se ha logrado el objetivo

inicial de recomendar a un usuario nuevos documentos conociendo algunos que le hayan

gustado previamente en base a la similitud entre ellos.

15





Máster Universitario en Ciberseguridad e Inteligencia de Datos

Referencias

[1] Fuente del conjunto de datos, posibles documentos a recomendar (documents.txt):

<https://drive.google.com/file/d/1kJ91jBvhxpny2m3UfvI3YhY6T0BsliV5/view?usp=sharing>

[2] Fuente del conjunto de datos, posibles documentos a recomendar (documents\_liked.txt):

[https://drive.google.com/file/d/13iD9qvDBMd_gPeMr7NRm_-2DQigWepTP/view?usp=sharin](https://drive.google.com/file/d/13iD9qvDBMd_gPeMr7NRm_-2DQigWepTP/view?usp=sharing)

[g](https://drive.google.com/file/d/13iD9qvDBMd_gPeMr7NRm_-2DQigWepTP/view?usp=sharing)

[3] Repositorio GitHub: <https://github.com/alu0101061672/TAAD.git>

16

