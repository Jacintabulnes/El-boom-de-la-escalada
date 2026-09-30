# Documentación base PISA Lectura
## Descripción
Este trabajo documenta el proceso de preparación y limpieza de una base de datos sobre desempeño en lectura a partir de los resultados del Programa para la Evaluación Internacional de los Estudiantes (PISA) de la OCDE.

El objetivo de la base es disponer de datos estructurados que permitan analizar dos dimensiones relevantes para el proyecto: la evolución del desempeño lector de Chile entre PISA 2022 y PISA 2025 y la posición de Chile en comparación con otros países y economías participantes en PISA 2025.

Para ello se trabajó a partir de las tablas originales publicadas por la OCDE, seleccionando los indicadores relacionados con puntaje promedio y niveles de desempeño en lectura. El resultado del proceso es el archivo `pisa_lectura_limpia.csv`, estructurado para facilitar su análisis posterior con Pandas y su utilización en visualizaciones para la webstory.
## Proceso de limpieza y preparación de los datos

### 1. Revisión de la base original
El proceso comenzó con la revisión del archivo original de resultados de PISA 2025 publicado por la OCDE. Este archivo contiene numerosas tablas estadísticas correspondientes a distintos ámbitos de la evaluación PISA, por lo que gran parte de la información disponible no era necesaria para responder las preguntas específicas de esta investigación.

Durante esta primera revisión se identificó que las tablas originales no estaban estructuradas como una única base de datos lista para analizar. El archivo incluía múltiples hojas, encabezados, títulos, notas metodológicas, filas informativas y diferentes indicadores estadísticos. Por esta razón, utilizar directamente el archivo original habría dificultado tanto el análisis con Pandas como la posterior construcción de visualizaciones.

A partir de esta revisión se decidió reducir el universo de información y trabajar solamente con las tablas relacionadas directamente con el desempeño en lectura. El archivo original se conservó sin modificaciones dentro de la carpeta `datos_originales`, de manera de mantener disponible la fuente primaria y asegurar la trazabilidad del proceso de limpieza.

### 2. Selección de las tablas relevantes
A partir de la revisión del archivo original se seleccionaron cinco tablas vinculadas específicamente con el desempeño en lectura. La selección se realizó considerando su utilidad para comparar a Chile entre distintos ciclos de PISA y para contrastar sus resultados con los de otros países y economías.

Las tablas seleccionadas fueron:

- `Table I.B1.2a.2`: puntaje promedio y variación en el desempeño en lectura.
- `Table I.B1.2a.11`: porcentaje de estudiantes en cada nivel de desempeño en lectura.
- `Table I.B1.2a.34`: evolución del porcentaje de estudiantes de bajo y alto desempeño en lectura.
- `Table I.B1.2a.37`: evolución del puntaje promedio en lectura a través de los distintos ciclos de PISA.
- `Table I.B1.2a.43`: evolución de la variación del desempeño en lectura.

Estas cinco tablas fueron conservadas inicialmente porque permitían explorar distintas dimensiones de la historia. Posteriormente, para construir la base final se priorizaron los indicadores que respondían de forma más directa a las preguntas de investigación: puntaje promedio, porcentaje bajo el Nivel 2 y porcentaje en el Nivel 5 o superior.

Esta decisión permitió reducir la cantidad de información sin perder los indicadores necesarios para el análisis propuesto.

### 3. Selección de variables
Luego de identificar las tablas pertinentes se definieron las variables que formarían parte de la base limpia. El criterio principal fue conservar únicamente aquellas que pudieran ser utilizadas posteriormente para realizar comparaciones y visualizaciones vinculadas con las preguntas de investigación.

Se conservaron cinco variables: `pais_economia`, `anio`, `puntaje_lectura`, `bajo_nivel_2_pct` y `nivel_5_o_superior_pct`.

La variable `puntaje_lectura` permite observar el desempeño promedio y comparar tanto distintos ciclos como países o economías. La variable `bajo_nivel_2_pct` permite identificar qué proporción de los estudiantes evaluados se encuentra bajo el Nivel 2 de desempeño. Finalmente, `nivel_5_o_superior_pct` permite observar la proporción ubicada en los niveles superiores de desempeño.

Se excluyeron de la base final otras variables presentes en las tablas originales, como errores estándar, percentiles, medidas adicionales de dispersión y otros indicadores que no serían utilizados directamente en las visualizaciones previstas. Los archivos originales se conservaron para que esta información pueda ser recuperada en caso de que sea necesaria durante etapas posteriores de la investigación.

