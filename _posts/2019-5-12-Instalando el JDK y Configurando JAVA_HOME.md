---
layout: post
title: "Instalando el JDK y Configurando la variable JAVA_HOME en Linux"
tags: 
  - Java
  - JDK
  - Programación
---

## Instalando el JDK y Configurando la variable JAVA_HOME en Linux

1. Para instlar el **Java Development Kid**, haz lo siguiente
    - Ve a la página de [Oracle](http://java.sun.com/javase/downloads/index.jsp)
    - Selecciona la versión adecuada del JDK y haz click en Descargar

El JDK es instalado en tu computadora en la ubicación por defecto, en /usr/jdk/jdk1.6.0_02. Puedes cambiar la localización.

2. Para configurar JAVA_HOME:
    - Para Korn y Shells Bash, corre los siguientes comandos:
    For Korn and bash shells, run the following commands:

export JAVA_HOME=jdk-install-dir

export PATH=$JAVA_HOME/bin:$PATH

For the bourne shell, run the following commands:

JAVA_HOME=jdk-install-dir

export JAVA_HOME

PATH=$JAVA_HOME/bin:$PATH

export PATH

For the C shell, run the following commands:

setenv JAVA_HOME jdk-install-dir

setenv PATH $JAVA_HOME/bin:$PATH

export PATH=$JAVA_HOME/bin:$PATH

Change the permissions to enable you to run the GlassFish ESB Installer by running the following command:

chmod 755 JavaCAPS.bin

