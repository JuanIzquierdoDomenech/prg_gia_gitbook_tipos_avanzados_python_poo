# Clase Rectangle

## Descripción de la clase

El tipo de datos Rectangle, que representa un rectángulo en un espacio bidimensional, estará definido por una clase en Python derivada de la interfaz `Shape`. Será un objeto iterable (implementará los métodos especiales `__iter__` y `__next__`.

### Atributos

<table><thead><tr><th width="133.75">Nombre</th><th width="155.9609375">Tipo</th><th width="130.55078125">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>vertices</code></td><td>de instancia</td><td>protegido</td><td><p>Tupla de 4 elementos de tipo <code>Point2D</code> correspondientes a los vértices v0, v1, v2 y v3 de un rectángulo. </p><p></p><p>¡Atención! Usaremos una tupla de Python y no una lista para garantizar que no se pueden ni añadir ni eliminar vértices.</p></td></tr><tr><td><code>N_VERTICES</code></td><td>de clase/estática</td><td>protegido</td><td>Constante de clase asociada al <code>Rectangle</code> con el número de vértices de un rectángulo (4).</td></tr></tbody></table>

### Métodos

<table><thead><tr><th>Perfil</th><th width="125.7578125">Visibilidad</th><th width="186.04296875">Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>check(vertices)</code></td><td>protegido</td><td>Estático</td><td>Comprueba, a partir de la secuencia provista, si esos vértices conforman un rectángulo válido.</td></tr><tr><td><code>__init__(color, vertices)</code></td><td>-</td><td>Método (constructor) de instancia</td><td><p>Creará un rectángulo. </p><p></p><p>Por defecto, los vértices de la tupla serán v0=(-1,0.5); v1=(1,0.5), v2=(1,-0.5), y v3=(-1,-0.5). </p><p></p><p>Si se proveen vértices que no conforman un rectángulo, lanzará <code>InvalidFigureError</code>.</p></td></tr><tr><td><code>get_vertex(ind)</code></td><td>público</td><td>De instancia</td><td><p>Devuelve el <code>Point2D</code> del rectángulo que ocupa el índice <code>ind</code>. </p><p></p><p>Lanza una excepción estándar <code>IndexError</code> si el índice está fuera del intervalo <code>[0, 3]</code>.</p></td></tr><tr><td><code>__getitem__(ind)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores)</td><td><p>Es una vía puramente Pythonica de invocar <code>get_vertex(ind)</code>. </p><p></p><p>Permite invocar índices con corchetes (por ejemplo, <code>rectangulo[0]</code> a <code>rectangulo[3]</code>).<br></p></td></tr><tr><td><code>vertices()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve la tupla alojada en el atributo protegido <code>vertices</code>.</td></tr><tr><td><code>vertices(vertices)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td><p>Modifica el atributo protegido <code>vertices</code> a partir de una secuencia/tupla de 4 <code>Point2D</code>. </p><p></p><p>Si no conforman un rectángulo válido, lanzará <code>InvalidFigureError</code>.</p></td></tr><tr><td><code>__eq__(other)</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Compara si dos rectángulos son lógicamente iguales (mismo color y vértices).</td></tr><tr><td><code>__hash__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td>Método para insertar y recuperar clases del rectángulo en un <code>set()</code>.</td></tr><tr><td><code>__iter__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores)</td><td>Inicializa un atributo privado que controla la iteración (índice a 0) y se devuelve a sí mismo (el propio objeto) como objeto iterador.</td></tr><tr><td><code>__next__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores)</td><td>Devuelve el siguiente vértice progresivamente usando el índice interno de iteración.</td></tr><tr><td><code>__str__()</code></td><td></td><td>Método de instancia (sobrecarga de operadores, método abstracto en <code>Shape</code>)</td><td><p>Devuelve una cadena de texto representando el rectángulo. </p><p></p><p>Por ejemplo: <code>"Rectangle(color: red, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))"</code>.</p></td></tr></tbody></table>

