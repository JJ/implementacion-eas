# Tercera sesión, montaje experimental

## Objetivos

* Coordinar todo lo aprendido en la creación de un algoritmo genético completo
* Entender el concepto de montaje experimental y aplicarlo en la práctica

## Introducción

Última sesión del curso. Para aprobar la asignatura habrá que [entregar un algoritmo genético completo siguiendo estas instrucciones](final.md).

En esta última sesión se trata de agrupar todo lo que hay en una sola librería que se use desde diferentes aplicaciones.

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



