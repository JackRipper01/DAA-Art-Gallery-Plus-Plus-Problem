# Informe: Solución al Problema de Seguridad en el Museo

## 1. Introducción y Definición del Problema

En este informe, abordamos el problema de optimización para la seguridad de un museo. El objetivo principal es **ubicar estratégicamente dispositivos de seguridad** en una habitación del museo para **vigilar todos los objetos de valor** dentro de ella, **minimizando el costo total** de los dispositivos utilizados debido a un presupuesto limitado.

Se consideran los siguientes tipos de dispositivos de seguridad:

1. **Sensor de Proximidad:** Detecta la presencia en áreas específicas.
2. **Cámara de Vigilancia de 360 Grados:** Vista panorámica completa sin puntos ciegos.
3. **Cámara de Vigilancia de 120 Grados:** Amplio campo de visión para áreas grandes.
4. **Cámara de Vigilancia de 60 Grados:** Vigilancia detallada para objetos específicos.

El problema, en su forma inicial, se puede resumir como:

* **Entrada:**
    * Plano de la habitación del museo representado como un polígono simple.
    * Coordenadas 2D de los vértices del polígono.
    * Coordenadas 2D de cada objeto de valor dentro del polígono.
    * Tipos de dispositivos de seguridad disponibles y sus costos.
* **Salida:**
    * Una configuración de dispositivos de seguridad (tipo y ubicación en los vértices del polígono) que garantice la vigilancia de todos los objetos de valor.
    * Esta configuración debe tener el costo total mínimo posible.

## 2. Enfoque Propuesto: Reducción al Problema de Weighted Set Cover

Nuestro enfoque para resolver este problema consiste en **reducirlo al problema clásico de Weighted Set Cover (Cobertura de Conjuntos Ponderada)**.  El problema de Weighted Set Cover es un problema de optimización combinatoria bien conocido y estudiado, para el cual existen algoritmos de aproximación y técnicas de solución.

La idea central es modelar el problema de seguridad en el museo en términos de conjuntos y costos, de manera que encontrar una solución óptima para el Weighted Set Cover resultante nos proporcione una solución óptima para el problema de seguridad.

## 3. Reducción Formal a Weighted Set Cover

Para formalizar la reducción, definimos los siguientes elementos:

### 3.1. Universo (U)

Sea  `U` el **conjunto de todos los objetos de valor** en el museo. Cada objeto de valor es un elemento único en este universo.

* **Definición Formal:**  `U = {o1, o2, ..., on}`, donde `oi` representa el i-ésimo objeto de valor en el museo, y `n` es el número total de objetos de valor.  Aquí, `o1`, `o2`, hasta `on` representan los objetos individuales en el conjunto U.

### 3.2. Colección de Conjuntos (S) y sus Pesos

Para cada vértice `v` del polígono que representa la habitación del museo, y para cada tipo de dispositivo de seguridad `d` disponible, definimos un conjunto `S_vd`. Este conjunto contiene todos los objetos de valor que son **vigilados** por el dispositivo `d` si este se coloca en el vértice `v`.

* **Definición Formal:** Para cada vértice `v` del polígono y cada tipo de dispositivo `d` en {Sensor de Proximidad, Cámara 360°, Cámara 120°, Cámara 60°}, definimos el conjunto `S_vd` como:
    `S_vd = {o en U | el objeto o es vigilado por el dispositivo d colocado en el vértice v }`.
    Esto significa que `S_vd` es el conjunto de todos los objetos `o` que pertenecen al universo `U` (objetos de valor) y que son vigilados por el dispositivo `d` cuando se coloca en el vértice `v`.

Cada conjunto `S_vd` tiene un peso asociado, que corresponde al costo de instalar el dispositivo `d`.

* **Definición Formal:** Sea `costo(d)` el costo de un dispositivo de tipo `d`. El peso del conjunto `S_vd` se define como:
    `peso(S_vd) = costo(d)`.
    En otras palabras, el peso del conjunto `S_vd` es simplemente el costo del dispositivo `d`.

### 3.3. Instancia del Problema Weighted Set Cover

Con las definiciones anteriores, podemos construir una instancia del problema Weighted Set Cover de la siguiente manera:

* **Universo:** `U = {o1, o2, ..., on}` (Conjunto de objetos de valor).
* **Colección de Conjuntos:** `S = {S_vd | para cada vértice v del polígono y cada tipo de dispositivo d}`.
    Esto significa que `S` es una colección de todos los conjuntos `S_vd` que podemos formar considerando cada vértice `v` y cada tipo de dispositivo `d`.
* **Pesos de los Conjuntos:** Para cada `S_vd` en `S`, el peso es `peso(S_vd) = costo(d)`.

### 3.4. Reducción

El problema de seguridad en el museo se reduce al problema Weighted Set Cover de la siguiente manera:

* **Instancia del problema de Seguridad:**  Polígono, vértices, objetos de valor, tipos de dispositivos y sus costos.
* **Instancia del problema Weighted Set Cover (construida a partir de la instancia de Seguridad):**
    * Universo `U` = Conjunto de objetos de valor.
    * Colección de conjuntos `S = {S_vd}`  (donde `S_vd` son los objetos vigilados por el dispositivo `d` en el vértice `v`).
    * Pesos de los conjuntos: `peso(S_vd) = costo(d)`.

**Resolver el problema Weighted Set Cover para esta instancia nos dará una solución que puede traducirse directamente a una solución para el problema de seguridad en el museo:**

* **Solución de Weighted Set Cover:** Un subconjunto de conjuntos `C` contenido en `S` tal que la unión de todos los conjuntos en `C` es igual a `U` (es decir, la unión de todos los `S_vd` que están en `C` es igual a `U`) y la suma de los pesos de los conjuntos en `C` es mínima.
* **Solución del problema de Seguridad:** Para cada conjunto `S_vd` en `C` (la solución de Weighted Set Cover), colocamos el dispositivo `d` en el vértice `v`. Esta configuración de dispositivos garantizará que todos los objetos de valor estén vigilados (porque la unión de los conjuntos cubre `U`) y tendrá el costo mínimo (porque la solución de Weighted Set Cover minimiza la suma de los pesos).

### 3.5. Correctitud de la Reducción

**Demostración de la Correctitud de la Reducción:**

* **Si encontramos una solución óptima para Weighted Set Cover:**  Esta solución nos indica qué conjuntos `S_vd` seleccionar. Cada selección de `S_vd` corresponde a colocar un dispositivo `d` en el vértice `v`.  Dado que la solución de Weighted Set Cover cubre todo el universo `U` (todos los objetos), sabemos que todos los objetos estarán vigilados.  Además, como la solución de Weighted Set Cover es de costo mínimo, la configuración de dispositivos resultante también tendrá el costo mínimo.

* **Si existe una solución óptima para el problema de Seguridad:**  Esta solución consiste en una configuración de dispositivos en los vértices que vigila todos los objetos con el menor costo posible. Podemos mapear esta solución a una solución de Weighted Set Cover seleccionando los conjuntos `S_vd` correspondientes a los dispositivos colocados en cada vértice.  Dado que la solución de seguridad cubre todos los objetos, la unión de estos conjuntos cubrirá el universo `U`.  Y como la solución de seguridad es de costo mínimo, la solución de Weighted Set Cover resultante también tendrá un peso mínimo.


**[Espacio para definir formalmente "vigilar" para cada tipo de dispositivo.]**
