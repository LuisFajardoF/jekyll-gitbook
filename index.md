---
title:  ''
author: Luis E. Fajardo
date: 05-01-2021
edited: 05-01-2021
layout: home
---

![md2tex logo][1]{:title="Logo md2tex" class="center-image"}

***
Es una herramienta creada con el fin de proporcionar una interfaz simple
para la elaboración de documentos PDF, utilizando Markdown y LaTeX. El
usuario necesita conocer la estructura sintáctica de **md2tex** pero no necesita 
conocer la estructura sintáctica de LaTeX, ya que **md2tex** es quien se encarga 
de generar código LaTeX para una posterior compilación con **pdflatex** y este 
finalmente produce un documento en formato PDF.

La sintaxis de **md2tex** trata de seguir el formato sintáctico de Markdown, aunque
con algunas variantes; así que algunas estructuras sintácticas de **md2tex** no siguen
rigurosamente el formato sintáctico de Markdown. 

Con **md2tex** se abordan las principales funcionalidades de LaTeX, de manera que el usuario
pueda escribir documentación técnica con la calidad que LaTeX proporciona. Se busca que el 
usuario aproveche estas funcionalidades al máximo aunque no tenga conocimientos previos de LaTeX.

**md2tex** requiere de una entrada proporcionada por el usuario, es decir, el usuario crea un nuevo
archivo de texto con la extensión `.md`, escribe texto en el archivo, **md2tex** tratará de interpretar
el contenido del archivo y si no se producen errores generará código LaTeX creando un archivo de extensión
`.tex`, este archivo podrá ser compilado por el compilador **pdflatex** y de esta manera se generará un 
archivo de extensión `.pdf`.

![md2tex control flow][2]{:title="Flujo de ejecución de md2tex" class="center-image"}

La ilustración anterior muestra el flujo de ejecución para generar un archivo PDF con **md2tex**. 

[1]: /assets/images/md2tex.png
[2]: /assets/images/flujo-ejecucion-md2tex.png
