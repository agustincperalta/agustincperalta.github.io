---
layout: post
title: "Instalando el JDK y Configurando la variable JAVA_HOME en Linux"
tags: 
  - Java
  - JDK
  - Programación
---

## Instalando el JDK y Configurando la variable JAVA_HOME en Sistemas UNIX


![Java Linux](/images/java_linux.png "Java Linux"){: .center-image}


1. Para instalar el **Java Development Kit**, haz lo siguiente
    - Ve a la página de [Oracle](http://java.sun.com/javase/downloads/index.jsp)
    - Selecciona la versión adecuada del JDK y haz click en Descargar

   El JDK es instalado en tu computadora en la ubicación por defecto: `/usr/jdk/jdk_version_` Pero puedes cambiar la localización.

2. Para configurar la variable de entorno $JAVA_HOME:
  
Para **Korn y Shells Bash**, corre los siguientes comandos:

    export JAVA_HOME=jdk-install-dir
    export PATH=$JAVA_HOME/bin:$PATH

Para **Bourne Shelll**, corre el siguientes comandos:

    JAVA_HOME=jdk-install-dir
    export JAVA_HOME
    PATH=$JAVA_HOME/bin:$PATH
    export PATH

Para **C shell**, corre los siguientes comandos:

    setenv JAVA_HOME jdk-install-dir
    setenv PATH $JAVA_HOME/bin:$PATH
    export PATH=$JAVA_HOME/bin:$PATH


Cambia los permisos para que puedas correr el instalador **ESB GlassFish** ejecutando el siguiente comando:

    chmod 755 JavaCAPS.bin

