
 

---
layout: post
title: AWS Lambdas Tutorial
tags:
  - Serverless
  - AWS
  - Java
  - Lambdas
  - Amazon
---

 
 ![AWS Lambdas](/images/lambda.png "Lambdas"){: .center-image}


[1. Introducción a las Lambdas de AWS](#1-introducci%c3%b3n)   
[2. Configuración de seguridad](#2-configuraci%c3%b3n-de-seguridad)  
[3. Invocación de funciones Lambda](#3-invocaci%c3%b3n-de-funciones-lambda)  
[4. Fuentes de eventos](#4-fuentes-de-eventos)   
[5. Anatomía de una función lambda](#5-anatom%c3%ada-de-una-funci%c3%b3n-lambda)  
[6. Objetos de evento, contenido y contexto](#6-objetos-de-evento-contenido-y-contexto)  
[7. Modelo de Programación](#7-modelo-de-programaci%c3%b3n)  
[8. Escribiendo tu primera función Lambda](#8-escribiendo-tu-primera-funci%c3%b3n-lambda)   

#### 1.  Introducción
 
Una función es una parte de código que se ejecuta cada vez que se activa un **evento**. Una función se ejecuta dentro de un **tiempo de ejecución (runtime)** en una plataforma  y se aloja en una infraestructura proporcionada por **AWS**. Es posible seleccionar la cantidad de **memoria** asignada a una función, esto también controla la cantidad de **CPU** compartida que recibe la función cuando se ejecuta. La cantidad mínima de memoria que puede asignar es de **128 MB** , pero puede llegar hasta **3008 MB**. Las funciones también tienen un **tiempo de ejecución finito**, el cual puede configurarse y tiene un límite estricto de **900 segundos (15 minutos)** . Si la función aún se está ejecutando en este momento, se cancelará.
 
Una función se invoca por medio de un **evento externo** debido a un **mapeo preconfigurado** en la función, cada vez que ocurre el evento, se activará una llamada a la función. Si el servicio lo necesita, este puede **escalar automáticamente** para satisfacer la petición. 
 
Solo se paga la cantidad de tiempo que se ejecuta el código. El parametro que se usa es: **tiempo** (redondeado a **100ms**) y el numero de **memoria** que la funcion utiliza. AWS llama a esta combinación **gigabyte-segundo** de **GB/s**. Si se utilizan otros servicios dentro de AWS, estos generan su propia tarifa. 
              
Para cada cuenta de AWS, existen **límites** específicos para el servicio y el tiempo de ejecución: límite de concurrencia de **1000 ejecuciones a la vez**. El tamaño de las **variables de entorno** no puede ser superior a **4KB**. El tamaño de la **carga de invocación (payload)** no puede ser superior a **6MB** para solicitudes **sincrónas** y **256KB** para solicitudes **asíncronas**.

Puedes especificar tus propias **variables de entorno** que se establecerán en el nivel del sistema operativo durante cada invocación y puedes acceder a estos a través de tu código.  
 
 
#### 2. Configuración de seguridad
Las **políticas** son la forma en la que protegemos el acceso para entidades que invocan funciones, así como qué tareas pueden hacer mientras se ejecuta para proteger el servicio Lambda. Existen dos tipos de políticas:
 
##### a) Políticas de ejecución
 
Estas políticas se adjuntan a un **rol vinculado al servicio** y definen a qué **recursos** de AWS puede acceder ese rol. Siguen la misma sintaxis que una política de **IAM**. Cuando creas una función Lambda, tienes la opción de adjuntar un rol IAM existente o crear uno nuevo. Siempre se puede modificar la configuración para usar un rol diferente. Al adjuntar un rol a una función lambda, se define exactamente a qué **recursos** de AWS tiene acceso el código de la función mientras se está ejecutando.


##### b) Políticas de funciones
 
Las políticas de función otorgan permiso para que **otro servicio de AWS invoque** esa función particular. Se puede usar una función de política para permitir que un servicio en otra cuenta de AWS invoque a la función. 
 
#### 3. Invocación de funciones Lambda
 

Las funciones de Lambda se pueden invocar utilizando lo siguiente: **un push, un evento, un modelo basado en stream**. El modelo de **push** es un tipo de invocación **sincrona** en el que solicita una invocación de la función y luego espera a que la función vuelva con una **respuesta**. Puede esperar datos en la respuesta como el método GET en la API Gateway. El método **asíncrono** o de **evento** para invocar funciones y es utilizado principalmente por otros servicios en el ecosistema de AWS para solicitar que se active una función lambda como resultado de una acción en ese servicio. El servicio en sí invoca el Lambda en lugar de su propio código. Esta es la razón por la cual existen las **políticas de recursos** para que se puedan otorgar permisos a ese servicio. El modelo de invocación basado en **secuencias** se asemeja a una asignación entre Lambda y una **secuencia de eventos**. En el tipo de **modelo de extracción**, el servicio lambda está sondeando la secuencia. Puedes especificar el **tipo de invocación** como parámetro al llamar a Lambda a través de la API o SKD. Las opciones son: 

- **RequestResponse**: para invocar la función sincrónicamente y cuando espera una respuesta. La conexión se mantiene abierta hasta que la función devuelve un payload o finaliza inesperadamente.

- **Event**:  para invocar la función de forma asíncrona. La invocación de la llamada de API responde con **202 Aceptado**, lo que significa que todo va bien.


- **DryRun**: para verificar que todos sus parámetros de entrada sean válidos y que su usuario o rol de IAM tenga los permisos correctos para invocar la función. Esto devolverá un **HTTP 204**  si está validado; de lo contrario, recibirá un **código 4xx o 5xx** que describe el problema. 


#### 4. Fuentes de eventos
 
Las siguientes son las formas en que se puede invocar una función Lambda:

- A través de la **API de invocación AWS Lambda**
- Mediante el uso de un **SDK**, 
- **Orígenes de eventos**: varios servicios en el ecosistema de AWS pueden activar de forma nativa la invocación de una función Lambda.
 
Las fuentes de eventos pueden hacer uso de los diversos tipos de invocación.


#### 5. Método de la función lambda
  
El método controlador es el **punto de entrada** para todas las funciones de Lambda. En **Java** debes especificar un tipo de retorno, si está invocando el Lambda **sincrónicamente** (**RequestResponse**), este será el tipo de datos del objeto. Si invocas el Lambda **asincronico** (usando el tipo de **Event**), entonces no espera que se devuelva ningún dato , por lo que puedes usar un tipo de retorno **void**. También debes especificar el **tipo de datos de eventos entrantes** (generalmente es un **Sting**). 

Como resultado, la firma del método en Java es: 

```java 
nombreDelControlador tipoDeRetorno(TipoDeEntrada input, Context contexto) {
    return;
    }
```


### 6. Objetos de evento, contenido y contexto
 
Son todos los objetos que se pasan al controlador en la inicialización.
- El objeto **Event** es necesario si desea acceder a las entradas externas con las que se llamó a la función, proporciona información sobre la solicitud de origen.

- El objeto **Context** proporciona algunas propiedades y métodos que puede usar para introspectar el **entorno en ejecución**. El objeto en sí estará en un formato diferente, dependiendo del tiempo de ejecución que elija.
  
  
- Para las invocaciones por medio de **API o SDK**, puedes incluir algunos datos **JSON** arbitrarios junto con él. Se puede acceder a estos datos durante el tiempo de ejecución a través del objeto **Event**. Si otro servicio invoca la lambda, ese servicio a menudo incluirá información útil en el evento. Cada servicio envia un objeto de evento con un formato diferente.
  
#### 7. Modelo de Programación
 
 
#### a) Tiempo de Ejecución
 
Al crear una nueva función Lambda, eliges qué **tiempo de ejecución** usar, en nuestro caso será **JDK 8**. No puedes cambiar el tiempo de ejecución una vez que ya se ha creado. AWS no admite una versión de tiempo de ejecución desactualizada junto con su sistema operativo y dependencias, de la misma forma no cuenta con soporte para las versiones que alcanzan una determinada etapa de su ciclo de vida. Antes de comenzar el **desuso**, AWS anuncia el final de la vida útil de un tiempo de ejecución. La **primera fase** es eliminar la capacidad de crear nuevas funciones utilizando el tiempo de ejecución obsoleto, en la **segunda fase** también elimina la capacidad de actualizar. Hay una **tercera fase** donde se elimina la capacidad de invocar la función por completo.
 
 
#### b) Escritura, construcción y empaquetado
 
Existen varias opciones sobre cómo crear una función. La **estructura del proyecto** se refiere a el uso de frameworks para escribir y crear plantillas de aplicaciones serverless. Estoy simplifican el trabajo duando empiece a crecer tu aplicación serverless con múltiples funciones lambda, sistemas de mensajería y almacenes de datos. Un **framework** centraliza el código para los componentes de una aplicación, permite un mayor control en un equipo de desarrollo distribuido, permite pruebas locales y depuración, alienta la creación de plantillas y la reutilización de código y librerias, brinda herramientas adicionales para ayudar con la implementación, la reversión, y gestión. Hay una gran cantidad de frameworks como: **Serverless Framework, AWS Chalice, Apex y AWS Serverless Application Model (SAM)**. Nosotros usaremos **Serverless Framework**, puedes consultar el tutorial [aqui](../Ambientacion/SERVERLESSF.MD).  En el caso del lenguaje **Java**, necesitamos empaquetar nuestra función y todas las dependencias en un **archivo jar** por medio de **maven**. Las dependencias requeridas ya deberían estar instaladas en el directorio local antes de comprimir. Para agrupar una función Java usando **Maven**, necesitamos crear un archivo **pom.xml** que tenga las configuraciones adecuadas de build del proyecto. Despues, podemos usar la línea de comando para construir el proyecto y crear nuestro archivo de almacenamiento Java **(.jar)**. 
 
Para que esto sea posible debemos agregar a nuestro archivo **pom.xml** las siguientes propiedades y dependencias:

```xml
    <!--  Propiedades -->
    <properties>
        
        <aws-lambda-java-events.version>1.3.0</aws-lambda-java-events.version>
        <aws-lambda-java-core.version>1.2.0</aws-lambda-java-core.version>
        <aws-java-sdk.version>1.11.241</aws-java-sdk.version>
        
    </properties>
    
    <!-- Dependencias -->

    <!--SDK AWS -->
       <dependency>
            <groupId>com.amazonaws</groupId>
            <artifactId>aws-java-sdk-core</artifactId>
            <version>${aws-java-sdk.version}</version>
        </dependency>

    <!-- AWS Lambda core-->
        <dependency>
            <groupId>com.amazonaws</groupId>
            <artifactId>aws-lambda-java-core</artifactId>
            <version>${aws-lambda-java-core.version}<version>
        </dependency>

    <!-- AWS Lambda events -->
        <dependency>
            <groupId>com.amazonaws</groupId>
            <artifactId>aws-lambda-java-events</artifactId>
            <version>${aws-lambda-java-events.version}</version>
        </dependency>

```



#### c) Despliegue
 
Una vez que tenemos nuestro paquete necesitamos desplegarlo en la plataforma. Existen varias hay opciones para la implementación. Lo más sencillo es usar el **panel de Lambda** en la consola de administración de AWS.


El archivo se carga a través del **navegador** en un bucket de amazon s3 que el servicio lambda crea en automatico. El servicio lambda utiliza ese objeto recién cargado como destino para la implementación y actualiza el código. Si contamos con una funcion almacenada en un S3, tambien podemos elegir ese objeto que ya se ha cargado en **bucket s3**. 
 
El versionado ocurre cuando crea la primera función Lambda, y se le da la versión **_LATEST_**. si deseas publicar una **nueva versión** de tu lambda debes hacer click en **Acciones** y luego en una nueva versión pública. Esto tomará lo que esté en la versión **_LATEST_** y lo guardará como una nueva versión con un valor numérico comenzando con 1. Cada nueva versión tiene su propio **número de recurso de Amazon (ARN)** para que pueda administrarlo o invocarlo individualmente. No necesitas hacer uso de esta de versiones, puedes usar la versión **_LATEST_** para siempre y seguir implementando nuevas versiones. Con los **Alias** puedes agregar arbitrariamente un nombre o un puntero a una versión. Estos también obtienen ARN, por lo que puede invocar una versión específica de la función mediante un alias. Un ejemplo útil de esto es: El alias de **Dev** apunta a **_LATEST_** porque contiene el código más actualizado. El alias de **Prod** apunta a una versión anterior donde el código ha sido probado y lanzado para uso en producción. Un lanzamiento de producción es tan simple como actualizar a qué versión apunta el alias. Esto es útil cuando todos los entornos están alojados en la misma cuenta de AWS. Para despliegues más grandes, podemos implementar artefactos ZIP en varias cuentas. Se recomienda que el desarrollador publique una nueva versión antes de actualizar **_LATEST_** para evitar conflictos. Usando los alias, podemos elegir equilibrar el **tráfico** en dos versiones diferentes de forma proporcional. Al hacer el lanzamiento de una función Lambda, podemos darle una ponderación para que la mitad del tráfico vaya a la nueva versión y la otra mitad a la otra, podemos monitorear cualquier impacto que pueda tener la nueva versión y tomar medidas donde sea necesario. Dentro de la entrada de registro de **START** en la secuencia de registros de CloudWatch de la función se puede observar qué versión se ha invocado.  
 
#### d) Pruebas, monitoreo y depuración              
 
Para **probar** una función, necesitamos crear un **objeto de evento** para invocarlo. Si tu función no utiliza un objeto de evento, puedes agregar algunos datos JSON arbitrarios. Si otro servicio llama a tu función, es probable que se invoque con un objeto de evento de una estructura definida. Para hacerlo a través de la consola, ve a la consola Lambda, busca tu función y configura un nuevo evento de prueba. Pega tu objeto de evento y asígnale un nombre. Una vez que haya creado el **evento de prueba**, puedes usar el botón **Probar** para invocar la función. 
 
Para realizar el mismo procedimiento desde **AWS CLI** debemos ejecutar el siguiente comando:
```bash
aws lambda invoke –Invocation-type [tipo_de_invocacion] –function-name [nombre_de_funcion] –payload [ruta_archivo_carga] 
```
Podemos pasar el JSON en línea con el comando o especificar un archivo que contenga los datos.
Por defecto, cada función Lambda viene con su propio grupo de registro de **CloudWatch Logs**. Para escribir algo en los registros, puedes usar los métodos que están disponibles en el **objeto de la consola** o escribir en **stdout o stderr**. Los registros aparecen en una secuencia de registro dentro del grupo de registro asociado con la función. Se crea una secuencia de registro para cada nueva instancia de la función.  

Para obtener los registros de CloudWatch de nuestra función, podemos utilizar el siguiente comando en AWS-CLI:
```bash
aws lambda invoke –Invokation-type  –function-name myFunction –log-type Tail –query 'LogResult' –archivo de salida de texto | base64 -d
 ```
El tipo de registro **Tail** nos permite obtener un objeto con datos de registro, que podemos extraer con el formato de consulta y salida. Los datos de LogResult están codificados en **base64**, por lo que canalizamos la salida a través del programa base64 con un interruptor para decodificar (-d para linux y Windows, D para macOS). El resultado es texto legible en la consola de línea de comandos que parece similar al que vería en la secuencia de registro de CloudWatch. Estos métodos son útiles para pruebas ad hoc o puntuales, pero idealmente, queremos automatizar nuestras pruebas en un pipeline. Una forma fácil de lograr la recopilación métrica es simplemente registrar el valor o la ocurrencia en strdout o stderr. 
 
 
 
### 8. Escribiendo tu primera función Lambda

####  Hola, mundo Usando AWS-CLI
 
Los comandos en una terminal usando el AWS CLI lo cual es mucho más sencillo.
 
**Obteniendo el ARN de nuestro rol:**

```bash
aws iam get-role –role-name [nombre_lambda] –query 'Role.Arn' --output text
 ```
**Crea una lambda a partir de un paquete jar**

```bash
aws lambda create-function -–function-name [nombre_lambda] –-runtime java8 –role [arn] --handler[metodo_handler_del_controlador] --zip-file  [ruta_archivo_jar] 
 ```

 Esto nos devolverá un **json** con los datos de nuestra lambda.

**Invocar la función**
```bash
aws lambda invoke -–funciton-name [nombre_lambda] -–payload [json_payload] output.file
 ```
