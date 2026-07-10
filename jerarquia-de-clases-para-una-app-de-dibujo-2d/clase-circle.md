# Clase Circle

## Descripción de la clase

El tipo de datos `Circle`, que representa un círculo en un espacio bidimensional, estará definido por una clase en Python de igual nombre, derivada de la clase abstracta `Shape`.

### Atributos <a href="#atributos" id="atributos"></a>

<table><thead><tr><th width="110.1875">Nombre</th><th width="136.51953125">Tipo</th><th width="143.91796875">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>center</code></td><td>de instancia</td><td>privado</td><td>Centro del círculo (tipo <code>Point2D</code>).</td></tr><tr><td><code>radius</code></td><td>de instancia</td><td>privado</td><td>Radio del círculo (tipo <code>float</code>). Debe ser mayor o igual que 0.</td></tr></tbody></table>

Métodos

**Además de los métodos abstractos heredados de la interfaz** [**`Shape`**](clase-abstracta-shape.md) que deberás implementar por "contrato" (`area()`, `perimeter()`, etc.), esta clase deberá implementar los siguientes métodos:

<table><thead><tr><th width="179.421875">Perfil</th><th width="128.2734375">Visibilidad</th><th>Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__(color, center, radius)</code></td><td>-</td><td>Método (constructor) de instancia</td><td>Extiende al constructor de la clase base. <code>center</code> debe ser un <code>Point2D</code> (si no, lanzará una excepción <code>TypeError</code>), y <code>radius</code> un valor numérico mayor o igual que cero (si no, lanzará una excepción <code>ValueError</code>). Por defecto, el color será "red", el centro (0,0) y radio 1.</td></tr><tr><td><code>center()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve el atributo <code>center</code>.</td></tr><tr><td><code>center(p)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td>Modifica el atributo <code>center</code> con una instancia de <code>Point2D</code> (si no, lanzará una excepción <code>TypeError</code>).</td></tr><tr><td><code>radius()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve el atributo <code>radius</code>.</td></tr><tr><td><code>radius(r)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td>Modifica el atributo <code>radius</code>. Lanzará <code>ValueError</code> cuando corresponda.</td></tr><tr><td><code>__eq__(other)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Compara si dos círculos son lógicamente idénticos (mismo color, centro y radio).</td></tr><tr><td><code>__hash__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Método para usar <code>Circle</code> en un <code>set</code>. Puedes retornar el hash de la tupla conteniendo color, y atributos del centro y el radio.</td></tr><tr><td><code>__str__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Devuelve una cadena de texto representando el círculo. Por ejemplo: <code>"Circle(color: red, center: (0.0, 0.0), radius: 1.0)"</code>.</td></tr></tbody></table>

{% hint style="warning" %}
Recuerda que el constructor de la clase derivada (`Circle` en este caso) debe invocar al constructor de la clase base (`Shape`) para inicializar los atributos comunes, antes de realizar cualquier otra operación, mediante la invocación de `__init__()` a través de `super()`.

_Primero establecemos los cimientos de la clase base, luego establecemos los detalles de la clase derivada._
{% endhint %}

{% hint style="info" %}
Usa la constante `math.pi` de la librería `math` de Python.
{% endhint %}

***

## Actividad 6: Implementación de la clase Circle

Desde el paquete `figures`, crea el fichero `circle.py`. Aquí tienes una plantilla para comenzar a adaptar:

```python
import math
from .shape import Shape
from .point2d import Point2D
from .exceptions import InvalidFigureError

class Circle(Shape):
    # Completar!
```

{% hint style="warning" %}
Recuerda que **debes implementar las funciones abstractas heredadas de `Shape`**: `area()`, `perimeter()`, `translate()`. En caso contrario, al intentar instanciar la clase `Circle`, se lanzará una excepción `TypeError`.
{% endhint %}

***

## Actividad 7: Depuración de la clase `Circle` <a href="#actividad-7-depuracion-de-la-clase-circle" id="actividad-7-depuracion-de-la-clase-circle"></a>

Al igual que en `Point2D`, incluiremos código principal en el módulo para comprobar el correcto funcionamiento la clase `Circle`.

Añade el siguiente código **(SIN MODIFICAR)** al final del fichero `circle.py`:

{% hint style="danger" icon="skull-crossbones" %}
**NO MODIFICAR ESTE BLOQUE DE CÓDIGO PRINCIPAL**

Su salida se podrá usar el día del examen para evaluaros.
{% endhint %}

<details>

<summary>Código de test</summary>