### 4. Reestructuración de los datos
Las tablas originales de la OCDE presentan los indicadores en estructuras diferentes, con encabezados de varias filas, títulos, notas y columnas estadísticas adicionales. Para facilitar el análisis, la información seleccionada fue reorganizada en una única estructura tabular.

Se adoptó un formato en el que cada fila corresponde a la observación de un país o economía en un determinado año, mientras que cada columna representa una variable. De esta manera, los indicadores provenientes de distintas tablas pudieron integrarse bajo una estructura común.

La reorganización permitió vincular el puntaje promedio de lectura con los porcentajes de estudiantes bajo el Nivel 2 y en el Nivel 5 o superior para cada observación disponible. Esta estructura facilita posteriormente operaciones como filtrar Chile, comparar los ciclos 2022 y 2025 o seleccionar los resultados correspondientes a 2025 para realizar comparaciones internacionales.

### 5. Limpieza y estandarización
Durante el proceso de limpieza se eliminaron los elementos de las tablas originales que no correspondían a observaciones de la base, como títulos, subtítulos, notas al pie y filas vacías. También se descartaron del archivo final las columnas que no fueron seleccionadas para el análisis.

Los nombres de las variables fueron estandarizados utilizando minúsculas y guiones bajos, evitando espacios y caracteres especiales. Así se definieron los nombres `pais_economia`, `anio`, `puntaje_lectura`, `bajo_nivel_2_pct` y `nivel_5_o_superior_pct`.

También se procuró mantener un formato consistente para los nombres de países y economías, de modo que una misma observación pudiera ser identificada correctamente al combinar información proveniente de distintas tablas.

Los indicadores de puntaje y porcentaje se conservaron como valores numéricos. En el caso de los porcentajes, los valores se almacenaron en una escala de 0 a 100 y sin incorporar el símbolo `%` dentro de las celdas, lo que permite realizar cálculos directamente sobre estas variables.

Finalmente, la información relevante proveniente de las distintas tablas fue integrada en una sola base, evitando mantener la estructura fragmentada en múltiples hojas del archivo Excel original.

### 6. Revisión de la base final
Una vez construida la base unificada, se realizó una revisión final para comprobar que su estructura fuera consistente y que pudiera ser utilizada posteriormente para el análisis.

Se verificó que cada columna tuviera un significado único y que cada fila correspondiera a una observación identificable mediante el país o economía y el año. También se revisó que las variables numéricas pudieran ser utilizadas para realizar cálculos y comparaciones.

Además, se comprobó la presencia de las observaciones necesarias para responder las principales preguntas de investigación, especialmente los registros correspondientes a Chile en 2022 y 2025 y los datos de los países y economías disponibles para la comparación internacional de 2025.

Esta revisión permitió comprobar que la base final contara con las variables necesarias para comparar la evolución de Chile y contextualizar sus resultados frente a otros participantes de PISA.

### 7. Exportación
Una vez finalizado el proceso de selección, reestructuración y limpieza, la base fue exportada en formato CSV con el nombre `pisa_lectura_limpia.csv`.

Se eligió el formato CSV porque permite almacenar los datos en una estructura simple y compatible con distintas herramientas de análisis y visualización. Además, este formato permite cargar directamente la base en un DataFrame de Pandas, requisito establecido para esta entrega.

Los archivos originales no fueron reemplazados ni modificados. Se conservaron por separado en la carpeta `datos_originales`, mientras que el CSV corresponde al producto final del proceso de limpieza y preparación.

## Fuentes utilizadas
La fuente utilizada para la construcción de esta base fue el Programa para la Evaluación Internacional de los Estudiantes (PISA), desarrollado por la Organización para la Cooperación y el Desarrollo Económicos (OCDE).

Se escogieron los datos de PISA porque permiten realizar comparaciones internacionales y temporales del desempeño de estudiantes de 15 años bajo una metodología común. Esto resulta especialmente pertinente para el proyecto, ya que permite observar tanto la evolución de Chile entre los ciclos 2022 y 2025 como contextualizar sus resultados frente a otros países y economías participantes.

La fuente principal corresponde a las tablas estadísticas de *PISA 2025 Results (Volume I): Future-Ready Students*. A partir de estas tablas se obtuvieron los indicadores utilizados en la base limpia: puntaje promedio en lectura, porcentaje de estudiantes bajo el Nivel 2 y porcentaje de estudiantes en el Nivel 5 o superior.

Se decidió trabajar con la fuente oficial de la OCDE y conservar los archivos originales descargados como respaldo. De esta manera, los valores presentes en la base limpia pueden ser rastreados hasta las tablas desde las cuales fueron obtenidos.

### Referencias

- OECD (2026), *PISA 2025 Results (Volume I): Future-Ready Students*, OECD Publishing.
- OECD, *PISA 2025 Database*.

