# DAA Problem Set
Franco Hernández Piloto C411  
December 2024

## Demostración de que Conjunto Dominante es NP-completo

### Definición de Conjunto Dominante

Dado un \( k \), decidir si existe un conjunto dominante de tamaño \( k \) o menor. Un conjunto dominante es aquel conjunto de vértices de un grafo donde para todo vértice que no está en dicho conjunto se cumple que al menos uno de los vértices adyacentes a él pertenece al conjunto dominante.

### Demostración de que es NP

Dado un conjunto dominante válido, se itera por cada vértice y se comprueba si pertenece al conjunto dominante o alguno de sus adyacentes pertenece al conjunto dominante en tiempo polinomial.

### Reducción usando Vertex Cover NP-completo

Sea \( C \) un vertex cover de tamaño \( k \). Demostraremos que existe un \( D \), conjunto dominante, en \( G \) de tamaño \( k + \) (cantidad de vértices con grado 0).

Asumamos que existe un vértice \( x \) tal que ninguno de sus vértices adyacentes pertenece a \( C \) y él mismo no está en \( C \):
- Como \( C \) es un vertex cover, cubre todas las aristas.
- Sea \( \langle u,x \rangle \) una arista que contiene a \( x \). Como \( u \) pertenece a \( C \) ya que dicha arista está cubierta por el vertex cover \( C \), llegamos a una contradicción ya que existiría un vértice \( u \) adyacente a \( x \) y que pertenece a \( C \).

Luego, todo vértice cuyo grado sea mayor que 0 y no pertenezca a \( C \), tiene al menos un vértice adyacente a él que pertenece a \( C \).

Sea el conjunto \( D \) formado por todos los vértices que están en el vertex cover \( C \). Al agregarle todos los vértices con grado 0, tendríamos un conjunto dominante ya que todo vértice de \( G \) que no está en \( D \), tiene al menos un adyacente que sí está en \( D \).

Luego existe un conjunto dominante \( D \) de tamaño \( k \) más la cantidad de vértices con grado 0. Por lo tanto, como es NP y NP-hard, es NP-completo.

## Número Cromático

El número cromático de un grafo es el mínimo número de colores necesarios para colorear los vértices del grafo de manera que dos vértices adyacentes no compartan el mismo color.

## Determinación del Número Cromático de un Grafo

### Prueba de NP-dureza: Reducción de 3-SAT al Número Cromático

Consideremos una instancia de 3-SAT con variables \( x_1, ..., x_n \) y cláusulas \( C_1, ..., C_k \). Construiremos un grafo \( G = (V,E) \) que es 3-coloreable si y solo si la instancia de 3-SAT es satisfacible.

Comenzamos con un grafo vacío y añadimos tres nodos conectados formando un triángulo. Esto asegura que cada nodo reciba un color distinto al ser coloreado. Etiquetaremos estos nodos como Verdadero, Falso y Base, y nos referiremos a sus colores asociados de la misma manera.

Para cada variable \( x_i \) (donde \( i \in [1,n] \)), creamos nodos \( v_i \) y \( \neg v_i \), formando un triángulo con el nodo Base. Esto garantiza que al colorear los nodos correspondientes a una variable, no se les pueda asignar el color Base, pero sí Verdadero o Falso, y que una variable y su negación nunca tengan el mismo color.

En este punto, el grafo siempre es 3-coloreable. Para representar cada cláusula del 3-SAT y forzar al grafo a requerir más de 3 colores si una cláusula no puede ser satisfecha, añadimos la siguiente estructura:

![Reduccion Numero Cromatico](Reduccion_Numero_Cromatico_Imagen.png)

- La estructura asegura que el nodo superior (nodo A) no pueda ser coloreado con Base, Verdadero o Falso si todos los nodos correspondientes a las variables (\( v_1, \neg v_2, v_3 \)) están coloreados como Falso.
- Por lo tanto, si todas las variables son asignadas como Falso, el grafo no será 3-coloreable. En cualquier otro caso, este subgrafo es 3-coloreable.

Para cada cláusula \( C_i \), creamos un subgrafo como el descrito, usando las variables correspondientes a esa cláusula. El grafo resultante asegura que una variable y su negación no reciban el mismo color, y para ser 3-coloreable, al menos una variable en cada cláusula debe ser asignada el color Verdadero.

Por lo tanto, para determinar si la instancia de 3-SAT es satisfacible, podemos construir el grafo \( G \) y encontrar su número cromático. Si es 3, entonces asignar verdadero a las variables correspondientes a los nodos con el color Verdadero produce una asignación que asegura al menos una variable verdadera por cláusula, satisfaciendo la FNC. Por el contrario, si tenemos una asignación que satisface la FNC, colorear los nodos correspondientes a cada variable con su valor de verdad proporciona una 3-coloración válida del grafo.

Esta reducción demuestra que encontrar el número cromático es al menos tan difícil como resolver 3-SAT, probando que determinar el número cromático es NP-duro.

## Demostración de Clique NP-completo

### Demostración de que Clique es NP

Dado el conjunto de vértices del clique, verificar por cada uno si todos los otros vértices del clique son sus adyacentes se realiza en tiempo polinomial \( O(n^2) \), donde \( n \) es el tamaño del clique. Luego, es NP.

### Reducción usando Conjunto Independiente NP-completo

Sea \( I \) un conjunto independiente en grafo \( G = (V,E) \) de tamaño \( k \).
Sea \( G' = (V,E') \) donde \( E' \) son todas las aristas que no están en \( E\), ya que no hay aristas entre los vértices de \( I\) en \( G\).
Luego, en \( G' \), cada par de vértices en \( I\) está conectado por una arista formando un clique en \( G'\).
Por lo tanto, como es NP y NP-hard, es NP-completo.
