---
layout: post
title: Caracteristicas de los Sistemas Distribuidos
tags: 
  - Sistemas Distribuidos
  - Back-end
  - API
---

## Caracteristicas de los Sistemas Distribuidos

![Sistemas Distribuidos](/images/distributed_sistems.png "Sistemas Distribuidos"){: .center-image}

Sistema Distribuido
: Un **sistema distribuido** es el que sus componentes están situados en computadoras conectadas a una **red**, se comunican y coordinan acciones por medio de la transmición de mensajes.


### Introducción

Definimos a los **sistemas distribuidos** como en los que sus componentes de hardware y software localizados en computadoras en red se comunican y coordinan acciones con solo transmitir mensajes entre si.

Esto implica: 

* **Concurrencia:** Capacidad de un sistema de manejar el incremento de recursos compartidos añadiendo más recursos (como computadoras) a la red.

* **Sin reloj global:** Existen limites en la precisión en la que las computadoras en una red pueden sincronizar sus relojes debido a que no existe una noción global del tiempo correcto.

* **Fallas independientes:** Las fallas en la red resultan en el aislamiento de las computadoras que están conectadas a está, pero eso no significa que dejen de funcionar. Cada componente del sistema puede fallar independientemente, dejando a los otros para que sigan funcionando.

Los SD se implementan para **compartir recursos** desde componentes de hardware como discos e impresoras a entidades definidas de software, como archivos, bases de datos y objetos de datos de todo tipo.

## Ejemplos de Sistemas Distribuidos

Internet, Word Wide Web, Búsqueda Web, Juegos Online, Correo, Redes Sociales, eCommerce, etc. por mencionar unos.

En particular:

* **Búsqueda Web:**  La tarea de un motor de búsqueda web es indexar los contenidos íntegros del **World Wide Web**, de esta manera la mayoría de los buscadores analizan el contenido y realizan un  procesamiento sofisticado de una enorme base de datos, esta tarea en sí presenta un reto mayor para el diseño de sistemas distribuidos.

* **Juegos Multiplayer Masivos Online (MOGO)** Ofrecen una experiencia inmersiva por la que gran cantidad de usuarios interactúan en Internet en un mundo virtual de manera persistente. La ingeniería de los MOGO representa un reto mayor para la tecnologías de sistemas distribuidos, particularmente por la necesidad de la rápida respuesta en los tiempos para preservar la experiencia de usuario en el juego. Además la propagación en tiempo real de eventos de los varios jugadores y mantenimiento de una vista consistente del mundo compartido.

* **Comercio Financiero:** En el acceso en tiempo real de un gran rango de fuentes de información que incluyen: **caída del precio, el lanzamiento de figuras de desempleo, etc.** Estos sistemas comúnmente se llaman **Sistemas Distribuidos Basados en Eventos**. Además sirven para el monitoreo de la actividad comercial para el manejo del riesgo, asegurar cumplimiento con regulaciones y el monitoreo de patrones de actividad que puedan indicar transacciones fraudulentas.

## Tendencia en Sistemas Distribuidos

La tendencia en Sistemas Distribuidos apunta en un eje donde la inovación se refleja en los siguientes aspectos:

* La aparición estridente de tecnologías de red inmersiva. 
* La aparición de computo ubicuo emparejado con el deseo de soportar la movilidad del usuario en sistemas distribuidos.
* El incremento de la demanda de servicios multimedia.
* La perspectiva de sistemas distribuidos como utilidad.

### Redes Inmersivas y El Internet Moderno

Las redes se han vuelto un recurso inmersivo y penetrante, los dispositivos pueden conectarse (si lo desean) a cualquier hora y en cualquier lugar.

### Computo Móvil y Ubicuo

Está tecnología la encontramos en:

* Computadoras Portatiles y Laptops
* Dispositivos de mano que incluyen: teléfonos móviles, teléfonos inteligentes, dispositivos de GPS, PDA’s, video camaras y carmaras digitales
* Dispositivos wearables, como relojes inteligentes con funcionalidad similar al PDA 
* Dispositivos embebidos en electrodomésticos como lavadoras, sistemas de alta definición, autos y refrigeradores