{% code title="" %}
```python
if __name__ == "__main__":
    print("--- Pruebas del Constructor ---")
    c1 = Circle()
    print(f"[count: {Circle.count()}] c1 = {c1}")
    c2 = Circle(color="blue")
    print(f"[count: {Circle.count()}] c2 = {c2}")
    c3 = Circle(center=Point2D(3, 3))
    print(f"[count: {Circle.count()}] c3 = {c3}")
    c4 = Circle(radius=4)
    print(f"[count: {Circle.count()}] c4 = {c4}")
    c5 = Circle(center=Point2D(5, 5), radius=5)
    print(f"[count: {Circle.count()}] c5 = {c5}")
    c6 = Circle("green", Point2D(6, 6), 6)
    print(f"[count: {Circle.count()}] c6 = {c6}")

    print()
    print("--- Pruebas del Destructor ---")
    del(c1) # invocamos destructor __del__
    print(f"[count: {Circle.count()}] del(c1)")
    
    print()
    print("--- Pruebas de Comparación ---")
    c_eq_1 = Circle("red", Point2D(1, 1), 2.0)
    c_eq_2 = Circle("red", Point2D(1, 1), 2.0)
    c_diff = Circle("blue", Point2D(1, 1), 2.0)
    
    print(f"c_eq_1: {c_eq_1}")
    print(f"c_eq_2: {c_eq_2}")
    print(f"c_diff: {c_diff}")
    
    print(f"  > c_eq_1 == c_eq_2: {c_eq_1 == c_eq_2}")
    print(f"  > c_eq_1 != c_eq_2: {c_eq_1 != c_eq_2}")
    print(f"  > c_eq_1 == c_diff: {c_eq_1 == c_diff}")
    print(f"  > c_eq_1 != c_diff: {c_eq_1 != c_diff}")
    print(f"  > c_eq_1 == tuple(1,1):  {c_eq_1 == (1,1)}")
    print(f"  > c_eq_1 != tuple(1,1):  {c_eq_1 != (1,1)}")

    print()
    print("--- Pruebas de Getters y Setters ---")
    print(f"c2 antes:\n  > {c2}")
    c2.color = "red"
    c2.center = Point2D(8.0, 8.0)
    c2.radius = 8.0
    print(f"c2 modificado:\n  > {c2}")
    print(f"Valores leidos con getters:")
    print(f"  > color={c2.color}")
    print(f"  > center={c2.center}")
    print(f"  > radius={c2.radius}")

    print()
    print("--- Pruebas de Excepciones ---")
    print("Intentando instanciar Circle con color inválido...")
    try:
        Circle("yellow", Point2D(0,0), 1.0)
    except InvalidFigureError as e:
        print(f"  > Se capturó excepción InvalidFigureError correctamente: {e}")

    print("Intentando instanciar Circle con centro inválido (no Point2D)...")
    try:
        Circle("red", (0, 0), 1.0)
    except TypeError as e:
        print(f"  > Se capturó excepción TypeError correctamente: {e}")

    print("Intentando instanciar Circle con radio no numérico...")
    try:
        Circle("red", Point2D(0, 0), "1.0")
    except ValueError as e:
        print(f"  > Se capturó excepción ValueError correctamente: {e}")

    print("Intentando instanciar Circle con radio negativo...")
    try:
        Circle("red", Point2D(0, 0), -1.0)
    except ValueError as e:
        print(f"  > Se capturó excepción ValueError correctamente: {e}")

    print("Intentando modificar el centro con un valor inválido...")
    try:
        c2.center = (0, 0)
    except TypeError as e:
        print(f"  > Se capturó excepción TypeError correctamente: {e}")

    print("Intentando modificar el radio con un valor no numérico...")
    try:
        c2.radius = "2.0"
    except ValueError as e:
        print(f"  > Se capturó excepción ValueError correctamente: {e}")

    print("Intentando modificar el radio con un valor negativo...")
    try:
        c2.radius = -5.0
    except ValueError as e:
        print(f"  > Se capturó excepción ValueError correctamente: {e}")
    
    # Pruebas con conjuntos
    print()
    print("--- Pruebas con Conjuntos (Set) ---")
    lista_circulos = [Circle("red", Point2D(1.0, 1.0), 2.0),
                      Circle("blue", Point2D(3.0, 3.0), 4.0),
                      Circle("red", Point2D(1.0, 1.0), 2.0)]
    
    print(f"Lista original con {len(lista_circulos)} círculos:")
    for i, c in enumerate(lista_circulos):
        print(f"  {i}: {c}")
        
    conjunto_circulos = set(lista_circulos)
    
    print(f"\nConjunto (sin duplicados) con {len(conjunto_circulos)} círculos:")
    for i, c in enumerate(conjunto_circulos):
        print(f"  {i}: {c}")
    
    # Pruebas de número de figuras globales
    print()
    print(f"Figuras vivas (count): {Shape.count()}")
```
{% endcode %}

