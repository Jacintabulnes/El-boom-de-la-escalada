# Ficha técnica — Evolución histórica de Chile en PISA Lectura

## Fuente de los datos
Los datos utilizados para la construcción de esta base provienen del Programa para la Evaluación Internacional de los Estudiantes (PISA), desarrollado por la Organización para la Cooperación y el Desarrollo Económicos (OCDE).

Se utilizaron las tablas estadísticas disponibles en los archivos originales de PISA que contienen resultados históricos de Chile en Lectura. A partir de estas tablas se seleccionaron indicadores de desempeño promedio, niveles de desempeño y medidas de dispersión para los distintos ciclos disponibles.

Se escogió PISA porque utiliza una metodología internacional que permite observar la evolución del desempeño de estudiantes de 15 años a través del tiempo. Para esta base se trabajó exclusivamente con las observaciones correspondientes a Chile.

Los archivos originales fueron conservados sin modificaciones dentro de la carpeta `datos_originales`, de manera que los valores utilizados en la base limpia puedan rastrearse hasta su fuente.
[mrq53f.xlsx](https://github.com/user-attachments/files/32880166/mrq53f.xlsx)


## Metodología de construcción de la base
La base fue construida a partir de distintas tablas estadísticas de PISA que contienen información histórica sobre el desempeño de Chile en Lectura.

Primero se identificaron las tablas que permitían observar la evolución del puntaje promedio de Chile, la proporción de estudiantes ubicada bajo el Nivel 2, la proporción de estudiantes en el Nivel 5 o superior y medidas relacionadas con la dispersión de los resultados.

Posteriormente se seleccionaron únicamente las observaciones correspondientes a Chile y se integraron los indicadores en una estructura común utilizando el año del ciclo PISA como variable de unión.

Se eliminaron títulos, encabezados adicionales, notas y variables estadísticas que no serían utilizadas directamente en el análisis. Los nombres de las variables fueron estandarizados utilizando minúsculas y guiones bajos.

La base final fue revisada para comprobar la consistencia de los datos y posteriormente fue exportada en formato CSV.
## Alcance de los datos
La base reúne resultados históricos de Chile en la evaluación de Lectura de PISA para los ciclos disponibles seleccionados entre 2000 y 2025.

Cada fila representa un ciclo de PISA para Chile y contiene distintos indicadores asociados al desempeño lector de los estudiantes evaluados.

La base incluye información para los ciclos 2000, 2006, 2009, 2012, 2015, 2018, 2022 y 2025. El ciclo 2003 no fue incorporado debido a que las tablas utilizadas no presentan un valor disponible para Chile.

El alcance de la base es descriptivo y temporal. Permite observar cómo han cambiado los indicadores de desempeño lector de Chile entre distintos ciclos, pero no permite determinar por sí sola las causas de esos cambios.

PISA evalúa a estudiantes de 15 años, por lo que los resultados no deben interpretarse como una medición de la comprensión lectora de todos los niños o estudiantes chilenos.
## Características de los datos
## Características de los datos

La base limpia contiene ocho observaciones y seis variables. Cada fila corresponde a un ciclo de PISA para Chile y cada columna representa un indicador.

La variable `anio` permite ordenar cronológicamente las observaciones. Las demás variables son numéricas y permiten analizar distintos aspectos del desempeño lector.

Los porcentajes se almacenaron como valores numéricos en una escala de 0 a 100 y sin incorporar el símbolo `%` dentro de las celdas.

Los nombres de las variables fueron estandarizados utilizando minúsculas y guiones bajos para facilitar su utilización mediante herramientas de análisis como Pandas.

La estructura final permite realizar comparaciones entre ciclos, calcular variaciones y construir visualizaciones sobre la evolución histórica del desempeño lector de Chile.
## Otras observaciones
## Otras observaciones

La serie no debe interpretarse como una medición anual, ya que PISA se realiza por ciclos y los intervalos entre las observaciones no son siempre iguales.

La ausencia de un registro para 2003 responde a la falta de un valor disponible para Chile en las tablas utilizadas, por lo que no se incorporó ni se imputó un dato artificial.

El registro asociado a PISA 2000 debe interpretarse considerando la participación de Chile en PISA 2000+, cuya aplicación para el país se realizó posteriormente al ciclo principal.

Las variaciones entre ciclos permiten describir cambios en los indicadores, pero no permiten establecer relaciones causales. Para explicar las razones detrás de los cambios sería necesario complementar estos resultados con otras fuentes, estudios y entrevistas.

## Diccionario de datos
| Variable | Descripción | Tipo de dato | Valores posibles | Observaciones editoriales |
|---|---|---|---|---|
| `anio` | Ciclo PISA correspondiente a la observación. | Entero | 2000, 2006, 2009, 2012, 2015, 2018, 2022, 2025 | Se utiliza para ordenar temporalmente los resultados. |
| `puntaje_lectura` | Puntaje promedio obtenido por Chile en Lectura. | Decimal | Valores numéricos de la escala PISA | Permite observar la evolución del desempeño promedio. |
| `bajo_nivel_2_pct` | Porcentaje de estudiantes que se encuentra bajo el Nivel 2 de desempeño en Lectura. | Decimal | 0–100 | Permite observar la evolución del bajo desempeño. |
| `nivel_5_o_superior_pct` | Porcentaje de estudiantes ubicado en el Nivel 5 o superior de desempeño en Lectura. | Decimal | 0–100 | Permite observar la evolución del alto desempeño. |
| `desviacion_estandar` | Medida de dispersión de los puntajes de Lectura respecto del promedio. | Decimal | Valores numéricos positivos | Un valor mayor indica una mayor dispersión de los puntajes. |
| `rango_interdecil` | Diferencia entre los extremos definidos por los deciles utilizados en la tabla de origen. | Decimal | Valores numéricos positivos | Permite complementar el análisis de la dispersión de resultados. |
