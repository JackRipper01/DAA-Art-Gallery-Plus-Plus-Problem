# Problemas

## 0 - Policías

Kevin y $N$ oficiales de policía están parados en posiciones distintas en una cuadrícula unidimensional. Se mueven por turnos: primero, cada oficial se mueve un paso a la izquierda o a la derecha hacia un cuadrado desocupado, luego el Kevin se mueve a la izquierda o a la derecha hacia un cuadrado desocupado. Un oficial que no puede moverse es eliminado, y si el Kevin no puede moverse, es capturado. Encuentra el número máximo de oficiales que pueden ser eliminados.

## 1 - Distancia de árboles

Te dan dos enteros $x$ y $y$. Tu tarea es construir un árbol con las siguientes propiedades:

- El número de pares de vértices con una distancia par entre ellos es igual a $x$.
- El número de pares de vértices con una distancia impar entre ellos es igual a $y$.

Por un par de vértices, nos referimos a un par ordenado de dos (posiblemente, el mismo o diferente) vértices.

## 2 - Las cajas

Dado que hay $n$ bolsas, cada una con $a_i$ pelotas amarillas y $b_i$ pelotas verdeses, y cada caja puede contener $k$ pelotas, pero cada caja solo puede contener pelotas de la misma bolsa o pelotas del mismo color (amarillo o verdes):

Determina el número máximo de cajas que se puede llenar completamente.

## 3 - Subsecuencia X

Te dan un array de $N$ enteros como $A_1, A_2, A_3, \dots, A_N$. Tu tarea es encontrar el número de formas de dividir el array en subarrays contiguos tales que:

1. Cada elemento del array dado $A$ pertenezca exactamente a uno de los subarrays.
2. Existe un entero $m$, tal que el $X$ de cada subarray es igual a $m$.

El $X$ de una secuencia es el menor entero no negativo que no aparece en la secuencia.

## 4 - Subsecuencia Y

Dado un array binario $A$, encuentra la secuencia Y más larga $x_1, x_2, \dots, x_k$ tal que satisface:

$1 \leq x_1 < x_2 < \dots < x_k \leq N + 1$

$A[x_i : x_j - 1]$ contiene un número igual de ceros y unos para cada $i < j$.

## 5 - Asignación Equilibrada

Enunciado

Dado un grafo $G$ no dirigido de $n$ nodos, y tres números enteros $n_1$, $n_2$ y $n_3$ que cumplen:

\[
n_1 + n_2 + n_3 = n
\]

el problema consiste en asignar a cada vértice un número $1$, $2$ o $3$ de forma tal que:

1. La cantidad de nodos etiquetados con $1$, $2$ y $3$ sea exactamente igual a $n_1$, $n_2$ y $n_3$ respectivamente.
2. Para toda arista $(u, v) \in G$, si los valores asignados a sus extremos son $a$ y $b$, entonces se cumple que:

\[
|a - b| = 1
\]

El objetivo es determinar si existe una asignación válida y, en caso afirmativo, encontrarla.

## 6 - Ganancias y pérdidas

Se tiene un grafo simple (es decir, un grafo sin lazos ni múltiples aristas) que consta de $n$ vértices y $m$ aristas.

El peso del $i$-ésimo vértice es $a_i$.

El peso de la $i$-ésima arista es $w_i$.

Un subgrafo de un grafo es un conjunto de vértices del grafo y un conjunto de aristas del grafo. El conjunto de aristas debe cumplir la condición de que ambos extremos de cada arista del conjunto deben pertenecer al conjunto de vértices elegido.

El peso de un subgrafo es la suma de los pesos de sus aristas, menos la suma de los pesos de sus vértices. Necesitas encontrar el peso máximo de un subgrafo del grafo dado. El grafo dado no contiene lazos ni múltiples aristas.

## 7 - Cuadriculando

Se tiene una cuadrícula cuadrada de tamaño $n \times n$. Algunas celdas están coloreadas de negro, mientras que las demás están coloreadas de blanco. En una operación, puedes seleccionar un rectángulo y colorear todas sus celdas de blanco. El costo para colorear un rectángulo de tamaño $h \times w$ es $min(h, w)$. Debes hacer que todas las celdas sean blancas con el costo total mínimo.

