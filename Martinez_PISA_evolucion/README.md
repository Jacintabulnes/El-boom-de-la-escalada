# Documentación base PISA — Evolución histórica de Chile

## Descripción
Este trabajo documenta el proceso de preparación y limpieza de una base de datos destinada a analizar la evolución histórica del desempeño lector de Chile en PISA.

A diferencia de otras bases del proyecto enfocadas en comparar a Chile con otros países o en observar específicamente los resultados recientes, esta base adopta una perspectiva temporal. Su objetivo es reunir en una estructura común distintos indicadores de Lectura para observar cómo han cambiado los resultados de Chile a lo largo de los ciclos disponibles.

La base final contiene información sobre puntaje promedio, estudiantes bajo el Nivel 2, estudiantes en el Nivel 5 o superior y medidas de dispersión. Estos indicadores permiten analizar no solamente el cambio del promedio nacional, sino también la evolución de distintos componentes de la distribución de los resultados.

## Proceso de limpieza y preparación de los datos

### 1. Revisión de las bases originales
El proceso comenzó con la revisión de los archivos originales de PISA y de las distintas tablas estadísticas incluidas en ellos. Debido a que los indicadores de interés no se encontraban necesariamente reunidos en una única tabla, fue necesario identificar cuáles contenían información histórica comparable para Chile.

Durante esta revisión se buscaron específicamente indicadores relacionados con el puntaje promedio de Lectura, los niveles de desempeño y la dispersión de los resultados.

Los archivos originales fueron conservados sin modificaciones dentro de la carpeta `datos_originales`, de modo que el proceso pueda ser revisado y los valores de la base final puedan rastrearse hasta su fuente.
### 2. Selección de tablas

Luego de revisar el archivo original se seleccionaron las tablas que contenían los indicadores necesarios para construir una serie histórica de Chile.

Se utilizaron tablas con información sobre el puntaje promedio de Lectura, la proporción de estudiantes ubicada en distintos niveles de desempeño y medidas de dispersión de los resultados.

El criterio de selección fue que los indicadores pudieran ser asociados a un ciclo determinado de PISA y que contribuyeran directamente a responder las preguntas de investigación. Las tablas que no aportaban información relevante para este análisis temporal no fueron incorporadas a la base final.
### 3. Selección de variables
Se seleccionaron seis variables para construir la base limpia: `anio`, `puntaje_lectura`, `bajo_nivel_2_pct`, `nivel_5_o_superior_pct`, `desviacion_estandar` y `rango_interdecil`.

La variable `anio` identifica el ciclo PISA correspondiente a cada observación. `puntaje_lectura` permite seguir la evolución del desempeño promedio de Chile.

Las variables `bajo_nivel_2_pct` y `nivel_5_o_superior_pct` permiten complementar el promedio observando cómo ha cambiado la proporción de estudiantes en los niveles bajos y altos de desempeño.

Finalmente, `desviacion_estandar` y `rango_interdecil` incorporan información sobre la dispersión de los resultados, permitiendo analizar si las diferencias entre los puntajes de los estudiantes se han modificado a través del tiempo.

Se excluyeron otros indicadores presentes en las tablas originales que no serían utilizados directamente en las visualizaciones previstas.

### 4. Reestructuración de los datos
Los indicadores seleccionados provenían de distintas secciones o tablas de los archivos originales. Para facilitar su análisis, fueron reorganizados en una única estructura tabular.

Se adoptó un formato en el que cada fila corresponde a un ciclo de PISA para Chile y cada columna representa uno de los indicadores seleccionados.

El año fue utilizado como identificador para relacionar los valores provenientes de las distintas tablas. De esta manera, los indicadores correspondientes a un mismo ciclo quedaron reunidos en una sola observación.

Esta reorganización permite analizar conjuntamente la evolución del puntaje promedio, los niveles de desempeño y la dispersión de los resultados.
### 5. Limpieza y estandarización
Durante el proceso de limpieza se eliminaron los elementos de las tablas originales que no correspondían a observaciones, como títulos, subtítulos, notas y encabezados adicionales.

Se conservaron exclusivamente las observaciones correspondientes a Chile y los ciclos para los cuales existían datos utilizables en las tablas seleccionadas.

Los nombres de las variables fueron estandarizados utilizando minúsculas y guiones bajos. Los indicadores fueron almacenados como valores numéricos y los porcentajes se conservaron en una escala de 0 a 100 sin incorporar el símbolo `%` en las celdas.

No se imputaron valores para los ciclos en los que la fuente no presentaba información disponible. Por esta razón, 2003 no fue incorporado a la serie final.

El resultado fue una estructura simplificada y preparada para ser utilizada directamente en herramientas de análisis y visualización.
### 6. Revisión de la base final
Una vez construida la base unificada se realizó una revisión de su estructura y contenido.

Se comprobó que cada fila correspondiera a un ciclo identificable de PISA, que cada columna tuviera un significado único y que las variables numéricas pudieran ser utilizadas directamente para realizar cálculos.