</details>

Finalmente, úbicate en la raíz del proyecto (`p1`) y ejecuta el módulo `circle` como si fuera un script usando la opción `-m` del intérprete de Python:

```bash
python -m figures.circle
```

Deberías de generar una salida muy similar a esta:

<details>

<summary>Salida esperada</summary>

{% code title="" %}
```python
--- Pruebas del Constructor ---
[count: 1] c1 = Circle(color: red, center: (0.0, 0.0), radius: 1.0)
[count: 2] c2 = Circle(color: blue, center: (0.0, 0.0), radius: 1.0)
[count: 3] c3 = Circle(color: red, center: (3.0, 3.0), radius: 1.0)
[count: 4] c4 = Circle(color: red, center: (0.0, 0.0), radius: 4.0)
[count: 5] c5 = Circle(color: red, center: (5.0, 5.0), radius: 5.0)
[count: 6] c6 = Circle(color: green, center: (6.0, 6.0), radius: 6.0)

--- Pruebas del Destructor ---
[count: 5] del(c1)

--- Pruebas de Comparación ---
c_eq_1: Circle(color: red, center: (1.0, 1.0), radius: 2.0)
c_eq_2: Circle(color: red, center: (1.0, 1.0), radius: 2.0)
c_diff: Circle(color: blue, center: (1.0, 1.0), radius: 2.0)
  > c_eq_1 == c_eq_2: True
  > c_eq_1 != c_eq_2: False
  > c_eq_1 == c_diff: False
  > c_eq_1 != c_diff: True
  > c_eq_1 == tuple(1,1):  False
  > c_eq_1 != tuple(1,1):  True

--- Pruebas de Getters y Setters ---
c2 antes:
  > Circle(color: blue, center: (0.0, 0.0), radius: 1.0)
c2 modificado:
  > Circle(color: red, center: (8.0, 8.0), radius: 8.0)
Valores leidos con getters:
  > color=red
  > center=(8.0, 8.0)
  > radius=8.0

--- Pruebas de Excepciones ---
Intentando instanciar Circle con color inválido...
  > Se capturó excepción InvalidFigureError correctamente: Color 'yellow' no es válido. Usa 'red', 'green' o 'blue'.
Intentando instanciar Circle con centro inválido (no Point2D)...
  > Se capturó excepción TypeError correctamente: El centro debe ser una instancia de Point2D
Intentando instanciar Circle con radio no numérico...
  > Se capturó excepción ValueError correctamente: El radio debe ser un valor numérico
Intentando instanciar Circle con radio negativo...
  > Se capturó excepción ValueError correctamente: El radio no puede ser negativo
Intentando modificar el centro con un valor inválido...
  > Se capturó excepción TypeError correctamente: El centro debe ser una instancia de Point2D
Intentando modificar el radio con un valor no numérico...
  > Se capturó excepción ValueError correctamente: El radio debe ser un valor numérico
Intentando modificar el radio con un valor negativo...
  > Se capturó excepción ValueError correctamente: El radio no puede ser negativo

--- Pruebas con Conjuntos (Set) ---
Lista original con 3 círculos:
  0: Circle(color: red, center: (1.0, 1.0), radius: 2.0)
  1: Circle(color: blue, center: (3.0, 3.0), radius: 4.0)
  2: Circle(color: red, center: (1.0, 1.0), radius: 2.0)

Conjunto (sin duplicados) con 2 círculos:
  0: Circle(color: blue, center: (3.0, 3.0), radius: 4.0)
  1: Circle(color: red, center: (1.0, 1.0), radius: 2.0)

Figuras vivas (count): 11
```
{% endcode %}

</details>

Si la semántica de tu salida es diferente a la esperada, revisa tu implementación.

{% hint style="success" %}
* **Si el contador de figuras "vivas" muestra 7 en lugar de 11:** revisa el orden de las sentencias en el constructor de la clase derivada. Debes invocar el constructor de la clase base **antes** de realizar cualquier otra operación. Si no lo haces, cuando se intenta crear un círculo no válido, el contador no se incrementará (no se ejecuta el constructor de la clase base), pero sí que se decrementará (se ejecuta el destructor de la clase base). El resultado de esto es una resta neta (y artificial) de la cantidad total de figuras.
* **Si el contador de figuras vivas muestra 10 en lugar de 11:** en `Shape` estás comprobando el color antes de contabilizar la figura. Si la comprobación falla, no se llega a incrementar el contador (pero sí se decrementa posteriormente en el destructor)
{% endhint %}
