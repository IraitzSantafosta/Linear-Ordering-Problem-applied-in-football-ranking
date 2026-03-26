# Linear-Ordering-Problem-applied-in-football-ranking

Optimización de un ranking histórico de selecciones de fútbol

Este estudio analiza cómo construir un ranking internacional de fútbol más preciso utilizando datos históricos desde 1872 hasta 2021. Para ello, se seleccionaron las 25 selecciones nacionales con mayor número de partidos disputados y se aplicaron técnicas matemáticas y de inteligencia artificial.

1. Preparación de los datos

El primer paso consistió en transformar los resultados históricos de los partidos en una estructura que permitiera comparar equipos entre sí.

En lugar de contar simplemente victorias y derrotas, se introdujeron varios factores para mejorar la calidad del análisis:

Importancia de los goles: No es lo mismo ganar 1-0 que 6-0, pero tampoco se quiere que goleadas extremas distorsionen el resultado. Por eso se utilizó una escala logarítmica para suavizar estas diferencias.
Importancia del tiempo: Los partidos más recientes tienen más peso que los antiguos. Esto se logró dando mayor valor a los encuentros más cercanos al año 2021.
Condiciones del partido: Se tuvo en cuenta si el equipo jugaba en casa o fuera.
Tipo de competición: No todos los torneos son igual de importantes, así que se clasificaron en distintos niveles de prestigio.
Penaltis: En caso de empate, se añadió un pequeño extra al equipo ganador en la tanda.

Con todo esto se construyó una matriz que resume cuántas veces y con qué “fuerza” un equipo ha sido mejor que otro.

2. Cómo se define el problema

El objetivo es ordenar los 25 equipos de manera que el ranking final refleje lo mejor posible los resultados históricos.

Para ello:

Cada posible ranking es simplemente un orden diferente de los equipos.
Existen millones de posibles combinaciones.
Se define una función que mide qué tan bueno es un ranking.

Esta función da más importancia a acertar las posiciones altas (por ejemplo, quién es el mejor equipo del ranking) que las posiciones bajas. Es decir, equivocarse en el top 3 penaliza más que equivocarse en el puesto 20.

3. Métodos utilizados para encontrar el mejor ranking

Se probaron tres estrategias distintas:

A. Método rápido (Greedy)

Este método calcula una puntuación para cada equipo:

Suma todo lo bueno que ha hecho (rendimiento total).
Resta todo lo que ha sufrido contra otros equipos.

Después, ordena los equipos según esta puntuación.

✔ Ventaja: muy rápido
✖ Desventaja: no siempre encuentra la mejor solución posible

B. Recocido simulado (Simulated Annealing)

Este método se inspira en procesos físicos como el enfriamiento de metales.

Empieza con un ranking aleatorio.
Va haciendo pequeños cambios (intercambia dos equipos).
Si el cambio mejora el ranking, se acepta.
Si lo empeora, a veces también se acepta para evitar quedarse atrapado en soluciones malas.

Al principio explora mucho (acepta más errores), y poco a poco se vuelve más exigente.

✔ Ventaja: encuentra soluciones bastante buenas
✖ Desventaja: requiere más tiempo de cálculo

C. Algoritmo evolutivo (EDA)

Este es el método más avanzado.

Genera muchos rankings aleatorios (como una población).
Selecciona los mejores.
Aprende patrones: por ejemplo, si un equipo suele aparecer arriba en los mejores rankings.
Usa esas probabilidades para crear nuevas soluciones.
Introduce pequeñas variaciones para seguir explorando.

Es similar a cómo evolucionan las especies: selección, aprendizaje y variación.

✔ Ventaja: encuentra las mejores soluciones
✖ Desventaja: es el más costoso en tiempo y recursos

4. Resultados y conclusiones

Los resultados mostraron diferencias claras:

El método evolutivo (EDA) fue el mejor, logrando la puntuación más alta.
El recocido simulado también obtuvo buenos resultados, aunque algo inferiores.
El método rápido (Greedy) fue el menos preciso, pero el más eficiente.

Además:

El método Greedy y el recocido simulado tienden a encontrar soluciones parecidas.
El algoritmo evolutivo explora soluciones muy diferentes, lo que le permite encontrar mejores resultados.

Conclusión final

Rendimiento de la Función Objetivo (Fitness): El algoritmo evolutivo EDA demostró ser el más efectivo al obtener el valor de maximización más alto (23244.77), superando al Recocido Simulado (23011.54) y al Greedy (21262.83)
. Esto prueba que el modelado probabilístico por poblaciones es muy apto para el problema LOP en este contexto

Costes Computacionales y Similitud: Aunque el EDA logra la mejor optimización, demanda muchos más recursos computacionales y tiempo de ejecución que los otros dos
. Además, el análisis de similitud demostró que el Greedy y el Recocido Simulado convergen hacia regiones similares del espacio de búsqueda (similitud de 0.24), mientras que el EDA explora áreas significativamente distintas (similitud de solo 0.079 con el Recocido Simulado)
