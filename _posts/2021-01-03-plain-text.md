---
title: Procesamiento de Texto Plano
author: Luis E. Fajardo
category: plaintext
date: 05-01-2021
edited: 11-01-2021
layout: post
---
***
**md2tex** interpreta los bloques de texto de manera secuencial, leyendo las líneas
del bloque de texto de izquierda a derecha, de esta manera traslada el texto del archivo de
entrada hacia el archivo de salida.

Algunos elementos que necesitan un procesamiento extra son las tildes y las palabras escritas
dentro de un elemento de énfasis, como ser: negrita, cursiva o subrayado (que se explicarán en 
el apartado **Enfasis en el texto**).

Para las palabras que requieren uso de tilde en **md2tex** se hace uso del caracter _comilla simple_ `'`
antes de la letra a tildar, por ejemplo: `inversión` en **md2tex** deberá ser escrita como _inversi'on_.
A continuación se presenta una demostración de texto plano en **md2tex**:

```md
!--
    cover: default {
        title: El inspector Cambalache y el robo en el museo
        author: Eva Mar'ia Rodr'iguez
    }
--!

Oy'o la conversaci'on y no pod'ia creer lo que pasaba. Tras las cortinas, el inspector 
Cambalache permanec'ia escondido mientras aquellas dos personas tan siniestras planeaban 
el robo de los cuadros m'as valiosos del museo de la ciudad. El pobre inspector estaba 
muerto de miedo, y no sab'ia qu'e hacer. As'i que esper'o a que los ladrones se marcharan 
para salir de su escondite y avisar a sus compa~neros de la comisar'ia para que evitaran 
el robo. Pensar'eis que el inspector Cambalache era un poco cobarde. La verdad es que s'i, 
pero 'el se defend'ia diciendo que era una persona prudente y que pensaba bien las cosas 
antes de actuar.
```
Puede guardar el código anterior en un archivo, por ejemplo: `test.md`.
Si **md2tex** se encuentra en una carpeta local puede ejecutarlo con el siguiente comando:
```bash
$ ./md2tex test.md
```
El archivo LaTeX generado por md2tex es el siguiente:

```latex
\documentclass{article}

\begin{document}
	\title{El inspector Cambalache y el robo en el museo}
	\author{Eva Mar\'ia Rodr\'iguez}
	\maketitle
	Oy\'o la conversaci\'on y no pod\'ia creer lo que pasaba. Tras las cortinas, el inspector 
	Cambalache permanec\'ia escondido mientras aquellas dos personas tan siniestras planeaban 
	el robo de los cuadros m\'as valiosos del museo de la ciudad. El pobre inspector estaba 
	muerto de miedo, y no sab\'ia qu\'e hacer. As\'i que esper\'o a que los ladrones se marcharan 
	para salir de su escondite y avisar a sus compa\~neros de la comisar\'ia para que evitaran 
	el robo. Pensar\'eis que el inspector Cambalache era un poco cobarde. La verdad es que s\'i, 
	pero \'el se defend\'ia diciendo que era una persona prudente y que pensaba bien las cosas 
	antes de actuar.
\end{document}
```

El archivo anterior se encontrará en la carpeta `/latex/tex`, ahí aparecerá como `test.tex`.
Para compilar el archivo con **pdflatex** desde la terminal escriba lo siguiente:

```bash
$ pdflatex test.tex
```

El comando `pdflatex` compilará el archivo `test.tex` y generará 3 nuevos archivos:

```
tex
├── test.aux
├── test.log
└── test.pdf
```

A continuación se explica un poco acerca de los archivos `.aux` y `.log`:

- **aux**: sirve para gestionar las referencias cruzadas (\ref) y las citas bibliográficas (\cite), entre 
otras cosas. En general, guarda la información que ha de pasarse de un proceso de compilación a otro.
- **log**: aquí se guarda la información sobre el proceso de compilación, las advertencias, los errores, 
los paquetes utilizados con su respectiva versión y tal. Es especialmente útil si nos falla al crear el 
documento y no sabemos por qué _(Tomado de: [Una nota sobre los archivos auxiliares][1]{:target="_blank"})_.


El archivo `test.pdf` puede abrirlo con su lector de archivos PDF. El resultado será similar al
siguiente:

- [Ver PDF - Demostración de Texto Plano][2]{:target="_blank"}

> Debido a limitaciones de la herramienta no se soportan caracteres en formato UTF-8.


[1]: https://ondiz.github.io/cursoLatex/Contenido/Ap1.Auxiliares.html
[2]: ../assets/pdf/plain_text_demo.pdf
