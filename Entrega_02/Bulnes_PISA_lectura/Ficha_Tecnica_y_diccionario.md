# Ficha técnica y diccionario de datos

## Ficha técnica

### Fuente de los datos
Los datos utilizados provienen del Programa para la Evaluación Internacional de los Estudiantes (PISA, por sus siglas en inglés), desarrollado por la Organización para la Cooperación y el Desarrollo Económicos (OCDE).

Para esta base se utilizaron los resultados de lectura correspondientes a PISA 2022 y PISA 2025, obtenidos a partir de las tablas de resultados publicadas por la OCDE. PISA evalúa a estudiantes de 15 años de distintos países y economías. En la edición 2025 participaron 91 países y economías y más de 760.000 estudiantes. En este ciclo, ciencias fue el dominio principal de evaluación, mientras que lectura y matemáticas fueron dominios secundarios.

La fuente principal utilizada para construir esta base corresponde a las tablas del informe *PISA 2025 Results (Volume I): Future-Ready Students*, publicado por la OCDE en septiembre de 2026. De estas tablas se seleccionaron los indicadores relacionados con desempeño en lectura y su evolución temporal.

Fuentes oficiales:

- OECD (2026), *PISA 2025 Results (Volume I): Future-Ready Students*. OECD Publishing. (https://www.oecd.org/en/publications/pisa-2025-results-volume-i_73451bc5-en.html)
- Base de datos oficial PISA 2025, OECD. (https://www.oecd.org/en/data/datasets/pisa-2025-database.html) 

### Metodología de construcción de la base
La base de datos limpia fue construida a partir de las tablas originales de resultados de PISA 2025 publicadas por la OCDE. El archivo original contenía numerosas tablas correspondientes a distintas dimensiones y áreas evaluadas por PISA, por lo que primero se realizó una selección de aquellas relacionadas específicamente con el desempeño en lectura.

De las tablas disponibles se identificaron cinco como potencialmente útiles para la investigación: puntaje promedio y variación en lectura (Table I.B1.2a.2), distribución de estudiantes según niveles de desempeño (Table I.B1.2a.11), evolución de estudiantes de bajo y alto desempeño (Table I.B1.2a.34), evolución del puntaje promedio en lectura (Table I.B1.2a.37) y variación del desempeño en lectura a través del tiempo (Table I.B1.2a.43).

Posteriormente, se seleccionaron las variables necesarias para responder las preguntas de investigación. La base final conserva el país o economía, el año de medición, el puntaje promedio en lectura, el porcentaje de estudiantes bajo el Nivel 2 de desempeño y el porcentaje de estudiantes ubicados en el Nivel 5 o superior.

Los datos fueron reorganizados en formato tabular, de manera que cada fila representa la observación de un país o economía en un determinado año y cada columna corresponde a una variable. Se eliminaron de la base final los títulos, subtítulos, notas al pie, filas vacías y otras columnas de las tablas originales que no eran necesarias para el análisis propuesto.

Finalmente, se revisó la estructura de las variables y la presencia de datos faltantes. La base resultante fue exportada en formato CSV bajo el nombre `pisa_lectura_limpia.csv`, con el objetivo de facilitar su posterior análisis mediante Pandas y su utilización en herramientas de visualización de datos.

### Alcance de los datos
La base reúne información sobre desempeño en lectura de estudiantes de 15 años evaluados por PISA. Su unidad de análisis corresponde a un país o economía participante en un determinado año de evaluación.

Para el análisis temporal de Chile, la base permite comparar los resultados de PISA 2022 y PISA 2025. Para el análisis internacional, permite situar los resultados de Chile frente a los demás países y economías incluidos en los datos seleccionados de PISA 2025.

Los principales indicadores considerados son el puntaje promedio en lectura, el porcentaje de estudiantes que se encuentra bajo el Nivel 2 de desempeño y el porcentaje de estudiantes que alcanza el Nivel 5 o superior.

El alcance de la base es comparativo y descriptivo. Los datos permiten observar diferencias entre años y entre países o economías, pero no permiten por sí solos establecer las causas de esas diferencias.

Además, los resultados no deben interpretarse como una medición de todos los niños, adolescentes o estudiantes de Chile, ya que PISA trabaja específicamente con una muestra representativa de estudiantes de 15 años que cumplen los criterios definidos por la evaluación.

### Características de los datos
La base limpia está almacenada en formato CSV y presenta una estructura tabular o "tidy", diseñada para facilitar su análisis y visualización. Cada fila corresponde a una observación de un país o economía en un determinado año y cada columna representa una variable.

La base contiene cinco variables: `pais_economia`, `anio`, `puntaje_lectura`, `bajo_nivel_2_pct` y `nivel_5_o_superior_pct`.

Las variables asociadas a puntajes y porcentajes fueron almacenadas como datos numéricos, mientras que el nombre del país o economía corresponde a una variable de texto y el año a una variable numérica entera.

La estructura permite filtrar los datos por país y año, comparar indicadores entre distintas observaciones y utilizar directamente la información en herramientas de análisis como Pandas y en programas de visualización de datos.

En la construcción de la base se buscó mantener nombres de variables breves, descriptivos y consistentes. Los porcentajes se expresan en una escala de 0 a 100; por ejemplo, un valor de 38,18 en `bajo_nivel_2_pct` representa un 38,18 % de los estudiantes de la observación correspondiente.

### Observaciones
Los resultados deben interpretarse considerando la metodología propia de PISA. La evaluación se realiza sobre una muestra de estudiantes de 15 años y, por lo tanto, los resultados no representan directamente a todos los estudiantes ni a todos los niños de cada país.

El indicador `bajo_nivel_2_pct` corresponde al porcentaje de estudiantes cuyo desempeño se encuentra por debajo del Nivel 2 de competencia en lectura según la clasificación utilizada por PISA. Por su parte, `nivel_5_o_superior_pct` identifica la proporción de estudiantes que alcanza los niveles superiores de desempeño (Nivel 5 o Nivel 6).

Para la comparación entre PISA 2022 y PISA 2025 se mantienen los valores numéricos originales disponibles en las tablas seleccionadas. Las diferencias entre ambos años pueden calcularse a partir de estos valores, pero no deben interpretarse por sí solas como evidencia de una causa específica.

La base fue construida con fines de análisis periodístico y visualización. Por esta razón, se conservaron únicamente las variables pertinentes para las preguntas de investigación del proyecto y no la totalidad de los indicadores disponibles en las bases originales de PISA.

Los nombres de países o economías se conservaron de manera consistente para permitir su filtrado y comparación. Los archivos originales utilizados durante el proceso se mantienen en la carpeta `datos_originales` para garantizar la trazabilidad de la información.

## Diccionario de datos
| Variable | Descripción | Tipo de dato | Valores posibles | Observaciones editoriales |
|---|---|---|---|---|
| `pais_economia` | Nombre del país o economía al que corresponde la observación. | Texto (`string`) | Países y economías presentes en la base seleccionada de PISA. | Se utiliza como identificador geográfico para realizar comparaciones internacionales. |
| `anio` | Año correspondiente al ciclo de evaluación PISA de la observación. | Número entero (`integer`) | 2022, 2025 | Permite realizar comparaciones temporales, particularmente entre los resultados de Chile en ambos ciclos. |
| `puntaje_lectura` | Puntaje promedio obtenido en lectura por los estudiantes de 15 años de cada país o economía en el ciclo correspondiente. | Número decimal (`float`) | Valores numéricos de la escala PISA de lectura. | Un puntaje mayor representa un mayor desempeño promedio en la evaluación de lectura. No corresponde a un porcentaje. |
| `bajo_nivel_2_pct` | Porcentaje de estudiantes cuyo desempeño en lectura se encuentra por debajo del Nivel 2 de competencia de PISA. | Número decimal (`float`) | 0 a 100 | Se expresa como porcentaje. Un valor mayor indica una mayor proporción de estudiantes bajo este nivel de desempeño. |
| `nivel_5_o_superior_pct` | Porcentaje de estudiantes que alcanza el Nivel 5 o Nivel 6 de desempeño en lectura. | Número decimal (`float`) | 0 a 100 | Se expresa como porcentaje y permite identificar la proporción de estudiantes ubicada en los niveles superiores de desempeño. |
