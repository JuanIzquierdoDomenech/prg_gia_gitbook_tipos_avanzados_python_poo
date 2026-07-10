# Prueba de la aplicación completa

A diferencia de las demás clases que hemos desarrollado encapsuladas en el paquete `figures`, crearemos este fichero de pruebas **en el directorio principal `p1/`**, es decir, un nivel **por encima** de `figures/`. Este script actuará como el punto de entrada de nuestra app.

Crea un fichero llamado `app.py`. Gracias a nuestro nuevo `__init__.py`, comprobarás que la importación es muy sencilla y limpia, pudiendo hacerla en una sola línea `from` sin necesidad de especificar el nombre de los módulos (ficheros `.py`) internos.

{% code title="" %}
```python
from figures import Circle, Rectangle, Square, Point2D, Drawing

def main():
    pass
    # Completar!

if __name__ == '__main__':
    main()
```
{% endcode %}

Para ejecutar el script interactivo, ejecuta, desde la raíz del proyecto `p1`:

{% code title="" %}
```bash
python app.py
```
{% endcode %}

Completa el código de la función `main()` para que genere una salida muy parecida a la siguiente:

{% hint style="info" icon="backward" %}
Esto de llama hacer **ingeniería inversa**.
{% endhint %}

{% code title="" %}
```bash
--- Inicializando el dibujo con un Círculo y un Cuadrado ---

--- Mostrando todo el contenido ---
0: Circle(color: red, center: (0.0, 0.0), radius: 1.0)
1: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))

--- Introduciendo duplicados intencionadamente ---

--- Mostrando todo el contenido (con duplicados) ---
0: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
1: Circle(color: red, center: (0.0, 0.0), radius: 1.0)
2: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
3: Circle(color: red, center: (0.0, 0.0), radius: 1.0)

--- Eliminando duplicados ---

--- Mostrando todo el contenido (limpio) ---
0: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
1: Circle(color: red, center: (0.0, 0.0), radius: 1.0)

--- Añadiendo un Rectángulo y un Círculo ---

--- Mostrando todo el contenido ---
0: Rectangle(color: green, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))
1: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
2: Circle(color: red, center: (0.0, 0.0), radius: 1.0)
3: Circle(color: blue, center: (2.5, 2.5), radius: 2.0)

--- Añadiendo un Círculo y un Cuadrado ---

--- Mostrando todo el contenido ---
0: Square(color: blue, vertices: ((2.0, 4.0), (4.0, 4.0), (4.0, 2.0), (2.0, 2.0)))
1: Rectangle(color: green, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))
2: Square(color: blue, vertices: ((-1.0, 1.0), (1.0, 1.0), (1.0, -1.0), (-1.0, -1.0)))
3: Circle(color: red, center: (0.0, 0.0), radius: 1.0)
4: Circle(color: blue, center: (2.5, 2.5), radius: 2.0)
5: Circle(color: green, center: (-1.0, 5.0), radius: 1.5)

--- Calculando área total de círculos ---
  > Suma de áreas: 22.77655

--- Trasladando todos los cuadrados con incremento (+10, +10) ---

--- Mostrando contenido tras la traslación ---
0: Square(color: blue, vertices: ((12.0, 14.0), (14.0, 14.0), (14.0, 12.0), (12.0, 12.0)))
1: Rectangle(color: green, vertices: ((-1.0, 0.5), (1.0, 0.5), (1.0, -0.5), (-1.0, -0.5)))
2: Square(color: blue, vertices: ((9.0, 11.0), (11.0, 11.0), (11.0, 9.0), (9.0, 9.0)))
3: Circle(color: red, center: (0.0, 0.0), radius: 1.0)
4: Circle(color: blue, center: (2.5, 2.5), radius: 2.0)
5: Circle(color: green, center: (-1.0, 5.0), radius: 1.5)
```
{% endcode %}

{% hint style="danger" %}
**SE ESCRUPULOSO CON REPRODUCIR ESTA SALIDA**

Esta salida (y el código fuente que la genera) se podría revisar el día del examen para evaluaros.
{% endhint %}

Si has llegado hasta aquí, ¡enhorabuena! Has completado la Práctica 1!
