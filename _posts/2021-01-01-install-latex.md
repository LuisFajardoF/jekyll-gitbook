---
title: Instalación de paquetes LaTeX
author: Luis E. Fajardo
date: 05-01-2021
edited: 08-01-2021
category: env
layout: post
---
***
Los requerimientos para elaborar documentos PDF con **md2tex** son los siguientes:
- Sistema operativo Linux (de preferencia Debian).
- Instalación de paquete `texlive-lang-spanish`.
```sh
# En debian o derivados
$ apt install texlive-lang-spanish
```
- Los paquetes faltantes se instalarán con `tlmgr`.
```sh
# Establecer el repositorio de donde tlmgr descargará los paquetes.
$ tlmgr option repository ftp://tug.org/historic/systems/texlive/2018/tlnet-final
# Para descargar paquetes con tlmgr
$ tlmgr install <package>
```