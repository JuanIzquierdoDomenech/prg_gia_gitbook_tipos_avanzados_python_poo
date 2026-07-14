---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

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

Añade este bloque al final del propio fichero `square.py`:

{% hint style="danger" icon="skull-crossbones" %}
**NO MODIFICAR ESTE BLOQUE DE CÓDIGO PRINCIPAL**

Su salida se podrá usar el día del examen para evaluaros.
{% endhint %}

<details>

<summary>Código de test</summary>

{% code title="" %}
```python
if __name__ == "__main__":
    from .point2d import Point2D
    from .exceptions import InvalidFigureError

    print("--- Pruebas del Constructor ---")
    s1 = Square()
    print(f"[count: {Square.count()}] s1 = {s1}")
    v_cuadrado = (Point2D(-2.0, 2.0), Point2D(2.0, 2.0), Point2D(2.0, -2.0), Point2D(-2.0, -2.0))
    s2 = Square("blue", v_cuadrado)
    print(f"[count: {Square.count()}] s2 = {s2}")
    
    print()
    print("--- Pruebas del Destructor ---")
    del(s1) # invocamos destructor __del__
    print(f"[count: {Square.count()}] del(s1)")
    
    print()
    print("--- Pruebas de Comparación ---")
    s_eq_1 = Square("red", v_cuadrado)
    s_eq_2 = Square("red", v_cuadrado)
    s_diff = Square("blue", v_cuadrado)
    
    print(f"s_eq_1: {s_eq_1}")
    print(f"s_eq_2: {s_eq_2}")
    print(f"s_diff: {s_diff}")
    
    print(f"  > s_eq_1 == s_eq_2: {s_eq_1 == s_eq_2}")
    print(f"  > s_eq_1 != s_eq_2: {s_eq_1 != s_eq_2}")
    print(f"  > s_eq_1 == s_diff: {s_eq_1 == s_diff}")

    print()
    print("--- Pruebas de Getters, Setters y Métodos ---")
    print(f"s2 antes:\n  > {s2}")
    s2.color = "red"
    v_cuad_nuevo = (Point2D(0.0, 4.0), Point2D(4.0, 4.0), Point2D(4.0, 0.0), Point2D(0.0, 0.0))
    s2.vertices = v_cuad_nuevo
    print(f"s2 modificado:\n  > {s2}")
    print(f"Valores leidos:")
    print(f"  > area={s2.area()}; perimeter={s2.perimeter()}")

    print()
    print("--- Pruebas de Indexación e Iteración ---")
    print(f"Acceso a s2 por s2.get_vertex(0): {s2.get_vertex(0)}")
    print(f"Acceso a s2 por s2[1] (__getitem__): {s2[1]}")
    
    print("Iterando vértices de s2:")
    for i, v in enumerate(s2):
        print(f"  Iteración {i}: {v}")

    print()
    print("--- Pruebas de Excepciones ---")
    print("Intentando instanciar Square con vértices de rectángulo (no cuadrado)...")
    try:
        # Vértices de un rectángulo 4x2
        v_rectangulo = (Point2D(0.0, 2.0), Point2D(4.0, 2.0), Point2D(4.0, 0.0), Point2D(0.0, 0.0))
        Square("red", v_rectangulo)
    except InvalidFigureError as e:
        print(f"  > Se capturó excepción InvalidFigureError correctamente: {e}")

    print("Intentando modificar un cuadrado con vértices completamente inválidos...")
    try:
        v_invalidos = (Point2D(0,0), Point2D(0,0), Point2D(10,5), Point2D(90,90))
        s2.vertices = v_invalidos
    except InvalidFigureError as e:
        print(f"  > Se capturó excepción InvalidFigureError correctamente: {e}")

    print()
    print("--- Pruebas con Conjuntos (Set) ---")
    lista_cuadrados = [Square("red", v_cuadrado),
                       Square("blue"),
                       Square("red", v_cuadrado)]
    print(f"Lista original con {len(lista_cuadrados)} cuadrados")
    conjunto_cuadrados = set(lista_cuadrados)
    print(f"Conjunto (sin duplicados) con {len(conjunto_cuadrados)} cuadrados")
    
    print()
    print(f"Figuras vivas (count): {Square.count()}")
```
{% endcode %}

</details>

Finalmente, úbicate en la raíz del proyecto (`p1`) y ejecuta el módulo `square` como si fuera un script usando la opción `-m` del intérprete de Python:

```bash
python -m figures.square
```

Deberías de generar una salida muy similar a esta:

<details>

<summary>Salida esperada</summary>

{% code title="" %}
```python
--- Pruebas del Constructor ---
[count: 1] s1 = Square(color: red, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
[count: 2] s2 = Square(color: blue, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))

--- Pruebas del Destructor ---
[count: 1] del(s1)

--- Pruebas de Comparación ---
s_eq_1: Square(color: red, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))
s_eq_2: Square(color: red, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))
s_diff: Square(color: blue, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))
  > s_eq_1 == s_eq_2: True
  > s_eq_1 != s_eq_2: False
  > s_eq_1 == s_diff: False

--- Pruebas de Getters, Setters y Métodos ---
s2 antes:
  > Square(color: blue, vertices: ((-2.0, 2.0), (2.0, 2.0), (2.0, -2.0), (-2.0, -2.0)))
s2 modificado:
  > Square(color: red, vertices: ((0.0, 4.0), (4.0, 4.0), (4.0, 0.0), (0.0, 0.0)))
Valores leidos:
  > area=16.0; perimeter=16.0

--- Pruebas de Indexación e Iteración ---
Acceso a s2 por s2.get_vertex(0): (0.0, 4.0)
Acceso a s2 por s2[1] (__getitem__): (4.0, 4.0)
Iterando vértices de s2:
  Iteración 0: (0.0, 4.0)
  Iteración 1: (4.0, 4.0)
  Iteración 2: (4.0, 0.0)
  Iteración 3: (0.0, 0.0)

--- Pruebas de Excepciones ---
Intentando instanciar Square con vértices de rectángulo (no cuadrado)...
  > Se capturó excepción InvalidFigureError correctamente: Los vértices proporcionados no conforman un cuadrado válido.
Intentando modificar un cuadrado con vértices completamente inválidos...
  > Se capturó excepción InvalidFigureError correctamente: Los vértices proporcionados no conforman un cuadrado válido.

--- Pruebas con Conjuntos (Set) ---
Lista original con 3 cuadrados
Conjunto (sin duplicados) con 2 cuadrados

Figuras vivas (count): 7
```
{% endcode %}

</details>

Si la semántica de tu salida es diferente a la esperada, revisa tu implementación.
