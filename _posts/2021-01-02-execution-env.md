---
title: Entorno de ejecución
author: Luis E. Fajardo
date: 05-01-2021
edited: 09-01-2021
category: env
layout: post
---

**Contenido**
* TOC
{:toc}

***

### Ejecución de _md2tex_

Al momento de ejecutar **md2tex** puede decidir hacerlo de dos maneras:
- Ejecutar **md2tex** como un archivo ejecutable local.
> Si desea tener **md2tex** como un archivo local puede descargarlo en la sección [Recursos][1]
> y ponerlo en una carpeta de su preferencia. Al momento de ejecutar la aplicación deberá 
> hacerlo de la siguiente manera:
> ```bash
> $ ./md2tex file.md
> ```
- Ejecutar **md2tex** como un archivo ejecutable del sistema.
> Para ejecutar **md2tex** como un archivo de sistema primero deberá descargarlo de la sección 
> [Recursos][1] y luego copiarlo a una carpeta de sistema, por ejemplo: `/usr/local/bin` en 
> sistemas Debian y derivados (seguramente necesitará permisos de __superusuario__ para esta operación).
> ```bash
> $ cp <download folder> /usr/local/bin
> ```
> Ahora podrá ejecutar **md2tex** desde cualquier carpeta del sistema. Ya no será necesario utilizar `./` al inicio del comando.
> ```bash
> $ md2tex file.md
> ```

### Estructura de *md2tex*

Cuando ejecute md2tex se crearán los siguientes archivos y carpetas _(las carpetas puede crearlas usted mismo)_:
- `latex/tex`: Aquí se crearan los archivos `.tex` generados por **md2tex**. Los archivos creados aquí pueden ser tomados para ser compilados por **pdflatex**.
- `latex/images`: Si su documento requiere imagenes deberá ponerlas en esta carpeta, ya que **md2tex** define esta ruta para las imagenes y por lo tanto el compilador **pdflatex** las buscará en esta ruta.

### Compilación de archivos LaTeX desde línea de comandos.

Al ejecutar **pdflatex** se compilarán los archivos `.tex` y obtendrá su documento PDF.
En la línea de comandos puede escribir lo siguiente:

```bash
$ pdflatex <.tex files...>
```

### Compilación de archivos LaTeX con _CMake_.

> - [Que es CMake?][2]{:target="_blank"}

Vaya a la carpeta `latex` de su proyecto y cree un nuevo archivo de texto llamado: `CMakeLists.txt`. 

Asumiendo que tiene un archivo llamado `test.md`, en `CMakeLists.txt` escriba lo siguiente:

```cmake
cmake_minimum_required(VERSION 2.8.4)
project(UseLATEX_DOC NONE)

include(UseLATEX.cmake)

add_latex_document (
    tex/test.tex
    # si su documento contiene imagenes descomente la siguiente línea
    # IMAGE_DIRS images
    # si su documento contiene bibliografía descomente la siguiente línea
    # BIBFILES bib/test.bib
)
```

Dentro de la carpeta `latex` cree una carpeta llamada `build`, aquí será construido su documento PDF.

Antes de compilar con LaTeX, la estructura de archivos debe ser similar a la siguiente:

```
my-folder
├── md2tex
├── test.md
└── latex
    ├── build
    ├── images
    ├── tex
        └── test.tex
    ├── CMakeLists.txt
    └── UseLATEX.cmake
```

Desde la línea de comandos ubíquese en la carpeta `build` y ejecute los siguientes comandos:

```bash
$ cmake ../
$ make
```
Si no ocurre ningún error; su archivo PDF estará dentro de la carpeta `build` _(siguiendo este ejemplo, el archivo deberá llamarse `test.pdf`)_. 

> - Si aún no tiene _cmake_ instalado en su sistema vaya a la sección [Recursos][1] de esta página y busque el apartado **Cmake**.
> - Si no ha descargado **UseLATEX.cmake**, vaya a la sección [Recursos][1] de esta página y busque el apartado **UseLATEX.cmake**.


[1]: /md2tex-docs/resources.html
[2]: https://riptutorial.com/es/cmake