El **computo móvil** es cumplimiento de tareas computacionales mientra el usuario está en movimiento o visitando distintos lugares distintos a su entorno usual.

El **computo ubicuo** es el aprovechamiento de dispositivos computacionales pequeños y baratos que están presentes en el entorno físico de los usuarios, incluyendo el hogar, oficina e incluso en entornos naturales, sin embargo la presencia de las computadoras en todos lados solo se vuelve útil si se pueden comunicar entre ellas.

El principal reto aplicado a estas situaciones es lograr una **interoperación rápida y conveniente/espontanea** entre todo el entorno computacional móvil y ubicuo.

### Sistemas Multimedia Distribuidos

Es la habilidad de los sistemas de soportar un rango amplio de **tipos de medios** de una manera integrada.

De manera integrada el soporte de **Audio y video** en los tipos de datos, esto es, el sistema deber ser capaz de guardar y localizar archivos de audio y video,transmitirlos sobre la red (posiblemente en **tiempo real** como surgen desde la video cámara), soportar la presentación de los medios al usuario y opcionalmente también compartir los medios a un grupo de usuarios.

Además acceder a brodcast en vivo o televisión grabada, acceso a bibliotecas de películas ofreciendo servicios de video en demanda, acceso a biblioteca de música, el suministro de facilidades de audio y video, conferencia y características de telefonía integrada incluyendo telefonía IP.

### Computo Distribuido como una utilidad (Cloud Computing)

Los recursos son suministrados por **proveedores de servicio** apropiados y rentados efectivamente en lugar de ser poseídos por el usuario final. Este modelo aplica a: 

* Recursos físicos y Servicios lógicos 
* Almacenamiento y Procesamiento
* Data centers
* Virtualización de Sistemas Operativos
* Servicios de Software
* Correo y Calendarios Distribuidos

El termino **Cloud Computing** es usado para capturar está visión del computo como utilidad. Una **nube** es definida como un set de aplicaciones basadas en Internet, almacenamiento y servicios de computo suficientes para satisfacer la mayoría de las necesidades de los usuarios, de esta manera habilitados de gran o total manera con almacenamiento de datos local y aplicaciones de software.

Esta perspectiva es del **recurso como servicio**.

Un **cluster de computadoras** es un set de computadoras interconectadas que cooperan para proveer un único e integrado rendimiento de capacidad computacional.

Los **Servidores Blade** son elementos mínimos computacionales que contienen el procesamiento y capacidades de almacenamiento. Otros elementos como poder, enfriamiento, discos de persistencia, red, pantallas son suministrados ya sea por el bastidor o por soluciones virtualizadas.

El **computo en red** también puede ser visto como el computo en la nube y como su predecesor el cual mantenia aplicaciones científicas.

## Enfoque en el Intercambio de Recursos

El gran significado para los usuarios es el **intercambio de recursos** a alto nivel en el cual juegan parte de sus aplicaciones, en su trabajo diario y actividades sociales.

El patrón de intercambio y la distribución geográfica de los usuarios  determina que mecanismos el sistema debe proveer para coordinar las acciones de los usuarios.

Usamos el termino **servicio** para una parte distinta del sistema que **administra una colección de recursos compartidos y presenta su funcionalidad a los usuarios y aplicaciones.** El mero acceso que tenemos al servicio es vía un set de operaciones que los exporta. Cada recurso debe ser manejado por un programa que ofrezca una interfaz de comunicación permitiendo al recurso ser accesado y actualizado confiablemente y consistentemente.

En el **modelo cliente servidor** las peticiones son mandadas en mensajes desde los clientes al servidor y las replicas son mandadas en mensajes del servidor a los clientes, así os términos cliente y servidor aplican solo a los roles ejecutados en una sola petición. **Cliente y Servidor** se refieren a los procesos en lugar de las computadoras donde se ejecutan.

En un **sistema distribuido** construido sobre un lenguaje **orientado a objetos**, los recursos pueden ser encapsulados como objetos y accesados como objetos de clientes.


