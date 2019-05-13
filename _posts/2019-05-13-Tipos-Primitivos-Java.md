---
layout: post
title: Tipos de Datos en Java - Primitivos
tags:
  - Java
  - primitivos
  - CamelCase
---

![Data types](/images/java-data-types.png "Data types"){: .center-image}




En java existen dos tipos de datos: **primitivos y de referencia u objeto**, los cuales se pueden almacenar en una variable.

**Variable**
: Es un espacio de memoria al que le asignamos un contenido, puede ser un valor numérico,de tipo carácter o cadena de caracteres

A continuación se explican los tipos de datos primitivos

##Tipos de datos Primitivos

Java tiene **ocho tipos de dato** incorporado, llamados **Tipos Primitivos de Java**. Estos ocho tipos de datos representan los bloques de construcción para los objetos de Java, porque todos los objetos de Java son solo una colección compleja de estos tipos de datos primitivo.

| **Identificador** | **Tipo** | **Rango** | **Ejemplo**
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
    
    Rango Negativo
    -(2^n)/2
    Rango Positivo
    [(2<sup>n</sup>)/ 2] - 1  
    donde n = valor en bits que la variable utiliza

Por ejemplo para obtener los rangos del tipo entero byte: 

    -(2<sup>n</sup>)/ 2 → -(2<sup>8</sup>)/2 → -256/2 → -128
	[(2<sup>n</sup>)/ 2] - 1 → [256/2] – 1 → 128 – 1 → 127

Cuando  un número es representado en nuestro código se le llama **literal**. Por defecto, **Java asume que se define una variable del tipo int como literal**. En el siguiente ejemplo, el número es mayor que  la capacidad de un int.

```java
    long max = 12345679; // NO COMPILA
    double number = 213431; // NO COMPILA
```
En estos casos, debes añadir una letra l para los datos enteros y d para los datos con punto flotante despues de la literal. Se recomienda el uso de mayusculas debido a que estas no se confunde con números.

```java
    long max = 12345679L; // COMPILA
    double number = 213431D; //COMPILA
```

Otra manera de especificar números es **cambiando la base**. Java permite especificar digitos en muchos otros formatos:


* **Octal** (digitos 0-7): Se usa el número 0 como prefijo de la literal, por ejemplo 017.
* **Hexadecimal** (digitos 0-9 y letras A-F): Se usa el número 0 seguido de la letra x o X como prefijo, por ejemplo 0xFF y 0XA3
* **Binario** (Digitos 0-1): Se usa el número 0 seguido de la letra b o B como prefijo, por ejemplo 0b10 y 0B10010

Otra característica de Java es que puedes añadir a tus literales numéricas son los **guiones bajos** (_) para hacerlos más fácil de leer. Puedes añadir guiones bajos en cualquier parte del número, excepto al inicio y al final de este y en los a números con punto decimal, el guión no puede ir ni antes ni después del punto.

```java
    double = _1000.0 // NO COMPILA
	double = 1000.0_; // NO COMPILA
	double notByDecimal = 1000_.00 // NO COMPILA
	Int million = 1_000_000 // COMPILA
	int anotherVarialble = 1_00_0.0_0; // COMPILA

```

## Naming y Camel Case

Al crear nuestras variables debemos tener en consideración algunas reglas básicas:

* Las variables son sensibles a las Mayúsculas y minúsculas
* Deben comenzar con letra, ,$, o _
* Las letras posteriores pueden ser letras, números, $ y _
* Las constantes se escriben en mayúsculas y contienen _ como espacios
* Por convención se debe usar la técnica “Camel Case”
* Upper Camel Case para nombre de clases: NombreDeClase
* Lower Camel Case para variables y metodos








