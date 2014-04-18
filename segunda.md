# Segunda sesión, implementación de algoritmos evolutivos

Primera sesión de la [asignatura de implementación de algoritmos evolutivos](README.md), día 10 de abril de 2014.

## Objetivos

* Entender cómo se temporizan los algoritmos evolutivos (y cualquier programa científico)
* Entender las estructuras de datos básicas de algoritmos evolutivos.
* Entender mecanismos básicos de optimización.

## Temporización de algoritmos

Para temporizar un algoritmo es necesario
* Repetir la ejecución varias veces
* Asegurarse de que siempre se hace en las mismas condiciones. Si no, repetir.
* Entender la diferencia entre tiempo *de reloj* y tiempo *del sistema*
* Analizar estadísticamente los resultados

### Ejercicio

¿Qué mecanismo usas o usarías para temporizar un algoritmo? Discute en [este *issue* del proyecto de la asignatura](https://github.com/JJ/implementacion-eas/issues/13) 

## El cromosoma

El [algoritmo genético canónico](http://geneura.ugr.es/~jmerelo/evolutionary-computation-perl/x207.html) incluye un cromosoma compuesto por una cadena binaria. Ese cromosoma se decodifica a una serie de parámetros, que estarán representados con un número de bits forzosamente finito.

### Ejercicio

Implementa un vector de bits o cadena binaria. En la documentación del mismo, argumenta la estructura de datos que usas. Prueba diferentes estructuras de datos y aplica alguna operación sobre ellos (por ejemplo, generación inicial) para ver cuál ofrece mejores prestaciones.

* [Ejercicio de Paloma, en Perl] (https://github.com/unintendedbear/unintendedbear-eas/blob/master/EA_Paloma.pl), [Documentación] (https://github.com/unintendedbear/unintendedbear-eas/blob/master/SegundaSesi%C3%B3n.md)
* [Ejercicio de Juanjo, en C++] (https://github.com/rotty11/MiRepositorio/blob/master/ev_crom.cpp), [Documentación] (https://github.com/rotty11/MiRepositorio/blob/master/ev_crom_explicacion.md), [Mediciones] (https://github.com/rotty11/MiRepositorio/blob/master/ev_crom_tiempos.txt)

## Fitness

El fitness es usualmente uno de los elementos críticos de un algoritmo evolutivo. Conviene usar todas las técnicas de implementación que se conozcan para hacerlo lo más rápido posible. 

Como benchmark de algoritmos evolutivos se suele usar MAX-ONES o COUNT-ONES, que cuenta el número de unos de una cadena. Otras funciones que se usan habitualmente son [Royal Road](http://web.cecs.pdx.edu/~mm/ecal92.pdf) y [MMDP](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.48.8442&rep=rep1&type=pdf).

### Ejercicio

Implementar esta función. Medir tiempos para diferentes tamaños de cadena, 128, 256, 1024. ¿Cómo se incrementa el tiempo necesario para calcularlo con el tamaño? ¿Es lineal? Usar la técnica descrita anteriormente para llevar a cabo la medición. Finalmente, si una vez implementado se descubre una forma mejor de hacerlo (por ejemplo, la de un compañero) volver a implementarlo y hacer una medición.

* [Ejercicio de Juanjo, en C++] (https://github.com/rotty11/MiRepositorio/blob/master/ev_fitness.cpp), [Documentación] (https://github.com/rotty11/MiRepositorio/blob/master/ev_fitness_explicacion.md), [Mediciones] (https://github.com/rotty11/MiRepositorio/blob/master/ev_fitness_tiempos.txt)

## Mutación y crossover

Un operador de mutación cambia un bit (o más) en una cadena de bits. El crossover intercambia una parte de la cadena entre dos cadenas, es un *swap* de los bits entre dos puntos de la cadena aleatorios.

### Ejercicios

¿Puedes hacer un operador de mutación y otro de crossover? ¿Es adecuada la implementación que elegiste antes?

## Selección

En el [algoritmo genético canónico](http://geneura.ugr.es/~jmerelo/evolutionary-computation-perl/x207.html), la selección está basada en rueda de ruleta. En todo caso, la selección se basa en el principio de que aquellos con más fitness deben reproducirse más que los que tengan un fitness inferior. Para ello hay habitualmente varias fases

* Selección: se seleccionan aquellos que se vayan a reproducir y se sacan tantas copias como sea necesario; el número de copias debe ser proporcional al fitness. Se upede usar rueda de ruleta o bien torneo: se van tomando los individuos de la población de n en n y se escoge el mejor para pasar al *pool* reproductivo. 
* Reproducción: en el algoritmo genético canónico, se toman pares de cromosomas, se lleva a cabo entrecruzamiento y posteriormente se aplica mutación a los dos
* Inserción: se insertan los nuevos individuos en la población, sustituyendo la población anterior, seleccionando los (tamaño de población) mejores o si la población tiene tamaño `n`, se toman los 1 o 2 individuos mejores y se sustituye totalmente el resto.

### Ejercicio

Añadir un procedimiento de selección al algoritmo genético, rueda de ruleta o torneo, y ejecutar un algoritmo genético completo sobre alguna de las funciones de fitness usadas. Comprobar el efecto de diferentes parámetros: tamaño de población, por ejemplo. Comprobar también el tiempo necesario para resolver problemas de diferente tamaño 

## Ejercicios de los alumnos

Añadid, tras hacer un pull de este repositorio y debajo de cada ejercicio, un enlace a vuestro ejercicio y luego a continuación un pull request. Los ejercicios los puedes publicar tanto en un repositorio como en un [Gist (para los que incluyan un solo script)](http://gist.github.com).
