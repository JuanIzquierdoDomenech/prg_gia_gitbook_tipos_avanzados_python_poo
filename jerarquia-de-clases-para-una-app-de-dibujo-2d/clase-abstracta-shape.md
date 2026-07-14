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

# Clase abstracta Shape

## Descripción de la interfaz <a href="#descripcion-de-la-interfaz" id="descripcion-de-la-interfaz"></a>

Vamos a describir los métodos que conformarán la interfaz (clase base) `Shape`. Esta clase determinará un conjunto de operaciones básicas que se pueden realizar sobre una figura concreta. `Shape` será una **clase abstracta**, por lo que **no será instanciable directamente**, pero definirá la firma de los métodos que sus herencias deben obligatoriamente implementar.

A fin de obligar a que las clases que hereden de `Shape` implementen los métodos abstractos definidos en `Shape`, haremos uso del módulo integrado `abc` (Abstract Base Classes), tal y como vimos en teoría. En concreto, importaremos la clase `ABC` y el decorador `@abstractmethod`, haciendo que, por un lado, la clase `Shape` herede de `ABC`, y por otro, que los métodos abstractos estén decorados con `@abstractmethod`.

### Atributos

<table><thead><tr><th width="112.76171875">Nombre</th><th width="128.40234375">Tipo</th><th width="119.24609375">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>color</code></td><td>de instancia</td><td>protegido</td><td><p>Color de la figura (string). </p><p></p><p>Solo podrá ser uno de estos tres valores: "red", "green", "blue".</p></td></tr><tr><td><code>count</code></td><td>estático</td><td>privado</td><td><p>Contabilizará el número total de figuras "vivas" (instancias activas). </p><p></p><p>Cada vez que se crea una figura, se incrementa. </p><p></p><p>Cada vez que se elimina (o se recolecta), debe decrementarse.</p></td></tr></tbody></table>

### Métodos

<table><thead><tr><th width="206.96484375">Perfil</th><th width="125.00390625">Visibilidad</th><th width="164.2421875">Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__(color)</code></td><td>-</td><td>Método (constructor) de instancia</td><td><p>Crea una figura del color especificado. Por defecto, el color es "red". </p><p></p><p>Lanzará nuestra excepción <code>InvalidFigureError</code> si el color proporcionado no es válido (<em>tip: mejor delega esa gestión en la propiedad setter</em>). </p><p></p><p>Incrementa el contador global de figuras.</p></td></tr><tr><td><code>__del__()</code></td><td>-</td><td>Método (destructor) de instancia</td><td><p>Decrementa el contador global de figuras. </p><p></p><p>Se llamará automáticamente cuando el recolector de basura de Python elimine una figura de memoria.</p></td></tr><tr><td><code>color()</code></td><td>público</td><td>Propiedad consultora de instancia</td><td>Devuelve el color de relleno de la figura.</td></tr><tr><td><code>color(new_color)</code></td><td>público</td><td>Propiedad modificadora de instancia</td><td><p>Cambia el color de relleno de la figura.</p><p></p><p>Lanzará la excepción <code>InvalidFigureError</code> si el color no es <code>"red"</code>, <code>"green"</code>, o <code>"blue"</code>.</p></td></tr><tr><td><code>count()</code></td><td>público</td><td>Método consultor estático</td><td>Devuelve el valor actual de <code>count</code>.</td></tr><tr><td><code>area()</code></td><td>público</td><td>Método de instancia abstracto</td><td>Toda figura concreta deberá implementar el cálculo de su área.</td></tr><tr><td><code>perimeter()</code></td><td>público</td><td>Método de instancia abstracto</td><td>Toda figura concreta deberá implementar el cálculo de su perímetro.</td></tr><tr><td><code>translate(incX, incY)</code></td><td>público</td><td>Método de instancia abstracto</td><td>Toda figura concreta deberá implementar el desplazamiento de la figura sobre el espacio de representación, aplicando los incrementos de X e Y proporcionados.</td></tr><tr><td><code>__eq__(other)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores) abstracto</td><td><p>Comprueba si dos figuras son lógicamente iguales. </p><p></p><p>Toda figura concreta deberá implementarla.</p></td></tr><tr><td><code>__ne__(other)</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores)</td><td><p>Compara si dos figuras son lógicamente diferentes delegando convencionalmente en <code>__eq__</code>. </p><p></p><p>Notad que es un método concreto que heredarán todas las clases derivadas.</p></td></tr><tr><td><code>__hash__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores) abstracto</td><td><p>Hace que el objeto sea "hasheable" (p.ej., uso en operaciones de conjuntos, uso como clave en diccionarios). </p><p></p><p>Toda figura concreta deberá implementarla.</p></td></tr><tr><td><code>__str__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores) abstracto</td><td>Toda figura concreta deberá implementar su representación en cadena de texto.</td></tr><tr><td><code>__repr__()</code></td><td>-</td><td>Método de instancia (sobrecarga de operadores)</td><td><p>Delega convencionalmente en <code>__str__</code>. </p><p></p><p>Notad que es un método concreto: estamos estipulando que, en todas las clases derivadas, <code>__repr__</code> delegará en su implementación de <code>__str__</code> concreta.</p></td></tr></tbody></table>

