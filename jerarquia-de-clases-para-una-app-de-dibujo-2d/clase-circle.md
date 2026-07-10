# Clase Circle

## Descripción de la clase

El tipo de datos `Circle`, que representa un círculo en un espacio bidimensional, estará definido por una clase en Python de igual nombre, derivada de la clase abstracta `Shape`.

### Atributos <a href="#atributos" id="atributos"></a>

<table><thead><tr><th width="110.1875">Nombre</th><th width="136.51953125">Tipo</th><th width="143.91796875">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>center</code></td><td>de instancia</td><td>privado</td><td>Centro del círculo (tipo <code>Point2D</code>).</td></tr><tr><td><code>radius</code></td><td>de instancia</td><td>privado</td><td>Radio del círculo (tipo <code>float</code>). Debe ser mayor o igual que 0.</td></tr></tbody></table>

Métodos

**Además de los métodos abstractos heredados de la interfaz** [**`Shape`**](clase-abstracta-shape.md) que deberás implementar por "contrato" (`area()`, `perimeter()`, etc.), esta clase deberá implementar los siguientes métodos:

<table><thead><tr><th width="179.421875">Perfil</th><th width="128.2734375">Visibilidad</th><th>Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__(color, center, radius)</code></td><td>-</td><td>Método (constructor) de instancia</td><td>Extiende al constructor de la clase base. <code>center</code> debe ser un <code>Point2D</code> (si no, lanzará una excepción <code>TypeError</code>), y <code>radius</code> un valor numérico mayor o igual que cero (si no, lanzará una excepción <code>ValueError</code>). Por defecto, el color será "red", el centro (0,0) y radio 1.</td></tr><tr><td><code>center()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve el atributo <code>center</code>.</td></tr><tr><td><code>center(p)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td>Modifica el atributo <code>center</code> con una instancia de <code>Point2D</code> (si no, lanzará una excepción <code>TypeError</code>).</td></tr><tr><td><code>radius()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve el atributo <code>radius</code>.</td></tr><tr><td><code>radius(r)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td>Modifica el atributo <code>radius</code>. Lanzará <code>ValueError</code> cuando corresponda.</td></tr><tr><td><code>__eq__(other)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Compara si dos círculos son lógicamente idénticos (mismo color, centro y radio).</td></tr><tr><td><code>__hash__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Método para usar <code>Circle</code> en un <code>set</code>. Puedes retornar el hash de la tupla conteniendo color, y atributos del centro y el radio.</td></tr><tr><td><code>__str__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Devuelve una cadena de texto representando el círculo. Por ejemplo: <code>"Circle(color: red, center: (0.0, 0.0), radius: 1.0)"</code>.</td></tr></tbody></table>

{% hint style="warning" %}
Recuerda que el constructor de la clase derivada (`Circle` en este caso) debe invocar al constructor de la clase base (`Shape`) para inicializar los atributos comunes, antes de realizar cualquier otra operación.

_Primero establecemos los cimientos de la clase base, luego establecemos los detalles de la clase derivada._
{% endhint %}
