# Exportación del paquete

El objetivo de un paquete de Python es encapsular múltiples módulos relacionados y ofrecer un punto de entrada unificado para facilitar su uso a los programadores clientes. Podemos conseguirlo definiendo un fichero `__init__.py` en la raíz del propio paquete. Este fichero se ejecuta automáticamente cuando alguien importa el paquete.

Crea (o edita) el fichero predeterminado `__init__.py` dentro del directorio `figures/`:

{% code title="" %}
```python
from .point2d import Point2D
from .circle import Circle
from .rectangle import Rectangle
from .square import Square
from .drawing import Drawing
from .exceptions import InvalidFigureError

# Definimos explícitamente qué clases se exportarán al hacer 'from figures import *'
# o cuáles estarán disponibles directamente desde el paquete 'figures.'
__all__ = [
    'Point2D',
    'Circle',
    'Rectangle',
    'Square',
    'Drawing',
    'InvalidFigureError'
]
```
{% endcode %}

{% hint style="info" %}
**¡Punto clave de diseño!**&#x20;

Nota que de manera especial que hemos omitido la importación y exportación de la clase **`Shape`**. Esto se hace intencionadamente porque `Shape` es una clase abstracta y de uso interno para la jerarquía.&#x20;

No queremos "exportarla" nativamente porque no está hecha para ser instanciada por un desarrollador externo.
{% endhint %}

Puedes comprobar rápidamente que funciona abriendo el intérprete interactivo de Python desde la raíz `p1/` e importando el paquete para listar su contenido usando la función integrada `dir()`:

{% code title="" %}
```python
>>> import figures
>>> dir(figures)
['Circle', 'Drawing', 'InvalidFigureError', 'Point2D', 'Rectangle', 'Square', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', 'circle', 'drawing', 'exceptions', 'point2d', 'rectangle', 'shape', 'square']
```
{% endcode %}

Notar que las clases que hemos decidido exportar en `__all__` están rápida y limpiamente accesibles en el primer nivel del paquete.