{% hint style="warning" icon="hand-point-ribbon" %}
Recuerda dotar, si procede, de los decoradores integrados de Python necesarios sobre los anteriores métodos para que actúen como:

* propiedades de instancia (`@property`)
* modificadores de propiedades de instancia (`@<propiedad>.setter`)
* métodos estáticos (`@staticmethod`)
* métodos de clase (`@classmethod`)
* métodos abstractos (`@abstractmethod`)

Además, recuerda añadir los parámetros automáticos `self` y `cls` donde corresponda.

Además, recuerda la nomenclatura para indicar métodos 'públicos', 'protegidos' y 'privados' en Python.
{% endhint %}

{% hint style="info" %}
La implementación del método concreto `__ne__(other)` delegará en el método abstracto `__eq__(other)`, pero ten en cuenta que antes deberá devolver `True` ("son figuras diferentes") si `self` y `other` son instancias de dos clases distintas (son de tipo diferente). Usa `type()` para ello. No podemos usar `isinstance()` aquí, porque `self` puede ser potencialmente una instancia de cualquier clase derivada de `Shape`: `Circle`, `Square`, etc.
{% endhint %}

***

## Actividad 5: Implementación de la clase `Shape` <a href="#actividad-5-implementacion-de-la-clase-shape" id="actividad-5-implementacion-de-la-clase-shape"></a>

Desde el paquete `figures`, crea con vim el módulo `shape.py`. En Python, para dotar de comportamiento abstracto a una clase, debemos heredar de `ABC` e importar el decorador `@abstractmethod`. Además, necesitaremos importar la excepción personalizada que definimos en la página [Excepciones definidas por el usuario](excepciones-definidas-por-el-usuario.md).

```python
from abc import ABC, abstractmethod
from .exceptions import InvalidFigureError # notar el punto de delante!

class Shape(ABC):
    # Completar!
```

Asegúrate de comprobar que no existan errores de sintaxis o indentación, ejecutando el módulo `shape` como un script, con `python -m figures.shape` desde el directorio `p1`.

Finalmente, añade un bloque de test en el `__main__` que intente instanciar la clase `Shape`, para comprobar que esto no es posible: debería generar una excepción `TypeError`.

Vuelve a ejecutar el módulo para comprobarlo. Tu salida debería ser similar a la siguiente:

{% code title="" %}
```bash
Traceback (most recent call last):
    ...
TypeError: Can't instantiate abstract class Shape without an implementation for abstract methods '__eq__', '__hash__', '__str__', 'area', 'perimeter', 'translate'
```
{% endcode %}
