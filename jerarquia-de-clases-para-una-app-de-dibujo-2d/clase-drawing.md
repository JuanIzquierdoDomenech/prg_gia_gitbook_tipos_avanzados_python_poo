# Clase Drawing

## Descripción de la clase

En las actividades previas hemos modelado una jerarquía de figuras geométricas completas en el paquete `figures`. Para culminar nuestra app de dibujo, crearemos la clase `Drawing`, la cual representará nuestro lienzo y actuará como contenedor de figuras (`Shape`).

Esta clase `Drawing` internamente compondrá una estructura de clase lista general de Python (`list`) instanciada de manera natural para representar nuestro lienzo. El orden de los elementos dictaminará el orden del plano (de frente a fondo).

### Atributos

<table><thead><tr><th width="139.08203125">Nombre</th><th width="166.421875">Tipo</th><th width="145.2109375">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>shapes</code></td><td>de instancia</td><td>privado</td><td>Lista estándar de Python (<code>list</code>) que contendrá objetos de tipo <code>Shape</code>.</td></tr></tbody></table>

### Métodos

<table><thead><tr><th width="243.34765625">Perfil</th><th width="122.453125">Visibilidad</th><th width="142.7734375">Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__()</code></td><td>-</td><td>Método (constructor) de instancia</td><td>Inicializa el dibujo creando una lista vacía de figuras.</td></tr><tr><td><code>add_front(shape)</code></td><td>público</td><td>De instancia</td><td><p>Añade la figura al frente del dibujo (principio de la lista). </p><p></p><p>Emite <code>TypeError</code> si <code>shape</code> no es una instancia de <code>Shape</code>.</p></td></tr><tr><td><code>add_back(shape)</code></td><td>público</td><td>De instancia</td><td><p>Añade la figura al fondo del dibujo (final de la lista). </p><p></p><p>Emite <code>TypeError</code> si <code>shape</code> no es una instancia de <code>Shape</code>.</p></td></tr><tr><td><code>print_all()</code></td><td>público</td><td>De instancia</td><td>Imprime por pantalla la información de todas las figuras, una por línea, de frente a fondo, mostrando el nivel de cada figura.</td></tr><tr><td><code>remove_duplicates()</code></td><td>público</td><td>De instancia</td><td>Elimina las figuras duplicadas del dibujo, conservando únicamente la primera aparición de cada una (de frente a fondo).</td></tr><tr><td><code>get_area_all_circles()</code></td><td>público</td><td>De instancia</td><td>Devuelve la suma del área de todos los círculos presentes en el dibujo exclusivamente.</td></tr><tr><td><code>move_squares(incX, incY)</code></td><td>público</td><td>De instancia</td><td>Traslada exclusivamente los cuadrados del dibujo por sus coordenadas a través del polimorfismo.</td></tr></tbody></table>

{% hint style="info" %}
Para `remove_duplicates()`, recuerda que puedes apoyarte en el uso de conjuntos (`set`) de Python para llevar un registro de las figuras ya vistas e ir filtrando la lista, aprovechando que implementamos adecuadamente `__eq__` y `__hash__` en nuestras clases anteriormente.
{% endhint %}

***

## Actividad 12: Implementación de la clase `Drawing`

Crea con vim un fichero llamado `drawing.py` en el paquete `figures`:

```python
from .shape import Shape
from .circle import Circle
from .square import Square

class Drawing:
    # Completar!
```

Una vez creado el fichero `drawing.py`, limítate a invocar el módulo desde la raíz `p1/` para comprobar que no existan errores de sintaxis en el código que has escrito:

```bash
python -m figures.drawing
```

Si el comando termina silenciosamente (sin devolver nada en consola), ¡enhorabuena, tu código es sintácticamente correcto!&#x20;

El testeo funcional y completo de esta clase, así como de toda la jerarquía en conjunto, se realizará desde el exterior del paquete en la Actividad 14.