## 8 - Visita

Dado un grafo con n nodos y m aristas. Cada arista conecta un par de nodos distintos y es bidireccional. Entre cualquier par de nodos, como máximo hay un arista. Para cada arista, se conoce su longitud.

Sabemos que el visitante pronto viajará desde la ciudad s hasta la ciudad t y elegirá uno de los aristas más cortos de s a t, pero no se sabe cuál arista escogerá.

se desea reparar los aristas en las posibles rutas del visitante.

Para todos los pares distintos s, t (s < t), encuentra el número de aristas que están en al menos un arista más corto entre s y t.

## 9 - Conectar todo

Dado un conjunto de $N$ nodos, donde cada nodo tiene un valor asociado $A_i$, se deben conectar todos los nodos mediante un conjunto de aristas bidireccionales. Una arista de longitud $L$ $(L > 0)$ puede ser construida entre los nodos $X$ e $Y$ si $(A_X \& A_Y \& L) = L$, donde $ \& $ representa el operador AND a nivel de bits.

Se solicita determinar la longitud mínima total de las aristas necesarias para conectar todos los nodos, o imprimir $-1$ si no es posible conectarlos.

- Dos nodos $X$ e $Y$ se consideran conectados si existe una secuencia de nodos $C_1, C_2, \dots, C_K$ $(K \geq 1)$ tal que $C_1 = X$, $C_K = Y$, y existe una arista entre $C_i$ y $C_{i+1}$ $(1 \leq i < K)$.
- Todos los nodos están conectados si cualquier par de nodos está conectado directa o indirectamente.

## 10 - Dos permutaciones

Se te dan dos permutaciones $a$ y $b$, ambas de tamaño $n$. Una permutación de tamaño $n$ es un array de $n$ elementos, donde cada entero de $1$ a $n$ aparece exactamente una vez. Los elementos en cada permutación están indexados de $1$ a $n$.

Puedes realizar la siguiente operación cualquier número de veces:

1. Elige un entero $i$ de $1$ a $n$;
2. Sea $x$ el entero tal que $a_x = i$. Intercambia $a_i$ con $a_x$;
3. Sea $y$ el entero tal que $b_y = i$. Intercambia $b_i$ con $b_y$.

Tu objetivo es ordenar ambas permutaciones en orden ascendente (es decir, que se cumplan las condiciones $a_1 < a_2 < \cdots < a_n$ y $b_1 < b_2 < \cdots < b_n$) utilizando el número mínimo de operaciones. Ten en cuenta que ambas permutaciones deben estar ordenadas después de realizar la secuencia de operaciones que hayas elegido.

## 11 - 3 puntos

Proporcione un algoritmo para determinar si en un plano hay 3 puntos alineados. Proporcionar un argumento por el cual se supone que no existe una solución con complejidad temporal polinomialmente menor

## 12 - Sistema

Un sistema consume un litro de petróleo por minuto y no puede contener más de $C$ litros. Inicialmente, hay $C_0$ litros. El sistema debe funcionar durante $m$ minutos, manteniendo al menos un litro de petróleo al inicio de cada minuto.

Hay $n$ amigos que pueden traer petróleo al sistema. El $i$-ésimo amigo:

- Puede traer como máximo $a_i$ litros de petróleo.
- Llega al inicio del minuto $t_i$.
- Cobra $p_i$ dólares por litro de petróleo que trae.

Objetivo
Determinar:

1. Cuántos litros de petróleo debe traer cada amigo para que el sistema funcione durante $m$ minutos.
2. Minimizar el costo total de petróleo pagada a los amigos.
3. Informar si no es posible mantener el sistema funcionando durante $m$ minutos.

Salida esperada
Entregar la cantidad mínima de dólares que se debe pagar o indicar que no es posible regar el jardín por $m$ minutos.

## 13 - Destrucción

