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

# Excepciones definidas por el usuario

## Motivación <a href="#motivacion" id="motivacion"></a>

En Python, el manejo de errores se realiza mediante **excepciones**. La librería estándar proporciona un amplio abanico de excepciones integradas, como `ValueError`, `TypeError` o `IndexError`. Muchas veces es suficiente con hacer uso de dichas excepciones. Por ejemplo, acceder a un elemento fuera del rango de una tupla o lista lanza de forma natural un `IndexError`.

Sin embargo, cuando desarrollamos aplicaciones complejas orientadas a objetos, suele ser una buena práctica de diseño definir **excepciones propias** que modelen errores específicos de nuestro dominio del problema. Esto permite a los usuarios de nuestro código capturar y gestionar los errores de forma mucho más precisa, separando los fallos semánticos de nuestra lógica de negocio de los errores genéricos de programación.

## Definición de una excepción propia <a href="#definicion-de-una-excepcion-propia" id="definicion-de-una-excepcion-propia"></a>

En Python, para definir una excepción propia, basta con crear una nueva clase que herede de la clase base `Exception` (o de alguna de sus derivadas).

***

## Actividad 2: Creación de la excepción `InvalidFigureError` <a href="#actividad-2-creacion-de-la-excepcion-invalidfigureerror" id="actividad-2-creacion-de-la-excepcion-invalidfigureerror"></a>

Dentro de nuestro directorio de trabajo `p1`, y concretamente en el paquete `figures`, nos interesa definir una excepción propia que nos servirá para indicar que se está intentando instanciar o modificar una figura geométrica con parámetros inválidos (p.ej., vértices que no conforman un rectángulo o cuadrado, o colores no permitidos).

Desde nuestro directorio de trabajo de la práctica (`p1`), crea con vim el módulo `exceptions.py`. Es decir, deberás ejecutar:

```bash
vim figures/exceptions.py
```

Dentro de vim, añade el siguiente contenido:

```python
class InvalidFigureError(Exception):
    """
    Excepción lanzada cuando una figura intenta instanciarse o
    tales como colores no permitidos o vértices incorrectos.
    """
    pass
```

Añade a continuación, en el fichero `exceptions.py`, un bloque de código principal (`if __name__ == "__main__"`) para testear la excepción creada. Para ello, lanza explícitamente la excepción usando `raise` (donde se crea una instancia de la clase `InvalidFigureError`) dentro de un bloque `try` y captúrala inmediatamente a continuación usando el bloque `except`, mostrando por pantalla el mensaje de error capturado.

{% code title="" %}
```python
if __name__ == ????:
    try:
        raise ???
    except ???:
        print(????)
```
{% endcode %}

Finalmente, sin moverte de la raíz del proyecto (directorio `p1`), ejecuta el módulo `exceptions` como si fuera un script usando la opción `-m` (_"run library module as a script"_) del intérprete de Python para comprobar que la excepción se lanza y se captura correctamente:

```bash
python -m figures.exceptions
```

{% hint style="warning" icon="lightbulb-exclamation-on" %}
A lo largo de las siguientes actividades de esta práctica, **deberás importar y lanzar (`raise`) esta excepción** cada vez que detectes una violación de las reglas semánticas de las figuras. Sin embargo, para errores de programación comunes o asociados a tipos integrados, deberás seguir empleando excepciones estándar adecuadas (como `IndexError`).
{% endhint %}
