---
layout: post
title: Tipos de Datos en Java - Primitivos
tags:
  - Java
  - primitivos
  - CamelCase
---

## TIPOS DE DATOS EN JAVA (PRIMITIVOS)

![Variables](/images/variable.png "Variables"){: .center-image}

En java existen dos tipos de datos: **primitivos y de referencia u objeto**, los cuales se pueden almacenar en una variable.

**Variable**
: Es un espacio de memoria al que le asignamos un contenido, puede ser un valor numérico,de tipo carácter o cadena de caracteres

A continuación se explican los tipos de datos primitivos.

##Tipos de datos Primitivos

Java tiene **ocho tipos de dato** incorporado, llamados Tipos Primitivos de Java. Estos ocho tipos de datos representan los bloques de construcción para los objetos de Java, porque todos los objetos de Java son solo una colección compleja de estos tipos de datos primitivo.

| Identificador | Tipo | Rango | Ejemplo
|:--------|:-------:|--------:|--------:|
| boolean   | 16 bits | true o false  |  true   |
| byte   |   8 bit  | -128 a 127   |   15  |
| short  |  16 bits  |  -32,768 a 32,767   |  15,858   |
| int   |  32 bits  | -2,147,483,648 a 2,147,483,647   |  4,132,852   |
| long   |  64 bits  |  9,223,372,036,854,775,808 a +9,223,372,036,854,775,807  |   5,462,895,628,956
  |
| float   | 32 bits  |  1.40129846432481707e-45 a 3.40282346638528860e+38
123  |  .45F   |
| double   |  64 bits  |  4.94065645841246544e-324d a 1.79769313486231570e+308d  |  123.456   |
|char|16 bits |UNICODE|‘a’|

No es necesario memorizar los valores, pero nos sirven de referencia para entender y usar la variable correcta de acuerdo a las necesidades de nuestra aplicación. La manera en la que se obtienen estos valores es aplicando la formula:
    
    -(2<sup>n</sup>)/ 2 para el rango negativo y  [(2<sup>n</sup>)/ 2] - 1 para el positivo donde n es el tipo de valor en bits que la variable utiliza. 















