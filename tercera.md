# Tercera sesión, montaje experimental

## Objetivos

* Coordinar todo lo aprendido en la creación de un algoritmo genético completo
* Entender el concepto de montaje experimental y aplicarlo en la práctica

## Introducción

Última sesión del curso. Para aprobar la asignatura habrá que [entregar un algoritmo genético completo siguiendo estas instrucciones](final.md).

En esta última sesión se trata de agrupar todo lo que hay en una sola
librería que se use desde diferentes aplicaciones.

## Desarrollo basado en test

El desarrollo basado en test incluye escribir el test para cada
función antes que la propia función. Se deben usar test completos pero
un test sólo es mejor que ninguno.

### Ejercicio

Informarse sobre las librerías y capacidades de test del lenguaje de
programación usado y programar tests para los operadores programados
anteriormente. Los test deberán seguir las prácticas habituales en el
lenguaje de programación usado

### Integración continua

La [integración continua](http://es.wikipedia.org/wiki/Integraci%C3%B3n_continua) consiste en la creación de una serie de
tests automáticos que se pasan a la hora de hacer un cambio en el
repositorio. GitHub está preparado para pasarlos cuando se hace un
*push* en sitios como [Travis](http://travis-ci.org) o usando software
tal como Jenkins. 

Con los tests programados, sólo hace falta un fichero de configuración
(en JSON, YAML o XML) para que el sitio que haya configurado desde
GitHub haga la integración continua. El fichero de configuración
estará bajo control de versiones, pero
[en el propio sitio](http://docs.travis-ci.com/) se explica como
configurarlo para un lenguaje de programación determinado.

### Ejercicio

Echar a andar la integración continua para el repositorio de código
del algoritmo genético.

## Un algoritmo genético completo

Un algoritmo canónico incluye

1. Generación inicial de la población
2. Bucle:
   1. Evaluación.
   2. Selección para la reproducción
   3. Generación de la nueva población por aplicación de los
   operadores genéticos
   
Todo ello, en Perl, se ve en
[a Perl primer for EA practitioners](http://www.slideshare.net/pierluca.lanzi/sigevolution-volume-4-issue-4). Un
[algoritmo genético canónico](http://geneura.ugr.es/~jmerelo/evolutionary-computation-perl/x207.html)
incluye todos esos componentes, con unos valores fijos para
representación, selección y operadores usados. 

### Condición de terminación del bucle

El bucle termina cuando 
1. Se encuentra la solución (si se conoce)
2. Se ha ejecutado un número determinado de generaciones
3. Número determinado de generaciones sin cambio.

### Ejercicio

Hacer una versión inicial del algoritmo genético completo aplicado a
una función de fitness ya programada como ONE_MAX.

## Diseño experimental

Generalmente en un trabajo se van a ejecutar decenas o miles de veces
un algoritmo para obtener resultados. Para ello, es necesario

* Ejecutar *siempre* con ficheros de configuración, *nunca* cambiado
  parámetros en el programa
* Llevar un *diario de laboratorio* donde se apunten los experimentos,
  parámetros, si ha habido algún cambio de condiciones, resultados
  positivos o negativos, lo que haga falta. La mayor parte de los
  editores permiten llevarlo fácilmente insertando fecha y autor. 
* Emitir los resultados en un *formato estructurado*. (Más información
  sobre esto maś abajo).
* ¡Ciencia abierta!

### Ejercicio

Modificar el programa inicial para trabajar con un fichero de configuración.

### Resultados experimentales

Conviene seguir las siguientes reglas

* Generar automáticamente los nombres de los ficheros de salida. Por
  ejemplo,
  `prefijo_experimento-parametros_de_entrada-numero_unico-numero_de_serie.extension`. Por
  ejemplo, `evostar2014-p1000-m01-080033-1.csv`  donde el prefijo es
  un nombre de congreso, se escogen parte de los parámetros (población
  y mutación, que serán los que se varíen, la hora que se inserta
  automáticamente y un número de serie en caso de que se haga todo en
  el mismo segundo (puede suceder en experimentos paralelos).
* Usad formatos estructurados para almacenar los resultados: 
  [JSON](http://www.json.org/), [YAML](http://yaml.org) o XML. Estos
  resultados incluirán tiempos y todo el fichero de configuración
  completo. Estos resultados son legibles y además guardan información
  sobrela estructura de datos real. *No* usar CSV ni texto.
* Crear un programa que procese los resultados y genere directamente
  tablas en LaTeX o programas para presentarlos en R. Te ahorrará un
  montón de tiempo a la hora de trabajar con ellos.
 * Por simplicidad, usar el mismo formato que para los ficheros de
   configuración. El formato INI está bien para ellos, pero no para
   resultados (aunque también se puede usar).
   
 ###  Ejercicio
 
 Integrar la emisión de resultados en este formato en el programa que
 implementa el algoritmo genético
 
 ## Consideraciones finales
 
 * Considerad buenas prácticas en el desarrollo de software: uso
   intensivo de git, desarrollo basado en test, integración continua. 
 * Mantente al tanto de los últimos avances en el lenguaje de
   programación/entorno/estilo de programación que uses
 * Planifica el mantenimiento futuro de la librería/aplicación con la
   que trabajes.
 * Ábrete a la colaboración. Incluye siempre el URL de la librería con
   el trabajo que publiques.
   
 A partir de aquí, [te queda entregar el trabajo final](final.md).