## Decisiones metodológicas y editoriales
La principal decisión metodológica fue acotar la base a los indicadores directamente relacionados con las preguntas de investigación. Aunque los archivos originales de PISA contienen una gran cantidad de variables y dimensiones, incorporar toda esa información habría dificultado el análisis y no necesariamente habría contribuido a la historia que se busca desarrollar.

Se decidió trabajar principalmente con tres indicadores de lectura: puntaje promedio, porcentaje de estudiantes bajo el Nivel 2 y porcentaje de estudiantes en el Nivel 5 o superior. El puntaje promedio permite observar cambios generales en el desempeño, mientras que los niveles permiten complementar ese dato mostrando cómo se distribuyen los estudiantes en categorías de desempeño bajo y alto.

También se decidió estructurar la base utilizando al país o economía y al año como identificadores de cada observación. Esta decisión permite realizar dos tipos de comparación: una temporal, enfocada en el cambio de Chile entre PISA 2022 y PISA 2025, y otra internacional, que permite comparar a Chile con los demás países y economías disponibles para 2025.

Otra decisión fue no incorporar en la base limpia todos los indicadores estadísticos presentes en las tablas originales, como errores estándar, percentiles y medidas adicionales de dispersión. Estos datos no fueron eliminados de las fuentes originales, que permanecen disponibles en la carpeta `datos_originales`, pero no se incluyeron en el CSV simplificado debido a que no forman parte de las visualizaciones inicialmente planteadas.

Desde el punto de vista editorial, se optó por no utilizar los resultados de PISA como una medición de la comprensión lectora de todos los niños chilenos. PISA evalúa específicamente a estudiantes de 15 años bajo una metodología determinada, por lo que las conclusiones derivadas de esta base deben referirse a esa población y evaluación.

Finalmente, se consideró que las comparaciones observadas en la base son descriptivas. Una variación entre 2022 y 2025 permite identificar un cambio en los indicadores, pero no permite establecer por sí sola las causas de dicho cambio. La explicación de posibles causas requerirá complementar el análisis de datos con otras fuentes, estudios y entrevistas durante el desarrollo de la webstory.

## Preguntas que permite responder la base
A partir de la base limpia es posible responder, entre otras, las siguientes preguntas:

1. **¿Cómo cambió el puntaje promedio de lectura de Chile entre PISA 2022 y PISA 2025?**

   Esta pregunta puede responderse filtrando las observaciones correspondientes a Chile y comparando la variable `puntaje_lectura` entre ambos años.

2. **¿Cómo cambió el porcentaje de estudiantes chilenos bajo el Nivel 2 de desempeño en lectura entre 2022 y 2025?**

   La variable `bajo_nivel_2_pct` permite observar si aumentó o disminuyó la proporción de estudiantes ubicada bajo este nivel entre ambos ciclos.

3. **¿Cómo se compara el desempeño promedio en lectura de Chile con el de otros países y economías en PISA 2025?**

   Al filtrar la base por el año 2025, es posible comparar el valor de `puntaje_lectura` de Chile con los resultados disponibles para otros participantes.

4. **¿Qué diferencias existen entre países y economías en la proporción de estudiantes de bajo y alto desempeño en lectura en PISA 2025?**

   Las variables `bajo_nivel_2_pct` y `nivel_5_o_superior_pct` permiten comparar la distribución de estudiantes en ambos extremos del desempeño y contextualizar la situación de Chile.

## Posibles usos para la visualización
La estructura de la base permite desarrollar visualizaciones orientadas a mostrar tanto la evolución temporal de Chile como su posición en el contexto internacional.

Una primera visualización puede comparar los resultados de Chile entre PISA 2022 y PISA 2025. Esta comparación puede mostrar el cambio en el puntaje promedio de lectura y complementarse con la variación en el porcentaje de estudiantes bajo el Nivel 2. De esta manera, la evolución no se representa únicamente mediante un puntaje promedio, sino también mediante un indicador relacionado con los niveles de desempeño.

Una segunda visualización puede situar a Chile dentro de los resultados internacionales de PISA 2025. Para ello, es posible ordenar los países y economías según su puntaje promedio en lectura y destacar visualmente la posición de Chile. También se puede realizar una comparación utilizando el porcentaje de estudiantes bajo el Nivel 2.

Estas visualizaciones permitirían construir una narración que avance desde el cambio observado dentro de Chile entre ambos ciclos hacia una contextualización internacional de sus resultados. La base limpia funciona, por lo tanto, como insumo para transformar los resultados estadísticos de PISA en elementos visuales que contribuyan a la webstory.
