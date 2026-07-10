# Clase Square

Descripción de la clase

El tipo de datos `Square`, que representa un cuadrado en un espacio bidimensional, estará definido por una clase en Python de igual nombre, **derivada de la clase** [**`Rectangle`**](clase-rectangle.md).

{% hint style="info" %}
Notad que esta clase está en un segundo nivel de jerarquía, es decir, es una subclase de una subclase.

Aquí se aprecia más aún la ventaja de la herencia, ya que reaprovecharemos mucho código.
{% endhint %}

### Atributos

Esta clase no define nuevos atributos. Su inicialización estará atada a las especificaciones base del rectángulo.

### Métodos

Esta clase deberá **sobreescribir el método de representación `__str__()` y la propiedad de modificación `vertices` heredados de la clase `Rectangle`.**

<table><thead><tr><th width="181.87109375">Perfil</th><th width="129.2890625">Visibilidad</th><th width="196.390625">Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>check(vertices)</code></td><td>privado</td><td>Estático</td><td><p>Sobreescritura del método heredado de la clase <code>Rectangle</code>. </p><p></p><p>Comprueba, a partir de una secuencia/tupla de 4 <code>Point2D</code>, si esos vértices conforman un cuadrado válido.</p></td></tr><tr><td><code>__init__(color, vertices)</code></td><td>-</td><td>Método (constructor) de instancia</td><td><p>Creará un cuadrado. </p><p></p><p>Por defecto, los vértices serán v0=(-1,1); v1=(1,1), v2=(1,-1), y v3=(-1,-1). </p><p></p><p>Lanzará <code>InvalidFigureError</code> si fallan la conformación inicial.</p></td></tr><tr><td><code>vertices()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve la tupla alojada en el atributo protegido <code>vertices</code> heredado de la clase <code>Rectangle</code>.</td></tr><tr><td><code>vertices(vertices)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td><p>Sobreescritura del método heredado de la clase <code>Rectangle</code>. </p><p></p><p>Valida los vértices del cuadrado. </p><p></p><p>Lanzará <code>InvalidFigureError</code> en caso de que no conformen un cuadrado válido.</p></td></tr><tr><td><code>__str__()</code></td><td>-</td><td>Método de instancia (sobrescritura de <code>__str__()</code> de <code>Rectangle</code>)</td><td><p>Sobreescritura del método heredado de la clase <code>Rectangle</code>. </p><p></p><p>Devuelve una cadena de texto representando el cuadrado. </p><p></p><p>Por ejemplo: <code>"Square(color: green, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))"</code>.</p></td></tr></tbody></table>

{% hint style="warning" %}
Como la propiedad `vertices` heredada de la clase `Rectangle` debe ser sobreescrita a causa de la validación de vértices en el setter, debemos reimplementarla completamente (tanto el getter como el setter).
{% endhint %}

{% hint style="info" icon="calculator-simple" %}
Por simplicidad, asumiremos que un cuadrado de vértices $$v_0, v_1, v_2, v_3$$​ será válido solo si todas sus aristas $$\overline{v_0 v_1}$$ , $$\overline{v_1 v_2}$$, $$\overline{v_2 v_3}$$ y​ $$\overline{v_3 v_4}$$​ tienen la misma longitud. De nuevo, considera hacer uso del método estático `Point2D.distance()`.
{% endhint %}

***

## Actividad 10: Implementación de la clase `Square` <a href="#actividad-10-implementacion-de-la-clase-square" id="actividad-10-implementacion-de-la-clase-square"></a>

Desde el paquete `figures`, crea con vim el fichero `square.py`. e implementa la clase según la especificación anterior.

***

## Actividad 11: Depuración de la clase `Square`