{% hint style="info" icon="calculator-simple" %}
Por simplicidad, asumiremos que un rectángulo de vértices $$v_0, v_1, v_2, v_3$$ será válido solo si, por un lado, las aristas ​​ tienen la misma longitud, y por otro lado, las aristas $$\overline{v_0v_1}$$​​ y $$\overline{v_2v_3}$$ tienen la misma longitud. Considera hacer uso del método estático `Point2D.distance()`.
{% endhint %}

***

## Actividad 8: Implementación de la clase `Rectangle` <a href="#actividad-8-implementacion-de-la-clase-rectangle" id="actividad-8-implementacion-de-la-clase-rectangle"></a>

Desde `figures`, crea com vim el fichero `rectangle.py` e implementala según la especificación anterior.

***

## Actividad 9: Depuración de la clase `Rectangle`

Guarda este test local en el módulo (recuerda probarlo lanzando `python -m figures.rectangle`):

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
    r1 = Rectangle()
    print(f"[count: {Rectangle.count()}] r1 = {r1}")
    v_personalizados = (Point2D(0.0, 2.0), Point2D(4.0, 2.0), Point2D(4.0, 0.0), Point2D(0.0, 0.0))
    r2 = Rectangle("blue", v_personalizados)
    print(f"[count: {Rectangle.count()}] r2 = {r2}")
    
    print()
    print("--- Pruebas del Destructor ---")
    del(r1) # invocamos destructor __del__
    print(f"[count: {Rectangle.count()}] del(r1)")
    
    print()
    print("--- Pruebas de Comparación ---")
    r_eq_1 = Rectangle("red", v_personalizados)
    r_eq_2 = Rectangle("red", v_personalizados)
    r_diff = Rectangle("blue", v_personalizados)
    
    print(f"r_eq_1: {r_eq_1}")
    print(f"r_eq_2: {r_eq_2}")
    print(f"r_diff: {r_diff}")
    
    print(f"  > r_eq_1 == r_eq_2: {r_eq_1 == r_eq_2}")
    print(f"  > r_eq_1 != r_eq_2: {r_eq_1 != r_eq_2}")
    print(f"  > r_eq_1 == r_diff: {r_eq_1 == r_diff}")
    print(f"  > r_eq_1 != r_diff: {r_eq_1 != r_diff}")

    print()
    print("--- Pruebas de Getters, Setters y Métodos ---")
    print(f"r2 antes:\n  > {r2}")
    r2.color = "red"
    # r2 lo trasladamos artificialmente sumando 1 a todo
    v_mas_uno = (Point2D(1.0, 3.0), Point2D(5.0, 3.0), Point2D(5.0, 1.0), Point2D(1.0, 1.0))
    r2.vertices = v_mas_uno
    print(f"r2 modificado:\n  > {r2}")
    print(f"Valores leidos:")
    print(f"  > color={r2.color}")
    print(f"  > vertices={r2.vertices}")
    print(f"  > area={r2.area()}; perimeter={r2.perimeter()}")

    print()
    print("--- Pruebas de Indexación e Iteración ---")
    print(f"Acceso a r2 por get_vertex(0): {r2.get_vertex(0)}")
    print(f"Acceso a r2 por r2[1] (__getitem__): {r2[1]}")
    
    print("Iterando vértices de r2:")
    for i, v in enumerate(r2):
        print(f"  Iteración {i}: {v}")

    print()
    print("--- Pruebas de Excepciones ---")
    print("Intentando acceder a un índice de vértice inválido (r2[4])...")
    try:
        r2[4]
    except IndexError as e:
        print(f"  > Se capturó excepción IndexError correctamente: {e}")

    print("Intentando instanciar Rectangle con vértices que no forman rectángulo...")
    try:
        v_invalidos = (Point2D(0,0), Point2D(0,0), Point2D(10,5), Point2D(90,90))
        Rectangle("red", v_invalidos)
    except InvalidFigureError as e:
        print(f"  > Se capturó excepción InvalidFigureError correctamente: {e}")

    print("Intentando instanciar Rectangle con una lista en lugar de tupla...")
    try:
        v_lista = [Point2D(0,2), Point2D(4,2), Point2D(4,0), Point2D(0,0)]
        Rectangle("red", v_lista)
    except InvalidFigureError as e:
        print(f"  > Se capturó excepción InvalidFigureError correctamente: {e}")

    print()
    print("--- Pruebas con Conjuntos (Set) ---")
    lista_rectangulos = [Rectangle("red", v_personalizados),
                         Rectangle("blue"),
                         Rectangle("red", v_personalizados)]
    print(f"Lista original con {len(lista_rectangulos)} rectángulos")
    conjunto_rectangulos = set(lista_rectangulos)
    print(f"Conjunto (sin duplicados) con {len(conjunto_rectangulos)} rectángulos")
    
    print()
    print(f"Figuras vivas (count): {Rectangle.count()}")
