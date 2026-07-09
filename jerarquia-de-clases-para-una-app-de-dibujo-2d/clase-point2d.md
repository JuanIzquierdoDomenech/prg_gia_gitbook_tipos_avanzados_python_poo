# Clase Point2D

El tipo de datos `Point2D`, que representa un punto bidimensional en el espacio cartesiano, estará definido por una clase en Python de igual nombre.

### Atributos <a href="#atributos" id="atributos"></a>

Dado que en Python no declaramos los atributos previamente como en C++, estos se inicializarán dinámicamente en el constructor.

| Nombre | Tipo         | Visibilidad | Descripción                       |
| ------ | ------------ | ----------- | --------------------------------- |
| `x`    | de instancia | público     | Coordenada x del punto (`float`). |
| `y`    | de instancia | público     | Coordenada y del punto (`float`). |

### Métodos

<table><thead><tr><th width="172.34375">Perfil</th><th width="113.47265625">Visibilidad</th><th>Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__(x, y)</code></td><td>-</td><td>Método especial (constructor) de instancia</td><td>Por defecto, las coordenadas <code>x</code> e <code>y</code> tomarán el valor 0. Deberá comprobar que los valores proporcionados son floats o se pueden convertir a float. De lo contrario, lanzará una excepción <code>ValueError</code>.</td></tr><tr><td><code>distance(a, b)</code></td><td>público</td><td>de clase</td><td></td></tr><tr><td><code>__eq__(other)</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__ne__(other)</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__hash__()</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__getitem__(key)</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__setitem__(key, value)</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__str__()</code></td><td>-</td><td></td><td></td></tr><tr><td><code>__repr__()</code></td><td>-</td><td></td><td></td></tr></tbody></table>

{% hint style="info" %}

{% endhint %}

{% hint style="info" %}

{% endhint %}

{% hint style="info" %}

{% endhint %}

{% hint style="info" %}

{% endhint %}

***

## Actividad 3: Implementación de la clase Point2D <a href="#actividad-3-implementacion-de-la-clase-point2d" id="actividad-3-implementacion-de-la-clase-point2d"></a>

Desde nuestro directorio de trabajo de la práctica (`p1`), crea con vim el módulo `point2d.py`. Es decir, deberás ejecutar:

<a class="button secondary">Copiar</a>

```
vim figures/point2d.py
```

A continuación, dentro de vim, añade el siguiente contenido y completa la implementación:

<a class="button secondary">Copiar</a>

```
import math

class Point2D:
    # Completar!
```

Recuerda ir comprobando la sintaxis de tu código ejecutando el módulo como un script `python3 -m figures.point2d`.

***

## Actividad 4: Depuración de la clase Point2D <a href="#actividad-4-depuracion-de-la-clase-point2d" id="actividad-4-depuracion-de-la-clase-point2d"></a>

Vamos a probar la clase `Point2D` que acabamos de implementar. Para evitar que el código de prueba se ejecute cuando importemos esta clase desde otros ficheros de la aplicación, envolveremos las pruebas en el bloque estandarizado `if __name__ == "__main__"`.

Añade el siguiente código **(SIN MODIFICAR)** al final del fichero `point2d.py`:

**NO MODIFICAR ESTE BLOQUE DE CÓDIGO PRINCIPAL**

Su salida se podrá usar el día del examen para evaluaros.

<details>

<summary>Código de test</summary>

{% code title="" %}
```python
if __name__ == "__main__":
    a = Point2D(0, 0.0)
    b = Point2D(1.0, 1)

    print(f"a = {a}; b = {b}")
    print(f"> d(a,b) = {Point2D.distance(a, b):.5f}") # ~1.41421
    print(f"> a==b --> {a == b}") # False
    print(f"> a!=b --> {a != b}") # True

    print()
    a = Point2D(1, 1) # re-instanciamos a con el valor de b
    print(f"a = {a}; b = {b}")
    print(f"> d(a,b) = {Point2D.distance(a, b)}") # 0.0
    print(f"> a==b --> {a == b}") # True
    print(f"> a!=b --> {a != b}") # False

    print()
    print(f"> a == tuple(1,1) --> {a == (1,1)}")
    print(f"> a != tuple(1,1) --> {a != (1,1)}")

    print()
    print("Intentando crear un Point2D con valores no numéricos...")
    try:
        Point2D("a", 0)
    except ValueError:
        print("> Se capturó excepción ValueError correctamente")
    try:
        Point2D(0, "CERO")
    except ValueError:
        print("> Se capturó excepción ValueError correctamente")

    # Prueba de conjuntos (sets)
    print()
    lista_puntos = [Point2D(1, 1), Point2D(2, 1), Point2D(1, 2),
                    Point2D(2, 2), Point2D(1, 1), Point2D(2, 2)]
    print(f"Lista de {len(lista_puntos)} puntos: {lista_puntos}") # 6 puntos
    conjunto_puntos = set(lista_puntos)
    print(f"> Conjunto de {len(conjunto_puntos)} puntos únicos de la lista: {conjunto_puntos}") # 4 puntos

    # Pruebas de indexadores
    print()
    p = Point2D(5.0, 10.0)
    print(f"p = {p}")
    print(f"> p[0] = {p[0]};\n> p['x'] = {p['x']}\n> p['X'] = {p['X']}")
    print(f"> p[1] = {p[1]};\n> p['y'] = {p['y']}\n> p['Y'] = {p['Y']}")
    p[0] = 7.0
    p['y'] = -3.0
    print(f"Tras modificar con indexadores:\n> p = {p}")
    print()
    print("Intentando acceder a una clave inválida de p...")
    try:
        print(p[2])
    except KeyError:
        print("> Se capturó excepción KeyError correctamente")
```
{% endcode %}

</details>

Finalmente, ubícate en la raíz del proyecto (`p1`) y ejecuta el módulo `point2d` como si fuera un script usando la opción `-m` del intérprete de Python:

```bash
python -m figures.point2d
```

Deberías de generar una salida muy similar a esta:

<details>

<summary>Salida esperada</summary>

{% code title="" %}
```bash
a = (0.0, 0.0); b = (1.0, 1.0)
> d(a,b) = 1.41421
> a==b --> False
> a!=b --> True

a = (1.0, 1.0); b = (1.0, 1.0)
> d(a,b) = 0.0
> a==b --> True
> a!=b --> False

> a == tuple(1,1) --> False
> a != tuple(1,1) --> False

Intentando crear un Point2D con valores no numéricos...
> Se capturó excepción ValueError correctamente
> Se capturó excepción ValueError correctamente

Lista de 6 puntos: [(1.0, 1.0), (2.0, 1.0), (1.0, 2.0), (2.0, 2.0), (1.0, 1.0), (2.0, 2.0)]
> Conjunto de 4 puntos únicos de la lista: {(1.0, 1.0), (1.0, 2.0), (2.0, 1.0), (2.0, 2.0)}

p = (5.0, 10.0)
> p[0] = 5.0;
> p['x'] = 5.0
> p['X'] = 5.0
> p[1] = 10.0;
> p['y'] = 10.0
> p['Y'] = 10.0
Tras modificar con indexadores:
> p = (7.0, -3.0)

Intentando acceder a una clave inválida de p...
> Se capturó excepción KeyError correctamente
```
{% endcode %}

</details>

Si la semántica de tu salida es diferente a la esperada, revisa tu implementación.
