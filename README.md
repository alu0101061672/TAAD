## Sistemas recomendadores

### Técnicas Avanzadas de Análisis de Datos

## Introducción

A continuación se va a describir el trabajo realizado, comenzando con el objetivo general del proyecto, la metodología que se ha seguido y los resultados esperados.

### Objetivo

El objetivo de este proyecto es implementar un sistema de recomendación basado en contenido, que nos permita recomendar los mejores documentos para un cliente, mediante el algoritmo de clasificación KNN.

### Metodología

Crear un software que reciba un archivo de texto plano con extensión .txt, que contenga el conjunto de posibles documentos a recomendar al usuario final. Cada documento viene representado en una línea del archivo. 

Se ha generado un fichero de texto con algunos documentos que le han gustado a dicho usuario.

### Resultados esperados

El software debe proporcionar como salida lo siguiente:

* Para cada documento, tabla con las siguientes columnas:
    *  Índice del término.
    *  Término.
    *  TF.
    *  IDF.
    * TF-IDF.
* Similaridad coseno entre cada par de documentos.

## Análisis Exploratorio de Datos

En esta sección se va a llevar a cabo el análisis exploratorio de datos, incluyendo la instalación de las librerías necesarias, el preprocesado de los datos para leer los ficheros, la limpieza de dichos datos y la unión de los posibles documentos a recomendar con los que le han gustado al usuario.


### Instalación de librerías

Se procede a instalar las librerías necesarias para llevar a cabo este proyecto.


### Preprocesado de datos

A continuación, se van a leer los ficheros de los posibles documentos a recomendar y los documentos que le han gustado al usuario. Posteriormente, se van a limpiar los datos y a unir ambos documentos.


#### Lectura de ficheros

En este apartado se van a leer los documentos necesarios para la realización de este proyecto. El fichero de los documentos a recomendar al usuario y el fichero de los documentos que le han gustado al usuario.

#### Limpieza de datos

Ahora se van a limpiar los datos leídos anteriormente.

El próximo paso es crear un bucle para recorrer los documentos y realizar dos funciones. La primera es crear un array de índices idx en el que se almacenan los números de los documentos, para posteriormente generar una columna con los números de los documentos. La segunda es eliminar de la columna de documentos el número y el punto al inicio de cada uno. También se quita el punto final de cada documento.

Se ordena el _dataframe_ por los valores de los números de documentos de valor más bajo al más alto. Se coloca como índice el número del documento.

#### Unión de ambos documentos

El siguiente paso es unir los posibles documentos a recomendar y los documentos que le han gustado al usuario.

## Creación de la tabla

Ahora se va a crear la tabla de documentos que cuenta con el índice del término, el término y el TF-IDF de cada uno de los documentos, tanto de los posibles a recomendar como los que le han gustado al usuario.

Para ello, se crea un nuevo _dataframe_ que cuenta con las mismas filas que números de documentos y con las columnas correspondientes: Índice del término, Término y TF-IDF.

### Índice del término y término

En esta sección se van a calcular los datos de las columnas índice del término y término.

### TF-IDF

En esta sección se van a calcular los datos de la columna TF-IDF. TF-IDF es una abreviatura de Term Frequency-Inverse Document Frequency. Este es un algoritmo muy común para transformar el texto en una representación significativa de números que se utiliza para ajustar el algoritmo de la máquina para la predicción. Se genera la matriz TF-IDF y se añaden los valores a la tabla como una matriz densa.

Para ello, se crea un array con todos los documentos, se crea el vector TF-IDF para cada uno y se asigna el resultado a la tabla creada anteriormente. Se genera con éxito la matriz TF-IDF en la tabla.

## Similaridad del coseno

Primero, se calcula la matriz TF-IDF de todos los documentos. Como resultado se genera la matriz de similaridad del coseno.

Como para la siguiente función el índice tiene que empezar en 0, se genera una lista de los índices de la tabla restándole un valor. De esta manera, el documento 0 realmente es el documento 1 y el documento 9 es el documento 10.

Se obtienen como resultado las medidas de similaridad entre documentos en forma de matriz. Como en la matriz se tienen los mismos valores en el triángulo superior como inferior se va a obtener solamente el inferior.

## Resultados y conclusiones

Para obtener los resultados se realiza una función. Esta función recorre el triángulo inferior de las medidas de similaridad entre documentos con los índices desde el 0 hasta el 9, que corresponde a un documento respecto al resto de los documentos. Posteriormente se recorre internamente cada uno de los documentos respecto a ese documento. Se ha optado por recomendar aquellos documentos que tengan un valor superior al 0,6 y menor a 1 (el documento consigo mismo).

Se obtienen como resultado las recomendaciones.

Se pueden comprobar los resultados con la matriz anteriormente creada o con el triángulo inferior, en este caso se verá con la matriz. Hay que tener en cuenta que en la función se le sumó un valor al índice, así que los documentos que se recomiendan realmente hay que restar un valor al índice. Con estas consideraciones se pueden verificar los resultados.

Se puede concluir que se ha construido un sistema recomendador que, con dos ficheros de entrada, uno con los posibles documentos a recomendar al usuario con un formato específico y otro con los documentos que le han gustado al usuario, puede recomendar aquellos que tengan una similitud de al menos 0,6. Con lo que se ha logrado el objetivo inicial de recomendar a un usuario nuevos documentos conociendo algunos que le hayan gustado previamente en base a la similitud entre ellos.

## Ejemplo de uso

Se deben de cargar los dos ficheros mencionados. Los posibles documentos a recomendar y los documentos que le han gustado al usuario. Una vez se han cargado los documentos con los formatos determinados, se ejecuta todo el código para obtener las recomendaciones.

El formato debe ser como se muestra a continuación para el fichero de posibles documentos a recomendar:

![alt text](https://github.com/alu0101061672/TAAD/blob/main/posibles_documentos.png)

Para el fichero de documentos que le han gustado:

![alt text](https://github.com/alu0101061672/TAAD/blob/main/documentos_gustados.png)

Por último, en el ejemplo propuesto en el código el resultado obtenido de la recomendación es: 

<img width="719" alt="recomendación" src="https://user-images.githubusercontent.com/43813221/190129896-cc727320-4a7f-403a-a844-67f556e70ecb.png">

Se pueden verificar los resultados obtenidos mirando la matriz:

<img width="647" alt="verificación_recomendación" src="https://user-images.githubusercontent.com/43813221/190130038-631ac0f5-08ba-4f08-ac80-176c530fe617.png">

