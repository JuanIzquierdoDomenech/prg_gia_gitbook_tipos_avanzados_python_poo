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

# Preparación del entorno

## Actividad 1. Crea el directorio de la práctica y inicializa el paquete `figure` <a href="#actividad-1.-crea-el-directorio-de-la-practica-y-inicializa-el-paquete-figure" id="actividad-1.-crea-el-directorio-de-la-practica-y-inicializa-el-paquete-figure"></a>

Abre una terminal Bash de Linux y sitúate en el directorio donde quieras mantener organizadas las prácticas de la asignatura (dentro de `$HOME/W` si estás en el escritorio DSIC-Linux de Polilabs). A continuación, crea el directorio de la práctica actual y sitúate en él:

```bash
mkdir p1
cd p1
```

{% hint style="info" icon="folder-open" %}
Tened en cuenta que `p1` será nuestro directorio de trabajo de partida durante toda la práctica. Todos los ficheros y paquetes deberán estar organizados a partir de este directorio.
{% endhint %}

Ahora vamos a inicializar el paquete `figures`. Crea el subdirectorio del paquete, e incluye en él un fichero `__init__.py` vacío con el comando `touch` para que Python lo reconozca como un paquete importable.

```bash
mkdir figures
touch figures/__init__.py
```

Más adelante crearemos los módulos que conformarán el paquete `figures` y finalmente modificaremos el fichero `__init__.py` para establecer qué clases se importan por defecto. Por ahora, nos aseguramos de que el paquete existe y es reconocible por Python:

```bash
python -c "import figures; print(figures)"
```