Consideremos un grafo no dirigido $G$ que consta de $n$ nodos y $m$ aristas. Cada arista $e_i$ posee 2 valores $c_i$ y $t_i$ tal que $c_i$ es el color correspondiente a la arista y $t_i$ el tiempo que toma eliminarla.  El objetivo es eliminar aristas de $G$ en el menor tiempo posible en el menor tiempo posible, cumpliendo las siguientes restricciones:

- No se pueden eliminar dos aristas que compartan un nodo.

- No pueden quedar dos aristas del mismo color que compartan un nodo.

- El tiempo total para eliminar un conjunto $E$ de aristas se define como $\max_{e_i \in E}{t_i}$

Si no es posible eliminar un conjunto de aristas que cumpla con estas condiciones, se debe imprimir "No". Si existe una solución, se debe imprimir "Sí", seguido del tiempo requerido y la cantidad de aristas a eliminar. Finalmente, se debe mostrar el conjunto de aristas a eliminar.

## 14 - Sistema de Seguridad en un Laboratorio

Un laboratorio de alta tecnología cuenta con un sistema de seguridad que monitorea el nivel de radiación permitido en una cámara sellada. Si el nivel de radiación excede un umbral secreto L, el sistema activa una alarma y bloquea el acceso a la cámara.
El valor de L es desconocido, pero puedes realizar experimentos en los que incrementas la radiación en X unidades. Dependiendo del valor de X en relación con L, ocurren los siguientes eventos:
Si X≤L : El experimento se completa con éxito, y la radiación acumulada en la cámara aumenta en X unidades.
Si X>L: El sistema activa la alarma, bloquea el experimento, y debes descontar X unidades de tu energía restante.
Si intentas realizar un experimento y tu energía disponible es menor que X, el sistema te expulsa del laboratorio por condiciones inseguras.

Se comienza con 1 unidad de energía. Se deben realizar no más de  110 operaciones para hallar el valor de L. Se asegura que L<10^14

## 15 - Cuento de un territorio

Determina si, dadas las posiciones actuales de los castillos, es posible que un país haya surgido mediante un proceso de unificación de territorios rectangulares. Considera las siguientes condiciones:

1. Inicialmente, había varios territorios rectangulares en el mapa, con paredes paralelas a los ejes y esquinas ubicadas en coordenadas enteras. Ninguno de los territorios se superponía, aunque podían compartir fronteras.

2. A medida que pasó el tiempo, pares de territorios se fusionaron para formar un rectángulo más grande. Este proceso continuó hasta formar un único territorio que representa el país actual.

3. Cada territorio inicial contenía un castillo rectangular construido dentro de su área, con las mismas restricciones de orientación y posicionamiento que los territorios. Estos castillos permanecieron intactos después de las fusiones.

Tu tarea es verificar si, dado un conjunto de posiciones actuales de castillos, es posible que el país haya sido formado como lo describe la historia.

## 16 - Emparejamiento

Se te proporciona un grafo bipartito con:

- $n_1$ vértices en la primera parte.
- $n_2$ vértices en la segunda parte.
- $m$ aristas.

El emparejamiento máximo en este grafo es el subconjunto más grande posible (en tamaño) de aristas, de manera que ningún vértice esté incidente a más de una arista seleccionada.

Debes procesar dos tipos de consultas en este grafo:

Consulta Tipo `1`

- Elimina el número mínimo posible de vértices del grafo para que el tamaño del emparejamiento máximo se reduzca exactamente en 1.
- Imprime los vértices eliminados.
- Luego, encuentra un nuevo emparejamiento máximo en el grafo y suma los índices de las aristas que pertenecen a este emparejamiento. Imprime esta suma.

Consulta Tipo `2`

- Se realiza solo después de una consulta de tipo `1`.
- Imprime las aristas que forman el emparejamiento máximo encontrado en la consulta anterior.

- El problema se debe resolver en modo en línea. Esto significa que:
  - No puedes leer toda la entrada de una sola vez.
  - Solo puedes leer cada consulta después de escribir la respuesta a la consulta anterior.