```
{% endcode %}

</details>

Finalmente, ubícate en la raíz del proyecto (`p1`) y ejecuta el módulo `rectangle` como si fuera un script usando la opción `-m` del intérprete de Python:

```bash
python -m figures.rectangle
```

Deberías de generar una salida muy similar a esta:

<details>

<summary>Salida esperada</summary>

{% code title="" %}
```python
--- Pruebas del Constructor ---
[count: 1] r1 = Rectangle(color: red, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))
[count: 2] r2 = Rectangle(color: blue, vertices: ((0.0, 2.0), (4.0, 2.0), (4.0, 0.0), (0.0, 0.0)))

--- Pruebas del Destructor ---
[count: 1] del(r1)

--- Pruebas de Comparación ---
r_eq_1: Rectangle(color: red, vertices: ((0.0, 2.0), (4.0, 2.0), (4.0, 0.0), (0.0, 0.0)))
r_eq_2: Rectangle(color: red, vertices: ((0.0, 2.0), (4.0, 2.0), (4.0, 0.0), (0.0, 0.0)))
r_diff: Rectangle(color: blue, vertices: ((0.0, 2.0), (4.0, 2.0), (4.0, 0.0), (0.0, 0.0)))
  > r_eq_1 == r_eq_2: True
  > r_eq_1 != r_eq_2: False
  > r_eq_1 == r_diff: False
  > r_eq_1 != r_diff: True

--- Pruebas de Getters, Setters y Métodos ---
r2 antes:
  > Rectangle(color: blue, vertices: ((0.0, 2.0), (4.0, 2.0), (4.0, 0.0), (0.0, 0.0)))
r2 modificado:
  > Rectangle(color: red, vertices: ((1.0, 3.0), (5.0, 3.0), (5.0, 1.0), (1.0, 1.0)))
Valores leidos:
  > color=red
  > vertices=((1.0, 3.0), (5.0, 3.0), (5.0, 1.0), (1.0, 1.0))
  > area=8.0; perimeter=12.0

--- Pruebas de Indexación e Iteración ---
Acceso a r2 por get_vertex(0): (1.0, 3.0)
Acceso a r2 por r2[1] (__getitem__): (5.0, 3.0)
Iterando vértices de r2:
  Iteración 0: (1.0, 3.0)
  Iteración 1: (5.0, 3.0)
  Iteración 2: (5.0, 1.0)
  Iteración 3: (1.0, 1.0)

--- Pruebas de Excepciones ---
Intentando acceder a un índice de vértice inválido (r2[4])...
  > Se capturó excepción IndexError correctamente: Índice de vértice fuera de rango.
Intentando instanciar Rectangle con vértices que no forman rectángulo...
  > Se capturó excepción InvalidFigureError correctamente: Los vértices proporcionados no conforman un rectángulo válido.
Intentando instanciar Rectangle con una lista en lugar de tupla...
  > Se capturó excepción InvalidFigureError correctamente: Los vértices proporcionados no conforman un rectángulo válido.

--- Pruebas con Conjuntos (Set) ---
Lista original con 3 rectángulos
Conjunto (sin duplicados) con 2 rectángulos

Figuras vivas (count): 7
```
{% endcode %}

</details>

Si la semántica de tu salida es diferente a la esperada, revisa tu implementación.
