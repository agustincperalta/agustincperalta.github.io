---
layout: post
title: "Arquitecturas del Núcleo de Sistemas Basados en Conocimiento: Sistemas Expertos "
tags:
  - Expert Sistem
  - Artificial Intelligence
  - Knowledge

---

## Sistemas Expertos


![an image alt text]({{ site.baseurl }}/images/inteligencia_artificial.jpg "an image title")




Los **Sistemas Expertos** son sistemas con un **conocimiento de un dominio en especifico**, con aplicación de conocimiento **teórico y empírico**. El conocimiento experto es una combinación de un entendimiento teórico de un problema y una colección de **reglas heuristicas** de solución de problemas que la experiencia ha mostrado ser efectiva en el dominio.

Los sistemas expertos son construidos obteniendo su conocimiento de **expertos humanos** y codificandolo dentro de una forma que una computadora pueda aplicar a problemas similares.

Es común ver a los sistemas crecer en **colaboración** con expertos en el campo.

El **Ingeniero del conocimiento** es el responsable de implementar este conocimiento en un programa.

El sistema experto **MYCIN** establecido la **metodología de los sistemas expertos contemporáneos**.

Las **desventajas** de los SE son:

1. Dificultad para capturar conocimiento “profundo” de un dominio de problema
2. Falta de robustez y flexibilidad
3. Inhabilidad de proveer explicaciones profundas
4. Dificultad en su verificación
5. Pequeño aprendizaje de la experiencia


Los sistemas expertos son la respuesta al problema de: **conocimiento-intensivo** o **método fuerte**

Los sistemas expertos:

- Soportan inspección de sus procesos de razonamiento, tanto en presentar sus pasos intermedioscomo respondiendo preguntas sobre el proceso de solución
- Permite la fácil modificación del añadido y borrado de habilidades de la base de conocimiento
- Razonan heuristicamente, usando conocimiento (a veces imperfecto) para obtener soluciones útiles
      
Los diseñadores de sistemas expertos a menudo comentan que la **fácil modificación de la base de conocimiento** es un factor mayor en la producción de un programa exitoso.

Una característica más de un sistema experto es su uso de **métodos heuristicos de problema-solución**.

Las **categorías** de los problemas de los sistemas expertos son:

- Interpretación
- Predicción
- Diagnostico
- Diseño
- Planeación
- Monitoreo
- Educación
- Control

## El Diseño de Sistema Expertos basado en Reglas

![Expert System Shell]({{ site.baseurl }}/images/expertsystemshell.png "Expert System Shell")

El usuario interactuá con el sistema por medio de su **interfaz de usuario**, en sus distintas variedades de estilos: pregunta y respuesta, basado en menús, interfaces graficas.

El corazón de el sistema experto es la **Base de Conocimientos** donde el conocimiento está representado en la forma de **reglas Si..entonces…** La base de conocimiento contiene tanto como el conocimiento general como la información de caso en especifico.

El **Motor de Inferencia** aplica el conocimiento a la solución del problema actual, es esencialmente un interprete de la base de conocimiento, realiza el **ciclo de control reconocer-actuar**.

Se mantienen separados el conocimiento del motor de inferencia por muchas razones:
      
    - Manera más natural
    - Enfoque a captura y organización
    - Permite cambios
    - Se puede usar en otros sistemas

Un **shell de sistemas expertos** tiene todos los componentes de la arquitectura, a excepción de la base de conocimientos y los datos de los casos en particular, los cuales están vacíos y pueden ser añadidos para una nueva aplicación

Los **Datos de los Casos en Especifico**: Los hechos, conclusiones, y otra información relevante sobre el caso en consideración.

El **Subsistema de Explicación** permite al programa explicar su razonamiento al usuario.

Muchos sistemas incluyen un **Editor de la Base de Conocimiento**, los cuales ayudan al programador a localizar y corregir **errores en el desempeño del programa**, a menudo accesando a la información dispuesta por el Subsistema de explicación. Además asiste a la **adición de nuevo conocimiento**, ayuda a mantener una **sintaxis de reglas correcta**, y realiza **verificaciones de consistencia** en las actualizaciones de la base de datos.

Shells de Sistemas Expertos: **CLIPS, JESS**.

Aunque la **separación del conocimiento y el control**, la **modularidad de la arquitectura** del sistema de producción, y el uso de un **lenguaje de representación de conocimiento** adecuado ayudan, la **adquisición y la formalización del conocimiento** del domino continua siendo una tarea difícil.

## TIPOS DE SISTEMAS EXPERTOS (MÉTODOS DE INFERENCIA)

> Clausulas de Horn: Cláusulas en las que, como máximo, hay un único literal positivo, en lógica proposicional son una fórmula lógica es una cláusula de Horn si es una cláusula (disyunción de literales) con, como máximo, un literal positivo. Se llaman así por el lógico Alfred Horn.