También se revisó que no existieran filas duplicadas ni celdas vacías dentro de las observaciones seleccionadas.

Finalmente, se verificó que la serie permitiera analizar la evolución histórica de Chile mediante los distintos indicadores seleccionados.
### 7. Exportación
Una vez finalizado el proceso de selección, integración, limpieza y revisión, la base fue exportada en formato CSV bajo el nombre `pisa_chile_evolucion_2000_2025_limpia.csv`.

Se eligió este formato por su compatibilidad con distintas herramientas de análisis y visualización y porque permite cargar directamente los datos mediante Pandas.

Los archivos originales no fueron reemplazados ni modificados y se conservaron por separado en la carpeta `datos_originales`.
## Fuentes utilizadas
La fuente utilizada corresponde al Programa para la Evaluación Internacional de los Estudiantes (PISA), desarrollado por la Organización para la Cooperación y el Desarrollo Económicos (OCDE).

Se escogieron los datos de PISA porque permiten observar la evolución del desempeño de estudiantes de 15 años utilizando indicadores construidos bajo un marco internacional común.

Para esta base se seleccionaron específicamente las observaciones históricas correspondientes a Chile. El objetivo fue construir una serie que permitiera estudiar la evolución del desempeño lector desde una perspectiva temporal, complementando las comparaciones internacionales desarrolladas en otras partes del proyecto.

Se conservaron los archivos originales como respaldo para mantener la trazabilidad entre las tablas de origen y la base limpia.
[pisa_chile_evolucion_2000_2025_limpia (1).csv](https://github.com/user-attachments/files/32880326/pisa_chile_evolucion_2000_2025_limpia.1.csv)

## Decisiones metodológicas y editoriales
La principal decisión metodológica fue concentrar esta base exclusivamente en Chile y ampliar el período temporal de análisis. Esto permite diferenciar este trabajo de otras bases del proyecto centradas en la comparación internacional o en ciclos específicos.

También se decidió complementar el puntaje promedio con indicadores sobre los niveles de desempeño y la dispersión de los resultados. Esta decisión permite evitar que la evolución histórica sea representada únicamente mediante un promedio nacional.

No se incorporaron valores para ciclos en los que la fuente no presentaba información disponible. En particular, no se imputó un resultado para 2003, ya que hacerlo habría implicado crear un dato no observado.

Desde el punto de vista editorial, los resultados de PISA se utilizarán específicamente para describir el desempeño de estudiantes de 15 años evaluados por el programa. Por lo tanto, no se presentarán como una medición directa de la comprensión lectora de todos los niños chilenos.

Finalmente, las variaciones observadas entre ciclos serán tratadas como cambios descriptivos. La base permite identificar cuándo los indicadores aumentan o disminuyen, pero no permite establecer por sí sola las causas de esas variaciones.


## Preguntas que permite responder la base
1. **¿Cómo ha evolucionado el puntaje promedio de Chile en Lectura a lo largo de los distintos ciclos de PISA?**

   La variable `puntaje_lectura` permite comparar los resultados de los diferentes ciclos disponibles e identificar períodos de aumento o disminución.

2. **¿Cómo ha cambiado la proporción de estudiantes chilenos bajo el Nivel 2 de desempeño en Lectura?**

   La variable `bajo_nivel_2_pct` permite observar la evolución del porcentaje de estudiantes ubicado en los niveles más bajos de desempeño.

3. **¿Cómo ha evolucionado la proporción de estudiantes chilenos que alcanza el Nivel 5 o superior?**

   La variable `nivel_5_o_superior_pct` permite observar los cambios en la proporción de estudiantes ubicada en los niveles altos de desempeño.

4. **¿Cómo ha cambiado la dispersión de los resultados de Lectura en Chile a través de los ciclos de PISA?**

   Las variables `desviacion_estandar` y `rango_interdecil` permiten analizar si la distribución de los puntajes se ha vuelto más o menos dispersa a través del tiempo.

   ## Posibles usos para la visualización

La estructura temporal de la base permite desarrollar visualizaciones destinadas a mostrar la evolución del desempeño lector de Chile.

Una primera visualización puede utilizar una línea de tiempo para representar el puntaje promedio de Lectura en cada ciclo disponible. Esto permitiría identificar períodos de aumento, estabilidad o disminución y situar los resultados recientes dentro de una trayectoria más extensa.

Una segunda visualización puede mostrar la evolución del porcentaje de estudiantes bajo el Nivel 2 y del porcentaje ubicado en el Nivel 5 o superior. Esto permitiría complementar el promedio nacional observando cómo han cambiado los extremos del desempeño.

Finalmente, las variables de dispersión pueden utilizarse para explorar cómo ha variado la distancia entre los resultados de los estudiantes a través del tiempo.

Estas visualizaciones complementarían la comparación internacional realizada por otros integrantes del proyecto, permitiendo que la webstory avance desde la trayectoria histórica de Chile hacia su situación reciente y su posición frente a otros países.

