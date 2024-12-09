# Ejercicio Técnico Buk

## Enunciado del Problema

La compañía X aplica una prueba de selección para contratar/descartar a los postulantes de una vacante. 
Dicha prueba consta de 8 preguntas de verdadero/falso. Para aprobar se necesitan 6 o más respuestas correctas.

Desafortunadamente, el reclutador de la compañía perdió el registro de respuestas correctas (facepalm), 
por lo que no sabemos cual es la respuesta correcta de cada pregunta. Ante esta delicada situación 
(ya los postulantes han respondido las pruebas), el equipo de reclutamiento decidió que para cada pregunta, 
se consideraría como correcta aquella respuesta más común entre los postulantes (si llegase a haber empate, 
se considera que la respuesta es "Si"). 

Por ejemplo, si en la pregunta 1, 20 postulantes contestaron “Si”, y 10 postulantes contestaron “NO”, entonces 
consideramos “Si” como la respuesta correcta.

Dado N el número de postulantes.
El input consta de N líneas donde cada línea representa las respuestas de un postulante a cada pregunta (1 para “Si”, 
0 para “No”). El dígito en la posición i representa la respuesta que dió el postulante para la pregunta i:

[1, 0, 1, 0, 1, 1, 1, 0] -> (Contestó Si en la pregunta 1, No en la pregunta 2, Si en la pregunta 3...)
[0, 0, 1, 1, 0, 0, 0, 1] -> (Contestó No en la pregunta 1, No en la pregunta 2, Si en la pregunta 3...)
etc...

Caso de ejemplo:
```
respuestas = [
    [0, 1, 0, 0, 1, 0, 1, 0],
    [0, 1, 1, 0, 0, 1, 1, 0],
    [0, 1, 1, 1, 1, 1, 0, 0],
    [1, 1, 0, 1, 0, 1, 0, 0],
    [1, 1, 0, 1, 1, 1, 0, 0],
    [1, 0, 0, 0, 0, 1, 0, 0],
    [0, 1, 0, 0, 1, 0, 1, 1],
    [1, 0, 0, 0, 0, 0, 0, 1],
    [1, 0, 0, 0, 1, 1, 1, 0],
    [1, 0, 1, 0, 0, 0, 0, 1],
]
```

Corrida en frío:
Para la pregunta 1: 6 postulantes contestaron SÍ, 4 postulantes contestaron NO. Por lo tanto la respuesta correcta es “SI”.

Para la pregunta 2: 6 postulantes contestaron SÍ, 4 postulantes contestaron NO. Por lo tanto la respuesta correcta es “SI”.

Para la pregunta 3: 3 postulantes contestaron SÍ, 7 postulantes contestaron NO. Por lo tanto la respuesta correcta es “NO”.

Para la pregunta 4: 3 postulantes contestaron SÍ, 7 postulantes contestaron NO. Por lo tanto la respuesta correcta es “NO”.

Para la pregunta 5: 5 postulantes contestaron SÍ, 5 postulantes contestaron NO. Por lo tanto la respuesta correcta es “SI”.

Para la pregunta 6: 6 postulantes contestaron SÍ, 4 postulantes contestaron NO. Por lo tanto la respuesta correcta es “SI”.

Para la pregunta 7: 4 postulantes contestaron SÍ, 6 postulantes contestaron NO. Por lo tanto la respuesta correcta es “NO”.

Para la pregunta 8: 3 postulantes contestaron SÍ, 7 postulantes contestaron NO. Por lo tanto la respuesta correcta es “NO”.

Pauta de Corrección según nuestro algoritmo:
```
[1, 1, 0, 0, 1, 1, 0, 0]
```

Siguiendo nuestra pauta, sabemos entonces que para cada postulante:
0 1 0 0 1 0 1 0 -> obtuvo 5 respuestas correctas
0 1 1 0 0 1 1 0 -> obtuvo 4 respuestas correctas
0 1 1 1 1 1 0 0 -> obtuvo 5 respuestas correctas
1 1 0 1 0 1 0 0 -> obtuvo 6 respuestas correctas
1 1 0 1 1 1 0 0 -> obtuvo 7 respuestas correctas
1 0 0 0 0 1 0 0 -> obtuvo 6 respuestas correctas
0 1 0 0 1 0 1 1 -> obtuvo 4 respuestas correctas
1 0 0 0 0 0 0 1 -> obtuvo 4 respuestas correctas
1 0 0 0 1 1 1 0 -> obtuvo 6 respuestas correctas
1 0 1 0 0 0 0 1 -> obtuvo 3 respuestas correctas


Output Esperado: 
```
Los siguientes postulantes aprobaron la prueba:
Postulante 4 con 6 respuestas correctas, 
Postulante 5 con 7 respuestas correctas, 
Postulante 6 con 6 respuestas correctas, 
Postulante 9 con 6 respuestas correctas,

En total, 4 postulantes pasaron la prueba.
```

## Ejercicios y ejecución:

1. Realice la implementación de este algoritmo en código. Como input recibirá un arreglo de respuestas. Cada respuesta será
a su vez un arreglo de 0s y 1s que describe la respuesta del postulante. Como output, se debe entregar que postulantes
pasaron la prueba, con cuantas respuestas correctas, y el total de postulantes aprobados.

```
input = [
    [0, 1, 0, 0, 1, 0, 1, 0],
    [0, 1, 1, 0, 0, 1, 1, 0],
    [0, 1, 1, 1, 1, 1, 0, 0],
    [1, 1, 0, 1, 0, 1, 0, 0],
    [1, 1, 0, 1, 1, 1, 0, 0],
    [1, 0, 0, 0, 0, 1, 0, 0],
    [0, 1, 0, 0, 1, 0, 1, 1],
    [1, 0, 0, 0, 0, 0, 0, 1],
    [1, 0, 0, 0, 1, 1, 1, 0],
    [1, 0, 1, 0, 0, 0, 0, 1],
]
```

  `$ ruby ejercicio_1.rb`

2. (Bonus) Asumamos que ahora la empresa X se volvió muy popular, y muchos postulantes quieren entrar ahí. Nuevamente nuestro
reclutador volvió a perder la pauta (quizás deberíamos respaldar estas cosas en drive), por lo que decidimos cambiar el
enfoque: Ahora necesitamos un algoritmo para obtener la pauta en el menor tiempo posible. Supongamos que tenemos una lista
de N respuestas (donde N es muuuuy grande). ¿Cómo sería un potencial algoritmo que permita obtener la pauta en 
el menor tiempo posible? (Hint: Usar fuerza bruta y revisar todas las respuestas para cada postulante no es factible).

  `$ ruby ejercicio_2.rb`

3. (Bonus) Ahora tenemos N postulantes y M preguntas (M muy grande). Nos interesa obtener el primer postulante
que obtenga K respuestas correctas (con K < M). Asumiendo que usar fuerza bruta y calcular toda la pauta no es factible,
¿Que algoritmo nos permite encontrarlo/a en el menor tiempo posible? (Hint: Iterar por todas las respuestas para obtener 
la pauta no es factible. Tampoco lo es iterar por cada postulante para obtener el total de correctas).

  `$ ruby ejercicio_3.rb`
