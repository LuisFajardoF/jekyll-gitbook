---
title:  Numeración de páginas
author: Luis E. Fajardo
date: 09-01-2021
edited: 11-01-2021
category: plaintext
layout: post
---

***

La numeración de páginas es otro párametro que puede agregar en **md2tex**. Por defecto, 
**md2tex** enumera las páginas con números arábigos. Para manipular la numeración de páginas
existe el parámetro *pagenumbering*, este puede cambiar el tipo de numeración de páginas.

Los tipos de numeración de páginas que **md2tex** y LaTeX soportan son los siguientes:

Tipo de numeración  | Descripción
:-------------------|:---------------------------
__gooble__          | Quita la numeración de páginas.
__arabic__          | Enumera las páginas con números arábigos.
__roman__           | Enumera las páginas con números romanos en minúscula.
__Roman__           | Enumera las páginas con números romanos en mayúscula.
__alph__            | Enumera las páginas con letras del alfabeto latino en minúscula.
__Alph__            | Enumera las páginas con letras del alfabeto latino en mayúscula.

La sintaxis para la numeración de páginas en **md2tex** puede ser la siguiente:

```md
!--
    pagenumbering: <type_numbering>
--!
```
> Donde `<type_numbering>` puede ser: gooble, arabic, roman, Roman, alph o Alph.

Al incluir este parámetro en su documento, en el código LaTeX generado deberá aparecer: 

```latex
% si el parámetro pagenumbering: Roman
\pagenumbering{Roman}
```

La numeración puede cambiar en cualquier parte del documento; si usted desea cambiar
el tipo de numeración puede escribir `!-- pagenumbering: <type_numbering> --!` en 
cualquier parte del documento.

Adicionalmente, el parámetro *pagenumbering* posee un paramétro _set_. Este parámetro
sirve para reiniciar la numeración de páginas con el número que usted desee.

Por ejemplo, en cualquier parte del documento puede escribir lo siguiente:

```md
!--
    pagenumbering: arabic {
        set: 3
    }
--!
```

El parámetro anterior generará el siguiente código en LaTeX:

```latex
\pagenumbering{arabic}
\setcounter{page}{3}
```

La numeración de páginas aparecerá en el pie de página con orientación centrada.

##### Agregar nueva página

En **md2tex** puede agregar una nueva página haciendo uso de `---` al inicio de una línea.
Esta acción hará uso del comando `\newpage` de LaTeX.

#### Demostración

Asumiendo que tiene un archivo llamado: `test.md` escriba lo siguiente:

```md
!--
    pagenumbering: gobble
--!

## Esta p'agina no est'a numerada.

---

!--
    pagenumbering: Roman
--!

## A partir de esta p'agina se numera con: _Roman_ y la numeraci'on comenzar'a en I. 

---

!--
    pagenumbering: Alph
--!

## A partir de esta p'agina se numera con: _Alph_ y la numeraci'on comenzar'a en A.

---

!--
    pagenumbering: arabic {
        set: 6
    }
--!

## A partir de esta p'agina se numera con: _arabic_ y la numeraci'on comenzar'a en 6.
```

Ejecute **md2tex**:

```bash
$ ./md2tex test.md
```

El código LaTeX generado por **md2tex** es el siguiente:

```latex
\documentclass{article}

\begin{document}
	\pagenumbering{gobble}

	\subsection*{Esta p\'agina no est\'a numerada.}
	\newpage
	\pagenumbering{Roman}

	\subsection*{A partir de esta p\'agina se numera con: \textit{Roman} y la numeraci\'on comenzar\'a en I.}
	\newpage
	\pagenumbering{Alph}

	\subsection*{A partir de esta p\'agina se numera con: \textit{Alph} y la numeraci\'on comenzar\'a en A.}
	\newpage
	\pagenumbering{arabic}
	\setcounter{page}{6}

	\subsection*{A partir de esta p\'agina se numera con: \textit{arabic} y la numeraci\'on comenzar\'a en 6.}
\end{document}
```

Vaya a la carpeta `latex/tex` y ejecute **pdfLaTeX**:

```bash
$ pdflatex test.tex
```

La salida PDF será similar a la siguiente:

- [Ver PDF - Demostración Numeración de Páginas][1]{:target="_blank"}

> Cada vez que se cambie el parámetro _pagenumbering_, la numeración será reiniciada.

[1]: ../assets/pdf/pagenumbering_demo.pdf