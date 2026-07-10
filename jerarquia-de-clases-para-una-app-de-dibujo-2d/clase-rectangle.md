# Clase Rectangle

## Descripción de la clase

El tipo de datos Rectangle, que representa un rectángulo en un espacio bidimensional, estará definido por una clase en Python derivada de la interfaz `Shape`. Será un objeto iterable (implementará los métodos especiales `__iter__` y `__next__`.

### Atributos

<table><thead><tr><th width="133.75">Nombre</th><th width="155.9609375">Tipo</th><th width="130.55078125">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>vertices</code></td><td>de instancia</td><td>protegido</td><td><p>Tupla de 4 elementos de tipo <code>Point2D</code> correspondientes a los vértices v0, v1, v2 y v3 de un rectángulo. </p><p></p><p>¡Atención! Usaremos una tupla de Python y no una lista para garantizar que no se pueden ni añadir ni eliminar vértices.</p></td></tr><tr><td><code>N_VERTICES</code></td><td>de clase/estática</td><td>protegido</td><td>Constante de clase asociada al Rectangle con el número de vértices de un rectángulo (4).</td></tr></tbody></table>

### Métodos

<table><thead><tr><th>Perfil</th><th width="125.7578125">Visibilidad</th><th width="186.04296875">Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>check(vertices)</code></td><td>protegido</td><td>Estático</td><td>Comprueba, a partir de la secuencia provista, si esos vértices conforman un rectángulo válido.</td></tr><tr><td><code>__init__(color, vertices)</code></td><td>-</td><td>Método (constructor) de instancia</td><td><p>Creará un rectángulo. Por defecto, los vértices de la tupla serán v0=(-1,0.5); v1=(1,0.5), v2=(1,-0.5), y v3=(-1,-0.5). </p><p></p><p>Si se proveen vértices que no conforman un rectángulo, lanzará <code>InvalidFigureError</code>.</p></td></tr><tr><td><code>get_vertex(ind)</code></td><td>público</td><td>De instancia</td><td><p>Devuelve el <code>Point2D</code> del rectángulo que ocupa el índice <code>ind</code>. </p><p></p><p>Lanza una excepción estándar <code>IndexError</code> si el índice está fuera del intervalo <code>[0, 3]</code>.</p></td></tr><tr><td><code>__getitem__(ind)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores)</td><td><p>Es una vía puramente Pythonica de invocar <code>get_vertex(ind)</code>. </p><p></p><p>Permite invocar índices con corchetes (por ejemplo, <code>rectangulo[0]</code> a <code>rectangulo[3]</code>).<br></p></td></tr><tr><td><code>vertices()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve la tupla alojada en el atributo protegido <code>vertices</code>.</td></tr><tr><td><code>vertices(vertices)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td><p>Modifica el atributo protegido <code>vertices</code> a partir de una secuencia/tupla de 4 <code>Point2D</code>. </p><p></p><p>Si no conforman un rectángulo válido, lanzará <code>InvalidFigureError</code>.</p></td></tr><tr><td><code>__eq__(other)</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Compara si dos rectángulos son lógicamente iguales (mismo color y vértices).</td></tr><tr><td><code>__hash__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Método para insertar y recuperar clases del rectángulo en un <code>set()</code>.</td></tr><tr><td><code>__iter__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores)</td><td>Inicializa un atributo privado que controla la iteración (índice a 0) y se devuelve a sí mismo (el propio objeto) como objeto iterador.</td></tr><tr><td><code>__next__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores)</td><td>Devuelve el siguiente vértice progresivamente usando el índice interno de iteración.</td></tr><tr><td><code>__str__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td><p>Devuelve una cadena de texto representando el rectángulo. </p><p></p><p>Por ejemplo: <code>"Rectangle(color: red, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))"</code>.</p></td></tr></tbody></table>

{% hint style="info" %}
Por simplicidad, asumiremos que un rectángulo de vértices $$v_0, v_1, v_2, v_3$$ será válido solo si, por un lado, las aristas ​​ tienen la misma longitud, y por otro lado, las aristas $$\overline{v_0v_1}$$​​ y $$\overline{v_2v_3}$$ tienen la misma longitud. Considera hacer uso del método estático `Point2D.distance()`.
{% endhint %}

***

## Actividad 8: Implementación de la clase Rectangle <a href="#actividad-8-implementacion-de-la-clase-rectangle" id="actividad-8-implementacion-de-la-clase-rectangle"></a>

Desde `figures`, crea com vim el fichero `rectangle.py` e implementala según la especificación anterior.

***