Inferencia: Se puede llevar a cabo de forma bastante simple con el Encadenamiento hacia Adelante y el Encadenamiento hacia atrás. Esta es la base de los lenguajes de programación lógicos

Complejidad: La complejidad en tiempo es de orden lineal con respecto al tamaño de la base de conocimiento.

ESTRATEGIAS DEL MOTOR DE INFERENCIA
Existen dos estrategias puras mediante las cuales el motor de inferencia realiza inferencia sobre la información que posee:

* Orientada por el objetivo: Conocida como búsqueda hacia átras (Backward Chaining)
* Orientada por los Datos: Conocida por búsqueda hacia adelante (Forward Chaining)

En ambos casos se tienen datos iniciales y un objetivo a verificar

Fordward Chaining o encadenamiento hacia adelante (Orientada por los Datos)

La estrategia orientada por los datos toma como origen de la inducción a los datos y a partir de estos intenta construir un conjunto que contenga como elemento al objetivo, para hacer esto usa las reglas como operadores de pertenencia al conjunto Memoria de Trabajo. Va agregando conclusiones a la misma, si todos los literales de una premisa se cumplen. Se continúa hasta que se obtiene la conclusión a comprobar o si no se puede hacer más inferencias.

Es un método impulsado por datos de lograr una meta particular desde una base de conocimiento y una conjunto de reglas de inferencia. Las reglas de inferencia son aplicadas por comparar hechos a los antecedentes de las relaciones de consecuencia y la base de conocimientos

La aplicación de las reglas de inferencia resulta con nuevo conocimiento (de la consecución de las relaciones emparejadas), las cuales son añadidas a la base de conocimiento


Backward Chaining o Encadenamiento Hacia Átras (Orientada por el Objetivo)

Toma como origen de la inferencia al objetivo y a partir de este intenta construir un árbol hacia los datos conocidos, estando las distintas reglas, asociadas a las ramas del mismo. 

El objetivo a satisfacer es el nodo principal y los conjuntos de nodos a partir de los cuales se puede deducir reciben el nombre de conjuntos de soporte del objetivos.

1. Se parte del literal a demostrar
2. Se busca alguna cláusula donde dicho literal sea la conclusión
3. Se mira si sus premisas son verdad
4. Si son verdades, se ha terminado
5. Si no lo son, se repite la operación para cada una de esas premisas

Se procede de forma recursiva hasta que todas las premisas sean satisfechas

Razonamiento Dirigido por Objetivos

Ventajas: 
consume menos tiempo y espacio que el encadenamiento hacia delante porque sólo trata las cláusulas y símbolos relevantes

Desventajas: 
Agrega menos información a la base de conocimiento, ya que se centra en la conclusión a demostrar

Implementación: de forma similar alas búsquedas YO

16 Artificial Intelligence As Empirical Enquiry
16. 1 Artificial Intelligence: A Revised Definition

	IA es el estudio de los mecanismos detrás del comportamiento inteligente a través de la construcción y evaluación de artefactos diseñados para representar estos mecanismos.


16.1.4 Modelos Probabilistas y Tecnología Estocástica

Estocástico: Se denomina estocástico (del latín stochasticus, “habil en conjeturar”) al sistema cuyo comportamiento es intrínseco (no depende de las circunstancias), lo cual es no determinista (todo fenómeno está prefijado de una manera necesaria por las circunstancias o condiciones en que se produce, y , por consiguiente, ninguno de los actos de nuestra voluntad es libre, sino necesariamente preestablecido)

Symbol-Based 7-1
MYCIN 9.2

Algunos sistemas introducen factores de certeza, de manera que dada una premisa se da una conclusión con un determinado grado de certeza en función de la fuerza de la regla.

Problema:

Estos sistemas no capturan correctamente las dependencias entre variables, de forma que cuando se dispara una regla el peso de la conslución depende únicamente de la spremisas, independientemente de las fuentes de las que provenga

El uso de factores de certeza ha recibido muchas críticas por su incapacidad para representar ciertas dependencias entre las observaciones y la forma en la que combina el conocimiento. 

Todo esto provoca la necesidad de encontrar otros fomalismos para trabajar con incertidumbre


Es clara la necesidad de contar con sistemas expertos que traten situaciones de incertidumbre. Un tipo de SE que trata este tipo de situaciones de forma efectiva lo constituyen los 

Factor de Certeza= Medida de Confianza - Medida de Desconfianza

CF(H|E) = MB(H|E) − MD(H|E).

H → Hipótesis
E → Evidencia

## ¿Por qué es necesario usar Factores de Certeza en un Sistema Experto?

Debido a que proceso estocástico que implica la clasificación del grado de confiabilidad y el grado de desconfianza de una regla de inferencia que explica el peso total de la misma influye en el comportamiento natural de recolección de datos para una mejor inferencia y por lo tanto un mejor resultado del sistema experto.