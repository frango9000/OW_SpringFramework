 # SPRING FRAMEWORK
 
 1.1 ¿Qué es Spring?
Spring es un framework de código abierto para el desarrollo de aplicaciones (empresariales) Java. Su origen está en el trabajo de Rod Johnson, que trabajaba como consultor externo, y que plasmó en el libro Expert One-to-One J2EE Design and Development  (Octubre, 2002). Según Johnson, el modelo de los Enterprise Java Beans era excesivamente tedioso y pesado para muchas aplicaciones desarrolladas hasta el momento. Por ello, condensó su experiencia y sus buenas prácticas en un conjunto de clases que fueron el origen del framework.

Algunas de las críticas de Johnson al uso de EJBs son (ver J2EE development without EJB (2004)):

Complejidad (descriptores, implementaciones de interfaces, …) y baja productividad del programador.

Modelo remoto solamente basado en RMI.

Muchas aplicaciones no necesitan componentes remotos.

Difíciles de depurar (volver a hacer deployment y volver a arrancar).

Mapeo O/R basado en entity beans limitado (por ejemplo, no existe la herencia)
…
Spring popularizó desde su inicio ideas como la inyección de dependencias (que aprenderemos más adelante), el uso de POJOs (Plain old Java Object) como objetos de negocio, etc… que suponían un cambio radical con respecto al estándar; de esta forma, las aplicaciones podían ser más ligeras, y posibilitó que un framework que estaba inicialmente ideado para la capa de negocio se convirtiera en un stack de tecnologías para todas las capas de la aplicación.

Spring está basado en los siguientes principios:

El buen diseño es más importante que la tecnología subyacente.

Los Java Beans ligados de una manera más libre entre interfaces es un buen modelo.

El código debe ser fácil de probar.
Desde hace tiempo, estas ideas tan innovadoras popularizadas por Spring se han ido incorporando poco a poco al estándar, de forma que Spring y JavaEE han convergido mucho. Aun así, Spring ha conseguido crear una comunidad de desarrolladores en torno a sus diferentes tecnologías, siendo una alternativa necesaria de conocer, y muy utilizada en el entorno empresarial. En la actualidad, las aportaciones más novedosas de Spring se centran en campos de BigData, NoSQL, HTML5, Mobile, aplicaciones sociales, seguridad…

A día de hoy, una de las principales diferencias que podemos encontrar entre JavaEE y Spring es la posibilidad de usar un servidor web más convencional (estilo Tomcat) para desplegar la aplicación (con Spring Boot aprenderemos que nos podemos olvidar incluso de esta parte). JavaEE requiere el uso de un servidor de aplicaciones que, normalmente, requerirá de mayor conocimiento para su configuración y despliegue, y necesitará de unos recursos más potentes para correr cualquier aplicación.

1.2 Módulos de Spring
En la siguiente imagen, podemos ver las diferentes tecnologías (en terminología Spring, proyectos) que conforman a día de hoy Spring:


Algunos de los módulos más importantes de Spring

Core: La parte fundamental de este framework es el módulo Core, y los adyacentes Bean y Context. Proveen toda la funcionalidad para la inyección de dependencias, permitiéndole administrar la funcionalidad del contenedor de Beans (trabajaremos sobre estos conceptos de forma más amplia en las próximas lecciones). Además, también proveen de los servicios Enteprise como JDNI, EJB, …

AOP: Se trata de un módulo que nos permitirá utilizar el paradigma de Programación Orientada a Aspectos (Aspect Oriented Programming). Este paradigma permite mejorar la modularización y separar las responsabilidades. De esta forma, podemos separar las funcionalidades comunes, que se utilizan transversalmente a lo largo de toda la aplicación, de aquellas que son propias de cada módulo.

Data: Se trata de un gran módulo, formado por múltiples submódulos, y que nos permite simplificar el acceso y persistencia de datos. Spring Data nos proporciona soporte para usar base de datos relacionales (JDBC), ORMs (como por ejemplo JPA, Hibernate, …) e incluso modelos de persistencia NoSQL (como por ejemplo, MongoDB).

Web: Este módulo nos permitirá implementar el patrón Modelo-Vista-Controlador (MVC) de una manera sencilla y limpia, haciendo uso de forma transparente también de otros patrones de diseño, como FrontController. De esta forma, podemos separar limpiamente la lógica de negocio de la presentación de los datos y el acceso a los mismos. Además de aplicaciones que implican el uso de vistas y formularios, también podremos crear servicios web (por ejemplo, al estilo REST) de una forma sencilla y rápida.
La modularidad de Spring nos permitirá la posibilidad de usar solo algunas de las partes del framework, y poder combinar esta con otros frameworks diferentes:

Un proyecto que implemente MVC mediante el uso de Struts podría incorporar el contenedor de IoC mediante el uso de Spring (sin necesidad de utilizar Spring Web MVC).

Una aplicación web desarrollada con Spring Web MVC podría implementar su capa de datos mediante el uso de Hibernate (sin hacer uso de Spring Data).
1.3 Versiones de Spring
La primera versión de Spring se publicó en marzo de 2004. Actualmente, la versión más estable en la actualidad de Spring es la 4.3.2, si bien ya podemos encontrar en fases preliminares la versión 5.0 (que nos permitirá trabajar con JDK 9).

Versión	Descripción
1.0	Primera versión de Spring
2.0	Espacios de nombres XML, soporte para AspectJ
2.5	Configuración a través de anotaciones
3.0	Actualización a Java5+, Configuración a través de Java (@Configuration)
A continuación, podemos ver algunos de los elementos que se han incorporado en las diferentes versiones 4.X

Versión	Cambios introducidos
4.0	
Mejora de la documentación.

Eliminación de código deprecado.

Adaptación al uso de Java 8

Basado en Java EE 6 (JPA 2.0, Servlet 3.0), con soporte para Java EE 7 (JPA 2.1, JTA 1.2, …)

Mejoras en el contenedor de inversión de control

Mejoras en el módulo web para la creación de servicios REST (@RestController, AsyncRestTemplate)
4.1	
Mejoras en las prestaciones de Java Message Services.

Soporte para anotaciones JCache (JSR-107)

Mejoras varias en el módulo web

Mejoras en el módulo de WebSocket.
4.2	
Varias mejoras en el módulo core (sobre todo a nivel de configuración a través de Java).

Mejoras en el módulo de acceso a datos (como por ejemplo, soporte para Hibernate 5.0).

Mejoras en JMS

Mejoras en el módulo web (integración de OkHTTP, soporte para CORS, anotaciones propias el mapeo, con @RequestMapping como metaanotación, …)
4.3	
Mejoras en el módulo core: métodos default de Java 8, mayor información en las excepciones, soporte de inyección por constructor para @Configuration…

Mejoras en el módulo web: anotaciones compuestas para @RequestMapping: @GetMapping, @PostMapping, @PutMapping, @DeleteMapping, y @PatchMapping; nuevas anotaciones compuestas para los ámbitos web: @RequestScope, @SessionScope, @ApplicationScope; otra serie de nuevas anotaciones…

Mejoras en los módulos de WebSocket y Testing



2.1 Spring Tool Suite: nuestro entorno de trabajo
STS (Spring Tool Suite), es un entorno de desarrollo basado en Eclipse que está preparado para el desarrollo de aplicaciones Spring. Proporciona un entorno ready-to-use para implementar, depurar, ejecutar y desplegar aplicaciones Spring, incluyendo integraciones con Git, Maven, AspectJ, así como todas las funcionalidades de las últimas versiones de eclipse.

La última versión disponible la podemos encontrar en la propia web de spring (https://spring.io/tools/sts). Si pinchamos sobre el enlace, podemos acceder a la descarga del entorno, que viene empaquetado como un fichero zip. Dentro del mismo, podemos encontrar una carpeta con todo el software, y el ejecutable, llamado STS.exe.

Sin embargo, en los primeros compases del curso, trabajaremos con Spring al estilo Maven, lo que nos proporcionará algunas ventajas:

Podremos trabajar con proyectos legacy (heredados), que estén configurados como proyectos Maven.

Nos permitirá implementar proyectos sin el uso de la herramienta específica STS, y así poder utilizar cualquier otro IDE de uso general (el propio Eclipse, Netbeans, JDeveloper…).
2.2 Una palabra más sobre Maven
A día de hoy encontramos a muchos desarrolladores de Spring que utilizan Eclipse, y que comienzan los desarrollos de Spring como proyectos Maven. Maven nos permite gestionar las dependencias a través de un fichero de configuración, pom.xml. A continuación podemos encontrar las dependencias Maven más usuales (y para la versión actual) para el trabajo con Spring.

Dependencia	¿Para qué sirve?
<dependency><groupId>org.springframework</groupId><artifactId>spring-core</artifactId><version>4.3.2.RELEASE</version></dependency>	Esta es una de las dependencias más básicas. Si queremos construir un proyecto básico con Spring, que nos permita usar el IoC container y definir nuestros propios beans, esta es la dependencia que debemos usar.
<dependency><groupId>org.springframework</groupId><artifactId>spring-webmvc</artifactId><version>4.3.2.RELEASE</version></dependency>	Esta dependencia nos permitirá trabajar con todos los componentes para implementar aplicaciones web siguiendo el patrón Modelo-Vista-Controlador
<dependency><groupId>org.springframework</groupId><artifactId>spring-aop</artifactId><version>4.3.2.RELEASE</version></dependency>	Esta dependencia sirve para poder utilizar la programación orientada a aspectos (AOP).
<dependency><groupId>org.springframework.data</groupId><artifactId>spring-data-jpa</artifactId></dependency>	Esta dependencia, algo más específica, nos permitirá trabajar con el submódulo de Spring Data para JPA
A lo largo del curso trabajaremos con algunas dependencias más, que no son propias de Spring, pero sí de otros elementos que necesitaremos, como la interfaz de usuario, el proveedor de ORM (Object Relational Mapping), la base de datos…:

Dependencia	¿Para qué sirve?
<dependency><groupId>com.h2database</groupId><artifactId>h2</artifactId></dependency>	Base de datos relacional embebible en un proyecto, implementada íntegramente en Java. Es muy útil para la fase de desarrollo o para sistemas que no necesitan un sistema gestor de base de datos profesional de alto rendimiento.
<dependency><groupId>org.hibernate</groupId><artifactId>hibernate-entitymanager</artifactId></dependency>	Hibernate es uno de los motores de persistencia más utilizado a día de hoy en proyectos sofware.
<dependency><groupId>log4j</groupId><artifactId>log4j</artifactId><version>1.2.14</version></dependency>	Log 4 Java es uno de los múltiples sistemas de logging disponibles para Spring, que nos permitirá configurar rápidamente este aspecto de nuestros proyectos.
Durante todas las lecciones, se proporcionarán las dependencias necesarias o el fichero pom.xml completo necesarios para poder realizar los ejemplos.


3.1 ¿Qué es eso de la inversión del control?
Aunque la plataforma Java provee de una gran cantidad de clases y funcionalidades para el desarrollo de aplicaciones, carece de los medios para organizar los bloques básicos en un todo coherente, dejando esta tarea para los arquitectos y desarrolladores. Si bien se pueden utilizar algunos patrones de diseño como Factory, Abstract Factory, Builder, Decorator, and Service Locator para componer las diferentes clases y objetos de la aplicación, estos patrones son simplemente eso: buenas prácticas.

Una forma sencilla de explicar el concepto de IoC (Inversion of control) es el Principio de Hollywood:

No nos llames; nosotros te llamaremos
La inversión de control es una forma de programar en la que el flujo de ejecución de un programa se invierte respecto a los métodos de programación tradicionales, en los que la interacción se expresa de forma imperativa realizando llamadas a procedimientos o funciones. De esta forma, para poder implementar la IoC, necesitamos un agente externo, normalmente llamado contenedor, que se encargará de realizar las conexiones necesarias entre las clases dependientes. Este agente externo será el encargado de controlar el flujo de la aplicación. De esa forma, podremos realiza la implementación de un código que esté débilmente acoplada.

Para entender este cambio, vamos a utilizar un ejemplo con pseudocódigo (para no enmarañar el concepto con mucho código fuente innecesario). Imaginemos que estamos escribiendo un programa que tomar alguna información del usuario y que estamos usando la línea de comandos. Deberíamos hacer algo así:

escribir "¿Cuál es tu nombre?"
nombre <- Introducir nombre por teclado
procesar_nombre(nombre)
escribir "¿Cuál es tu pregunta?"
pregunta <- Introducir pregunta por teclado
procesa_pregunta(pregunta)
A lo largo de la interacción existente en el programa, el código es el que decide el flujo: decide cuando preguntar, cuando leer las respuestas así como cuando procesarlas.

Supongamos ahora que queremos adaptar nuestro programa a un sistema gráfico de ventanas. Podríamos tener un código parecido al siguiente (se trata de otra simplificación en pseudocódigo, ya que este código implementado en Java necesitaría de bastantes líneas más):

importar ventanas, botones, campos_texto

ventana_principal <- crear nueva Ventana.
etiqueta_nombre <- crear nueva etiqueta "¿Cuál es tu nombre?"
añadir a ventana_principal << etiqueta_nombre
nombre <- crear nuevo campo_texto
añadir a ventana_principal << nombre
en_caso_de_evento('dejar foco') sobre nombre, procesar_nombre(nombre)
etiqueta_pregunta <- crear nueva etiqueta "¿Cuál es tu pregunta?"
añadir a ventana_principal << etiqueta_pregunta
pregunta <- crear nuevo campo_texto
añadir a ventana_principal << pregunta
en_caso_de_evento('dejar foco') sobre pregunta, procesar_pregunta(pregunta)
Ventanas.buclePrincipal
Hay una gran diferencia entre el flujo del primer programa y de este segundo, en concreto, en las llamadas a las funciones para procesar el nombre y la pregunta. En este segundo código, no se tiene control sobre cuando se llamarán a dichas funciones, sino que se le ha entregado al control al sistema de ventanas. El decidirá cuándo llamar a estas funciones, basándose en la vinculación que hemos hecho (en_caso_de_evento(...)). El control se ha invertido (en lugar de invocar yo a una clase, es el framework el que me invoca a mí). Este ejemplo es de Martin Fowler, una de las personas que acuñaron el concepto de Inversión de Control.

La inversión de control es un término genérico que puede implementarse de diferentes maneras, si bien la implementación realizada por Spring es la de inyección de dependencias, que trabajaremos en la siguiente lección.




4.1 Inversión de control mediante la inyección de dependencias.
La dependencia de un objeto respecto a otro ocurre cuando el primero necesita del segundo para completar alguna de sus tareas.

Un caso típico es el de un coche, que depende del motor para, por ejemplo, poder avanzar.

public class Motor
{
    //...

    public void acelerar() {
        //...
    }

    public int getRevoluciones() {
        return currentRPM;
    }

    //...
}
 
public class Vehiculo
{
    private Motor m;

    public Vehiculo() {
        m = new Motor();
    }

    public int getRevolucionesMotor() {
        return m.getRevoluciones();
    }
}
Como podemos comprobar, la dependencia entre las clases Vehiculo y Motor queda patente dado que una instancia de la primera alberga dentro una instancia de la segunda.

Sin embargo, podemos comprobar que el acoplamiento existente en el código es alto. El motor está fuertemente ligado al vehículo, de forma que esta relación es poco flexible. Si quisiéramos realizar cualquier tipo de modificación en la clase Motor, esto supondría un alto impacto en la clase Vehiculo (por ejemplo, si quisiéramos hacer una concreción en MotorDiesel o MotorGasolina).

Como primer paso para desacoplar el motor del vehículo, podríamos hacer que la clase Vehiculo deje de encargarse de instanciar el objeto Motor, pasándoselo como parámetro al constructor. De esta forma, la clase Vehiculo quedaría de la siguiente manera:

public class Vehiculo
{
    private Motor m;

    public Vehiculo(Motor motorVehiculo) {
        m = motorVehiculo;
    }

    public int getRevolucionesMotor() {
        return m.getRevoluciones();
    }
}
El constructor de vehículo se encarga de inyectar la dependencia dentro del objeto, eliminando esta responsabilidad de la propia clase. De esa forma, hemos dado un paso para desacoplar ambos objetos.

El siguiente paso que podríamos dar en aras de continuar con el desacoplamiento de ambos objetos es el uso de interfaces.

public interface IMotor
{
    public void acelerar();

    public int getRevoluciones();
}
 
public class MotorGasolina {

    public void acelerar() {
        realizarAdmision();
        realizarCompresion();
        realizarExplosion();        //Propio de los motores de gasolina
        realizarEscape();
    }

    public int getRevoluciones() {
        return currentRPM;
    }

    //...

}
 
public class MotorDiesel {

    public void acelerar() {
        realizarAdmision();
        realizarCompresion();
        realizarCombustion();        //Propio de los motores diesel
        realizarEscape();
    }

    public int getRevoluciones() {
        return currentRPM;
    }

    //...

}
 
public class Vehiculo
{
    private IMotor m;

    public Vehiculo(IMotor motorVehiculo) {
        m = motorVehiculo;
    }

    public int getRevolucionesMotor() {
        return m.getRevoluciones();
    }
}
Como podemos observar, la clase Vehiculo ya no está acoplada a la clase Motor, sino que bastará con un objeto que implemente la interfaz IMotor, como lo son MotorDiesel o MotorGasolina.

Por último, nos faltaría ver como se realizaría la inyección de dependencias propiamente dicha. Veamos la siguiente clase, Main:

// todos los import necesarios

public class Main {
    public static void main(String[] args) {


        /*Al proporcionar un objeto que implementa la interfaz IMotor 
        como parámetro del constructor de Vehiculo, estamos inyectando 
        la dependencia.*/
        Vehiculo cocheDiesel = new Vehiculo(new MotorDiesel());
        /*En este caso, realizamos otra inyección de una dependencia, 
        pero con una instancia de MotorGasolina.*/
        Vehiculo cocheGasolina = new Vehiculo(new MotorGasolina());

        //...
    }
}
4.2 Diferentes formas de inyección de dependencias
Como hemos visto en el ejemplo anterior, una de las formas de realizar la inyección de dependencias es mediante el uso de un constructor, pero no es la única. De hecho, a nivel formal podemos decir que existen algunas más:

Inyección por constructor

Inyección por método

Inyección por propiedad (esta la encontramos en otros lenguajes de programación, con C#).
En el ejemplo anterior hemos podido apreciar que, para la inyección por constructor, la clase que tiene la dependencia sobre otra debe tener, al menor, un constructor, donde reciba un parámetro de ese tipo.

public class Vehiculo
{
    private IMotor m;

    public Vehiculo(IMotor motorVehiculo) {
        m = motorVehiculo;
    }

    //...
}
En el caso de que quisiéramos implementar esta inyección de dependencia sin el uso de constructores con parámetros, podríamos hacer uso de la inyección por método (normalmente, uno de los métodos apodados como setter). Veamos el siguiente código, modificado para realizar la inyección de dependencia de esta forma:

public class Vehiculo
{
    private IMotor m;

    public Vehiculo() {}

    public void setMotor(IMotor motor) {
        this.m = motor;
    }

    //...
}
 
// todos los import necesarios

public class Main {
    public static void main(String[] args) {

        /* En este caso, inyectamos la dependencia 
        a través de un método*/
        Vehiculo cocheDiesel = new Vehiculo();
        cocheDiesel.setMotor(new MotorDiesel());

        Vehiculo cocheGasolina = new Vehiculo();
        cocheGasolina.setMotor(new MotorGasolina());

        //...
    }
}
4.3 Inyección de dependencias con Spring
Hasta ahora, hemos visto la conocida como inyección de dependencias para pobres, en la que solamente hemos utilizado elementos de Java SE para realizar dicha inyección.

Antes de continuar, hagámonos la siguiente pregunta con respecto al ejemplo: ¿qué otras dependencias tiene un vehículo?


Diagrama de clases simplificado para un Vehículo

Como podemos observar en el anterior diagrama de clases UML, la clase Vehiculo tiene una gran cantidad de dependencias. ¿Quién se hará cargo de todas ellas? La respuesta es Spring IoC Container, en el cual trabajaremos en la siguiente sección.


5.1 El contenedor de IoC de Spring
Los paquetes org.springframework.beans y org.springframework.context son la base para el contenedor de IoC de Spring. El interface BeanFactory nos proporciona un mecanismo avanzado de configuración para gestionar cualquier tipo de objeto. ApplicationContext es un subinterface de BeanFactory, que añade una integración con Spring AOP, manejo de recursos, internacionalización, publicación de eventos y otros elementos específicos para su uso con aplicaciones web.

5.1.1 Pero, ¿qué es eso de Bean?
En Spring, los objetos que forman el nucleo de nuestra aplicación y que son gestionados por el contenedor de IoC se llaman beans. Un bean es un objeto que será instanciado, ensamblado y en definitiva gestionado por el IoC container. Dicho de otro modo, un bean no será más que uno de los muchos objetos que conformen nuestra aplicación. Los Beans, y las dependencias entre ellos, son reflejados en el fichero de configuración de metadatos usado por el contenedor.

5.1.2 Elementos del contenedor de IoC
La interface org.springframework.context.ApplicationContext representa el contenedor de IoC y es responsable de instanciar, configurar y ensamblar los ya mencionados beans. El contenedor toma toda esta información leyendo los metadatos de configuración. Estos se pueden representar en XML, mediante anotaciones Java o incluso mediante código Java. Estos metadatos nos permitirán expresar los objetos que componen nuestra aplicación así como las interdependencias existentes entre ellos.

En la siguiente imagen, podemos ver, a alto nivel, como trabaja Spring. Nuestras clases son combinadas con los metadatos de configuración; por lo que después de crear e inicializar nuestro ApplicationContext, tendremos un sistema totalmente configurado y listo para ser ejecutado.



El contenedor de inversión de control de Spring.

5.1.3 Metadatos de configuración
Como hemos visto en la figura anterior, el contenedor de IoC necesita unos metadatos de configuración. Estos metadatos representan la forma en que serán instanciados, configurados y ensamblados los objetos de nuestra aplicación.

Tradicionalmente, esta configuración se ha proporcionado mediante XML, si bien podríamos usar otras alternativas:

La configuración mediante anotaciones: fue introducida a partir de la versión 2.5 de Spring (la usaremos de forma combinada con XML).

La configuración mediante código Java: comenzó con la versión 3.0 de Java.
A continuación podemos ver cual sería la estructura básica de un fichero XML de configuración:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions go here -->

</beans>
5.2 HolaMundo con Spring (con configuración XML)
Hasta ahora hemos introducido alguno de los conceptos nucleares sobre el Spring IoC container. Sin embargo, cualquier tecnología o lenguaje de programación que se precie debe tener su HolaMundo. Vamos a crear el nuestro paso a paso.

Paso 1: Crear un proyecto Maven.
Ejecutamos nuestro entorno de desarrollo, Spring Tool Suite, y procedemos a la creación de un nuevo proyecto de tipo Maven. En este punto, seleccionamos el arquetipo maven-archetype-quickstart. Como metadatos del proyecto, escribimos un Group Id, que en nuestro caso será com.openwebinars; y por último como Artifact Id escribimos el nombre del proyecto, que será HelloWorldSpring.

















Creación de un proyecto de tipo Maven, selección de arquetipo e introducción de los metadatos básicos del proyecto.

Si seguimos estos pasos, obtendremos un proyecto que tendrá el siguiente aspecto en el explorador del IDE:



Estructura del proyecto recién creado.

Procedemos, por último, a eliminar los ficheros App.java y AppTest.java, ya que crearemos nuestras propias clases a través de los asistentes.

Paso 2: Añadir las dependencias necesarias.
Abrimos el fichero pom.xml, al cual podemos acceder a través de nuestro proyecto, y seleccionamos la pestaña inferior pom.xml; necesitamos añadir las dependencias necesarias para usar Spring. La siguiente, nos añadirá todos los ficheros necesarios para usar el módulo Core.

<!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>4.3.1.RELEASE</version>
</dependency>
De esta forma, el fichero pom.xml debería tener el siguiente contenido:

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.openwebinars</groupId>
    <artifactId>HelloWorldSpring</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>jar</packaging>

    <name>HelloWorldSpring</name>
    <url>http://maven.apache.org</url>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.1.RELEASE</version>
        </dependency>
    </dependencies>
</project>
Almacenamos el contenido del fichero, y procedemos a actualizar el proyecto Maven.







Actualización del repositorio local de Maven, para descargar todas las dependencias.

Paso 3: Añadir el código Java.
Una vez configurado nuestro proyecto, vamos a dar paso a crear nuestro Hola Mundo.

En primer lugar, creamos un nuevo paquete, llamado com.openwebinars.beans, donde ubicaremos los beans de nuestro proyecto.

Posteriormente, creamos dentro de este nuevo paquete una nueva clase, llamada Mundo, y que tendrá un código muy sencillo (tan solo una propiedad, y sus correspondientes getter/setter):

package com.openwebinars.beans;

public class Mundo {

    private String saludo;

    public String getSaludo() {
        return saludo;
    }

    public void setSaludo(String saludo) {
        this.saludo = saludo;
    }

}
Ahora necesitamos definir este objeto, Mundo, en un contenedor, para que Spring lo pueda manejar. Esta operación la realizamos en el siguiente paso.

Paso 4: Definir el fichero de configuración XML.
En primer lugar, vamos a crear la ubicación en la cual almacenaremos nuestro fichero de configuración de beans. Es una carpeta que llamaremos resources y que estará físicamente a la misma altura del árbol de directorios que la carpeta llamada java, que contiene el código fuente.

Mediante el botón derecho del ratón sobre el proyecto, o la combinación de teclas Alt+Enter, accedemos a las propiedades del proyecto, y de entre ellas accedemos a Java Build Path. Seleccionamos la pestaña Source, y pulsamos sobre el botón Add Folder. En el diálogo que nos aparece, seleccionamos la carpeta src y pulsamos el botón Create New Folder. La ruta de la carpeta será main/resources.















Creación de la nueva carpeta src/main/resources donde ubicaremos el fichero de configuración de beans.

Dentro, creamos un nuevo paquete llamado com.openwebinars.xml. Dentro de este paquete, vamos a ubicar el fichero de configuración. Para crearlo, seleccionamos sobre dicho paquete Botón derecho > New > Spring Bean Configuration File (si no aparece directamente, tendriamos que seleccionar New > Other y buscarlo dentro de los asistentes de Spring).







Creación del fichero de configuración beans.xml

Ahora es cuando añadiremos la magia de Spring. A través de la etiqueta bean, registraremos dentro del contenedor el objeto Mundo, para poder usarlo posteriormente dentro de nuestra aplicación. Veamos el código a añadir para poder comentarlo

...
<bean id="mundo" class="com.openwebinars.beans.Mundo">
    <property name="saludo" value="Hola Mundo!"></property>
</bean>
Cada objeto deberá tener un identificador, un alias, que nos permitirá diferenciarlo de los demás a la hora de invocarlo. Dicho identificador lo establecemos a través del atributo id. En segundo lugar, el bean debe ir asociado a una clase (POJO) de nuestro proyecto. Dicha clase se establece mediante el atributo class; hay que indicar la ruta completa de la clase (es decir, nombre_paquete.nombre_clase).

Si queremos inicializar alguna de las propiedades del bean, no tenemos más que añadir un elemento property dentro del propio elemento bean, indicando el nombre de la propiedad, en nuestro caso saludo, y el valor que queremos establecerle inicialmente, que será Hola Mundo!.

Paso 5: Clase Main y ejecución.
Por último, nuestra aplicación necesita un Main para poder ejecutarse. Creamos una nueva clase, llamada App, dentro del paquete principal, com.openwebinars.HelloWorldSpring.

El primer paso que debemos seguir es crear un ApplicationContext; en particular, seleccionamos ClassPathXmlApplicationContext. Si el fichero XML estuviera en la misma ubicación que la clase, no necesitaríamos añadir ningún parámetro opcional; al no ser así, tenemos que indicar la ruta del paquete, de forma que la instanciación del objeto quedaría como sigue:

ApplicationContext appContext = new ClassPathXmlApplicationContext("com/openwebinars/xml/beans.xml");
Ahora, vamos instanciar el bean Mundo, a través del contexto. Para ello, usaremos el método getBean(...) de ApplicationContext, y utilizaremos alguna de las siguientes líneas de código:

Usando el id 
Mundo m = (Mundo) appContext.getBean("mundo");
Usando el .class 
Mundo m = (Mundo) appContext.getBean(Mundo.class);
En nuestro caso, preferimos la primera opción.

Para completar la primera versión de nuestro Main, añadimos una impresión por consola del saludo, quedando el código como sigue:

package com.openwebinars.HelloWorldSpring;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.openwebinars.beans.Mundo;

public class App {

    public static void main(String[] args) {  
        ApplicationContext appContext = new ClassPathXmlApplicationContext("com/openwebinars/xml/beans.xml");
        Mundo m = (Mundo) appContext.getBean("mundo");

        System.out.println(m.getSaludo());
    }
}
Si ahora ejecutamos este proyecto (como una aplicación java), podemos comprobar que la salida que obtenemos por la consola es la siguiente:

...
Hola Mundo!
Como podemos comprobar, hemos obtenido por consola Hola Mundo!, el mensaje que esperábamos.

Si revisamos el código, podemos comprobar que la variable appContext parece tener un warning: Resource leak: ‘appContext’ is never closed. Algunos programadores prefieren liberar el recurso asociado al contenedor de IoC una vez que no se va a utilizar más. Para ello, tendríamos que añadir la siguiente línea de código al final, quedando el código de la siguiente manera:

package com.openwebinars.HelloWorldSpring;

import org.springframework.context.ApplicationContext;
import org.springframework.context.ConfigurableApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.openwebinars.beans.Mundo;

public class App {

    public static void main(String[] args) {

        ApplicationContext appContext = new ClassPathXmlApplicationContext("com/openwebinars/xml/beans.xml");
        Mundo m = (Mundo) appContext.getBean("mundo");

        System.out.println(m.getSaludo());

        ((ConfigurableApplicationContext) appContext).close();
    }
}
5.3 Otras formas de inyección de dependencia
5.3.1 Inyección por constructor
Si revisamos el código del ejemplo HelloWorldSpring, y en particular, el de la clase Mundo, podemos darnos cuenta de que ¡Oh! No tiene constructor.

package com.openwebinars.beans;

public class Mundo {

    private String saludo;

    public String getSaludo() {
        return saludo;
    }

    public void setSaludo(String saludo) {
        this.saludo = saludo;
    }

}
¿Esto significa algo? En principio, no debería significar nada; Java, para aquellas clases que no definen un constructor de forma explícita, se encarga de definir un constructor (sin parámetros, obviamente) de forma implícita. Sin embargo, el hecho de no tener un constructor, nos dice que el tipo de inyección de dependencia que hemos hecho ha sido por método. ¿Y si quisiéramos realizarla por constructor? Los cambios a realizar serían francamente sencillos.

En primer lugar, definiríamos un constructor con parámetros para la clase Mundo, quedando la misma de la siguiente manera:

package com.openwebinars.beans;

public class Mundo {

    private String saludo;

    public Mundo(String saludo) {
        this.saludo = saludo;
    }

    public String getSaludo() {
        return saludo;
    }

    public void setSaludo(String saludo) {
        this.saludo = saludo;
    }
}
Teniendo ya un constructor explícito que recibe un parámetro con la dependencia que queremos inyectar, tendríamos que modificar el fichero de configuración, beans.xml. En este caso, en lugar de usar la etiqueta property, usaríamos constructor-arg para inicializar los valores, quedando el código de la siguiente manera:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="mundo" class="com.openwebinars.beans.Mundo">
        <!-- <property name="saludo" value="Hola Mundo!"></property>-->
        <constructor-arg value="Hola Mundo!"></constructor-arg>
    </bean>

</beans>
Si ejecutamos la aplicación, observaremos que el resultado es el mismo.

5.3.1.1 Definición de los argumentos de un constructor si son más de uno
Supongamos el escenario en el que la clase Mundo tuviera más de una propiedad:

package com.openwebinars.beans;

public class Mundo {

    private String saludo;
    private int radio;

    public Mundo(String saludo) {
        this.saludo = saludo;
    }

    public Mundo(int radio) {
        this.radio = radio;
    }

    public Mundo(String saludo, int radio) {
        this.saludo = saludo;
        this.radio = radio;
    }

    public int getRadio() {
        return radio;
    }

    public void setRadio(int radio) {
        this.radio = radio;
    }

    public String getSaludo() {
        return saludo;
    }

    public void setSaludo(String saludo) {
        this.saludo = saludo;
    }

}
Si el fichero de configuración lo modificamos para que tenga el siguiente aspecto:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="mundo" class="com.openwebinars.beans.Mundo">
        <!-- <property name="saludo" value="Hola Mundo!"></property>-->
        <constructor-arg value="Hola Mundo!"></constructor-arg>
        <constructor-arg value="6371"></constructor-arg>
    </bean>

</beans>
Y el fichero App.java lo modificamos para poder imprimir por pantalla el valor correspondiente al radio:

package com.openwebinars.HelloWorldSpring;

import org.springframework.context.ApplicationContext;
import org.springframework.context.ConfigurableApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.openwebinars.beans.Mundo;

public class App {

    public static void main(String[] args) {

        ApplicationContext appContext = new ClassPathXmlApplicationContext("com/openwebinars/xml/beans.xml");
        Mundo m = (Mundo) appContext.getBean("mundo");

        System.out.println(m.getSaludo() + "(" + m.getRadio() + " km.)");

        ((ConfigurableApplicationContext) appContext).close();

    }

}
Deberíamos obtener el siguiente resultado:

...
Hola Mundo!(6371 km.)
...
Como podemos comprobar, ha realizado la construcción del objeto de forma correcta. Pero, ¿y si queremos inicializar solamente un parámetro? O ¿y si cambiamos el orden de los argumentos?

Spring nos permite algunas introducir algunos atributos más a las etiquetas constructor-arg para esclarecer la inyección de dependencias:

Establecimiento de los tipos de datos: de esta forma, la asignación de los argumentos se realiza en base al tipo de dato usado.

    ...
    <bean id="mundo" class="com.openwebinars.beans.Mundo">
        <constructor-arg type="int" value="6371"></constructor-arg>
        <constructor-arg type="java.lang.String" value="Hola Mundo!"></constructor-arg>     
    </bean>
    ...
Establecimiento en base al índice del parámetro en el constructor: de esta forma, se realiza la inyección en base al orden de los parámetros definidos en el constructor.

    ...
    <bean id="mundo" class="com.openwebinars.beans.Mundo">
        <constructor-arg index="1" value="6371"></constructor-arg>
        <constructor-arg index="0" value="Hola Mundo!"></constructor-arg>       
    </bean>
    ...
Establecimiento en base al nombre del parámetro en el constructor: de esta forma, la inyección se materializa usando el nombre de los parámetros del constructor.

    ...
    <bean id="mundo" class="com.openwebinars.beans.Mundo">
        <constructor-arg name="radio" value="6371"></constructor-arg>
        <constructor-arg name="saludo" value="Hola Mundo!"></constructor-arg>  
    </bean>
    ...
5.3.2 Inyección por constructor vs. inyección por método
Ámbos mecanismos son posibles, y podemos mezclar su utilización como queramos. Sin embargo, algunos autores recomiendan utilizar la inyección por constructor para las dependencias obligatorias, y por método aquellas que sean opcionales

5.4 Referencias entre beans
Como podremos suponer, muy pocas apliaciones tendrán que manejar un solo bean. Normalmente, nuestro modelo y nuestra lógica de negocio tendrán que manejar múltiples beans. Hasta ahora, hemos visto como inyectar dependencias con tipos básicos java, pero ¿qué sucedería si necesitáramos inyectar como dependencia otro bean?



Detalle del diagrama de clases de Vehiculo

El atributo ref nos permite referenciar otro bean del contenedor. De esta forma, el fichero beans.xml quedaría como sigue:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="vehiculo" class="com.openwebinars.Beans.Vehiculo">
        <property name="marca" value="Mercedes Benz"></property>
        <property name="modelo" value="Clase C"></property>
        <property name="motor" ref="motor"></property>
    </bean>

    <bean id="motor" class="com.openwebinars.Beans.Motor">
        <property name="culata" ref="culata"></property>
        <property name="bloque" ref="bloque"></property>
        <property name="carter" ref="carter"></property>
        <property name="cilindrada" value="1.8"></property>
    </bean>

    <bean id="culata" class="com.openwebinars.Beans.Culata">
        <property name="cantidadBujias" value="4"></property>
    </bean>

    <bean id="bloque" class="com.openwebinars.Beans.Bloque">
        <property name="cantidadCilindros" value="4"></property>
    </bean>

    <bean id="carter" class="com.openwebinars.Beans.Carter">
        <property name="volumenAceite" value="6.5"></property>
    </bean>

</beans>
5.4.1 ¿Y si en lugar de property quiero usar constructor-arg?
Siguiendo la flexible línea que nos ofrece Spring, podemos referenciar beans haciendo uso de la etiqueta <constructor-arg> en lugar de <property>, para hacer una inyección basada en constructor, en lugar de basada en los métodos setter. Tan solo tendríamos que cambiar el fichero de configuración para que quedara como sigue:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="vehiculo" class="com.openwebinars.Beans.Vehiculo">
        <constructor-arg name="marca" value="Mercedes Benz"></constructor-arg>
        <constructor-arg name="modelo" value="Clase C"></constructor-arg>
        <constructor-arg name="motor" ref="motor"></constructor-arg>
    </bean>

    <bean id="motor" class="com.openwebinars.Beans.Motor">
        <constructor-arg name="culata" ref="culata"></constructor-arg>
        <constructor-arg name="bloque" ref="bloque"></constructor-arg>
        <constructor-arg name="carter" ref="carter"></constructor-arg>
        <constructor-arg name="cilindrada" value="1.8"></constructor-arg>
    </bean>

    <bean id="culata" class="com.openwebinars.Beans.Culata">
        <constructor-arg name="cantidadBujias" value="4"></constructor-arg>
    </bean>

    <bean id="bloque" class="com.openwebinars.Beans.Bloque">
        <constructor-arg name="cantidadCilindros" value="4"></constructor-arg>
    </bean>

    <bean id="carter" class="com.openwebinars.Beans.Carter">
        <constructor-arg name="volumenAceite" value="6.5"></constructor-arg>
    </bean>


</beans>
5.5 Beans anidados
Una de las maneras que tenemos para inyectar un bean dentro de otro es mediante el atributo ref, tanto si hacemos una inyección por setter como si la hacemos por constructor.

Sin embargo, existe otro método para poder inyectar un bean dentro de otro bean, y se conoce como inner beans o beans anidados.

<bean id="outer" class="...">
    <!-- en lugar de utilizar una referencia a un bean, simplemente definimos dicho bean en línea -->
    <property name="target">
        <bean class="com.example.Class"> 
            <property name="prop1" value="Asdfg"/>
            <property name="prop2" value="12"/>
        </bean>
    </property>
</bean>
El ejemplo del apartado 5.4 quedaría de la siguiente forma:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="vehiculo" class="com.openwebinars.Beans.Vehiculo">
        <property name="marca" value="Mercedes Benz"></property>
        <property name="modelo" value="Clase C"></property>
        <property name="motor">
            <bean class="com.openwebinars.Beans.Motor">
                <property name="culata">
                    <bean class="com.openwebinars.Beans.Culata">
                        <property name="cantidadBujias" value="4"></property>
                    </bean>
                </property>
                <property name="bloque">
                    <bean class="com.openwebinars.Beans.Bloque">
                        <property name="cantidadCilindros" value="4"></property>
                    </bean>
                </property>
                <property name="carter">
                    <bean class="com.openwebinars.Beans.Carter">
                        <property name="volumenAceite" value="6.5"></property>
                    </bean>
                </property>
                <property name="cilindrada" value="1.8"></property>
            </bean>
        </property>
    </bean>

</beans>
5.5.1 Anidación por constructor
Análogamente, también puede realizarse la anidación por constructor:

<bean id="outterBean" class="outerClass">
    <constructor-arg>
        <bean class="innerClass">
            ...
        </bean>
    </constructor-arg>
</bean>
La versión del fichero beans.xml con la inyección por constructor sería la siguiente:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="vehiculo" class="com.openwebinars.Beans.Vehiculo">
        <constructor-arg name="marca" value="Mercedes Benz"></constructor-arg>
        <constructor-arg name="modelo" value="Clase C"></constructor-arg>
        <constructor-arg name="motor">
            <bean class="com.openwebinars.Beans.Motor">
                <constructor-arg name="culata">
                    <bean class="com.openwebinars.Beans.Culata">
                        <constructor-arg name="cantidadBujias" value="4"></constructor-arg>
                    </bean>
                </constructor-arg>
                <constructor-arg name="bloque">
                    <bean class="com.openwebinars.Beans.Bloque">
                        <constructor-arg name="cantidadCilindros" value="4"></constructor-arg>
                    </bean>
                </constructor-arg>
                <constructor-arg name="carter">
                    <bean class="com.openwebinars.Beans.Carter">
                        <constructor-arg name="volumenAceite" value="6.5"></constructor-arg>
                    </bean>
                </constructor-arg>
                <constructor-arg name="cilindrada" value="1.8"></constructor-arg>
            </bean>
        </constructor-arg>
    </bean>

</beans>
5.5.2 Anidación vs. Referencia
¿Cuál de las dos opciones es mejor? La respuesta es que depende

Beans Referenciados	Beans anidados
Evitamos tener grandes bloques de código, que son difíciles de leer	El código estará más cohesionado (los beans están definidos donde se van inyectar).
Podemos obtener instancias de cualquiera de los beans que tengan propiedad id.	Todos los inner beans son anónimos. Si un bean se utiliza solamente como parte de otro, y no debe ser invocado como un objeto fuera de este, la mejor opción es anidarlo.
Permiten la separación de la definición de beans en más de un fichero	Se puede combinar la referencia de beans con la anidación de otros.
5.6 Colecciones
Hasta ahora, todas las referencias entre beans que hemos manejado podríamos llamarlas simples, es decir, siempre hacía referencia a un objeto, nunca a una colección de ellos. De sobra sabemos que las colecciones son elementos de la Programación Orientada a Objetos que se usan constantemente. Veamos como nos permitirá manejar esto Spring.

5.6.1. Tipos de colecciones manejadas por Spring
Spring nos va a permitir trabajar con los siguientes tipos de colecciones. Podemos ver en la siguiente tabla la etiqueta que necesitaremos en el fichero de configuración, y el tipo de colección (dentro del API de Java) a la que corresponden:

Etiqueta	Tipo de colección
<list/>	java.util.List
<set/>	java.util.Set
<map/>	java.util.Map
<props/>	java.util.Properties
5.6.2 Uso de una colección <list>
El esqueleto de la definición de un bean que utilizara una colección de tipo list sería el siguiente:

    <bean id="beanId" class="com.openwebinars.colecciones.ClassName">
        <property name="name" value="value"></property>
        <property name="collection">
            <list>
            ...        
            </list>
        </property>
    </bean>
Dentro del elemento <list> podemos definir:

Una referencia (<ref ...>) a otro bean
Un bean en linea
Al igual que en anteriores situaciónes, también podemos inyectar la dependencia de una lista usando un constructor.

5.6.3 Uso de una colección <set>
El esqueleto de la definición de un bean que utilizara una colección de tipo set sería el siguiente:

    <bean id="beanId" class="com.openwebinars.colecciones.ClassName">
        <property name="name" value="value"></property>
        <property name="collection">
            <set>
            ...        
            </set>
        </property>
    </bean>
5.6.4 Uso de una colección <map>
El esqueleto de la definición de un bean que utilizara una colección de tipo map sería el siguiente:

    <bean id="beanId" class="com.openwebinars.colecciones.ClassName">
        <property name="name" value="value"></property>
        <property name="collection">
            <map>
                <entry key="thekey">
                    ...
                </entry>
                ...        
            </map>
        </property>
    </bean>
Como podemos observar, esta sintaxis difiere de las anteriores debido a la naturaleza clave -> valor de las colecciones de tipo map. Por ello, cada bean de la colección, tendrá que definirse en un elemento <entry ...>, asignándole a cada uno una clave (key).

5.6.5 Uso de una colección <props>
El esqueleto de la definición de un bean que utilizara una colección de tipo props sería el siguiente:

    <bean id="beanId" class="com.openwebinars.colecciones.ClassName">
        <property name="name" value="value"></property>
        <property name="collection">
            <props>
                <prop key="thekey">value</prop>
                ...        
            </props>
        </property>
    </bean>
Las colecciones props, que es la abreviatura de properties, nos sirven como los maps, pero para definir una serie de pares clave -> valor donde el valor será un literal: un número, una cadena de caracteres, un booleano.

5.7 Carga tardía
Por defecto, ApplicationContext crea y configura todos los beans (de ámbito singleton) como parte del proceso de inicialización. Cuando esta opción no es deseable, podemos evitar esta preinstanciación marcándolo como lazy-init=true. De esta forma, le estamos indicando al contenedor que realice la instanciación la primera vez que el bean sea solicitado, en lugar de en la inicialización del contexto.

<bean id="lazy" class="com.foo.ExpensiveToCreateBean" lazy-init="true"/>
<bean name="not.lazy" class="com.foo.AnotherBean"/>
Se puede gestionar todo este proceso de manera global para el fichero de configuración, mediante el atributo default-lazy-init del elemento <beans>.

<beans default-lazy-init="true">
    <!-- no se preinstanciará ningún bean -->
</beans>
5.7.1 Uso de log4j para el ejemplo de carga tardía
Para hacer nuestro ejemplo de carga tardía, vamos a añadir una nueva dependencia en el fichero pom.xml, que nos permitirá gestionar mejor el logging (registro o bitácora) de Spring.

Añadimos esta nueva dependencia:

<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.14</version>
</dependency>
Con esta, indicamos que el sistema de logging que usaremos será Log4j, que está ampliamente extendido entre los desarrolladores de Java y Spring.

Hay que añadir información adicional de configuración. Para ello, creamos un nuevo fichero (usando el asistente de creación de ficheros), llamado log4j.properties dentro del director src/main/resources, y añadimos el siguiente contenido:

log4j.rootCategory=INFO, stdout

log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{ABSOLUTE} %5p %t %c{2}:%L - %m%n

log4j.category.org.springframework.beans.factory=DEBUG




6.1 Introducción
El contenedor de Spring puedes gestionar de forma automática las dependencias entre beans que colaboran. Se puede permitir a Spring resolver automáticamente inspeccionando dentro del contenido del ApplicationContext. A este proceso se le llama autowiring.

6.2 Modos de autowiring
Al usar la configuración del contenedor basada en XML, podemos establecer la inyección automática usando el atributo autowire del elemento <bean>. Esta funcionalidad tiene cuatro modos de trabajo. Hay que especificar, como valor del atributo, cual de ellos queremos usar:

Modo	Explicación
no	Es el modo por defecto (es decir, autowire=no es equivalente a no escribir nada con respecto a autowiring). Las referencias entre beans serán establecidas de alguna de las diferentes formas que hemos aprendido en las lecciones anteriores.
byName	La inyección automática se realiza en base al nombre de la propiedad. Spring busca un bean que tenga el mismo nombre que la propiedad que tiene la dependencia.
byType	Permite satisfacer la dependencia si Spring encuentra un bean que tenga el mismo tipo.
constructor	Análogo a byType, pero aplicando a argumentos de constructores.
6.3 Limitaciones y desventajas del autowiring
El autowiring funciona bien cuando su uso es consistente a lo largo de todo un proyecto; si no es así, podemos encontrarnos en alguna situación de confusión.

Algunas de las limitaciones son:

Las dependencias explícitas en <property>y <constructor-arg> sobrescriben el comportamiento automático. No se pueden inyectar automáticamente propiedades de tipos de datos básicos.

La inyección automática es menos exacta que la inyección explícita; con todo, Spring pone mucho cuidado en evitar la ambigüedad.

La inyección automática no permite generar documentación para el contenedor de Spring.

Una definición de varios beans de un mismo tipo que el que necesitamos para inyectar una dependencia pueden producir un problema. Si se trata de una colección, no pasa nada; pero en el caso de ser una dependencia que espera un valor, podemos obtener por respuesta una excepción.
6.4 Ejemplo de uso de autowire
Vamos a intentar trabajar, de una forma sencilla, con un ejemplo que tenga tres clases: Cliente, Persona, Ciudad.

package com.openwebinars.autowire;

public class Ciudad {

    private String nombre;

    public Ciudad() { }

    public Ciudad(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    @Override
    public String toString() {
        return "Ciudad [nombre=" + nombre + "]";
    }

}
 
package com.openwebinars.autowire;

public class Persona {

    private String nombre;
    private Ciudad ciudad;

    public Persona() { }

    public Persona(String nombre, Ciudad ciudad) {
        this.nombre = nombre;
        this.ciudad = ciudad;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public Ciudad getCiudad() {
        return ciudad;
    }

    public void setCiudad(Ciudad ciudad) {
        this.ciudad = ciudad;
    }

    @Override
    public String toString() {
        return "Persona [nombre=" + nombre + ", ciudad=" + ciudad + "]";
    }

}
 
package com.openwebinars.autowire;

public class Cliente {

    private long id;
    private Persona persona;


    public Cliente() { } 

    public Cliente(long id, Persona persona) {
        this.id = id;
        this.persona = persona;
    }

    public long getId() {
        return id;
    }

    public void setId(long id) {
        this.id = id;
    }

    public Persona getPersona() {
        return persona;
    }

    public void setPersona(Persona persona) {
        this.persona = persona;
    }

    @Override
    public String toString() {
        return "Cliente [id=" + id + ", persona=" + persona + "]";
    }  

}
Como hemos visto en los apartados superiores, para realizar el autowiring, necesitamos usar el atributo autowire de la etiqueta <bean>.

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="cliente" class="com.openwebinars.autowire.Cliente" autowire="byName">
        <property name="id" value="1"></property>
        <!-- <property name="persona" ref="persona"></property> -->
    </bean>

    <bean id="persona" class="com.openwebinars.autowire.Persona" autowire="byName">
        <property name="nombre" value="Luismi"></property>
        <!-- <property name="ciudad" ref="ciudad"></property>-->
    </bean>

    <bean id="ciudad" class="com.openwebinars.autowire.Ciudad">
        <property name="nombre" value="Sevilla"></property>
    </bean>

</beans>
También podríamos haber hecho la inyección automática de la dependencia por constructor, con el siguiente código de configuración:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="cliente" class="com.openwebinars.autowire.Cliente"
        autowire="constructor">
        <constructor-arg name="id" value="1"></constructor-arg>
    </bean>

    <bean id="persona" class="com.openwebinars.autowire.Persona"
        autowire="constructor">
        <constructor-arg name="nombre" value="Luismi">
        </constructor-arg>
    </bean>

    <bean id="ciudad" class="com.openwebinars.autowire.Ciudad">
        <constructor-arg name="nombre" value="Sevilla"></constructor-arg>
    </bean>

</beans>




7.1 Introducción
En Spring, no solo podemos controlar la inyección de varias dependencias en un solo objeto registrado como un bean, sino que además podemos controlar el ámbito o alcance (en inglés, scope) de los objetos creados. Este enfoque es potente y flexible, y permite controlar el ámbito a nivel de configuración, y así tener que evitar hacerlo directamente en Java.

En este apartado, conoceremos dos ámbitos: singleton y prototype (cuando trabajemos con Spring MVC veremos que existen algunos más: request, session, globalSession, application y WebSocket).

7.2 El ámbito singleton
Cuando definimos un bean como singleton, estamos indicando que solamente vamos a tener una instancia de dicho bean, que será compartida para todas las referencias que existan del mismo.

Dicho de otro modo, al definir un bean como singleton, estamos indicando al contenedor de Spring que debe crear exactamente una instanacia del objeto. Dicha instancia será almacenada en caché, y todas las siguientes llamadas o peticiones a dicho bean, tendrán como resultado la instancia cacheada.



Explicación de un bean de ámbito singleton

En Spring, podemos hablar de singleton describiéndolo como una instancia por contenedor. Esto significa que si definimos un bean de una clase particular en un solo contenedor, entonces, el contenedor crea una y solo una instancia de la clase definida por ese bean.

El ámbito singleton es el ámbito por defecto en Spring. Para definir un bean como singleton en XML, deberíamos escribir lo siguiente:

<bean id="accountService" class="com.foo.DefaultAccountService"/>

<!-- el siguiente modo es equivalente y redundante, ya que el ámbito singleton es el ámbito por defecto. -->
<bean id="accountService" class="com.foo.DefaultAccountService" scope="singleton"/>
7.3 El ámbito prototype
De manera opuesta, tenemos el ámbito prototype, en el cual, para cada petición de un bean, tendremos como resultado una nueva instancia.



Explicación de un bean de ámbito prototype

En el siguiente ejemplo, definiremos un bean como prototype:

<bean id="accountService" class="com.foo.DefaultAccountService" scope="prototype"/>
A diferencia de otros ámbitos, Spring no gestiona el ciclo de vida completo de un bean definido como prototype: el contenedor instancia, configura y devuelve el objeto al cliente, sin realizar ninguna operación más. Tanto es así, que no toma ningún tipo de responsabilidad en la destrucción del objeto: es el cliente el encargado de liberar los recursos, en caso de que estos fueran costosos de mantener.




8.1 Introducción
Spring nos permite interactuar con el contenedor, para realizar determinadas operaciones durante el ciclo de vida del mismo. Podemos ejecutar algún metodo justo después de instanciar un bean, y también justamente antes de destruirlo. Esto podemos hacerlo de 3 formas diferentes:

Implementando las interfaces InitializingBean y DisposableBean

Mediante el uso de las propiedades init-method y destroy-method en la configuración XML.

Usando las anotaciones @PostConstruct y @PreDestroy para decorar algún metodo del bean.
8.2 Uso de las interfaces InitializingBean y DisposableBean
Spring provee de dos interfaces en el paquete org.springframework.beans.factory, llamadas InitializingBean y DisposableBean, siendo su nombre muy autodescriptivo.

InitializingBean nos obliga a darle cuerpo al método afterPropertiesSet, y nos permitirá realizar algún tipo de lógica tras la inicialización del bean.

DisposableBean nos obliga a implementar el método destroy, que nos permitirá ejecutar alguna funcionalidad antes de que el bean sea destruido.
Podemos ver ambas interfaces en funcionamiento en el siguiente ejemplo. A continuación, podemos ver el único bean que vamos a crear por ahora, llamado ClientesServicio:

package com.openwebinars.lifecycle;

import org.springframework.beans.factory.DisposableBean;
import org.springframework.beans.factory.InitializingBean;

public class ClientesServicio implements InitializingBean, DisposableBean {


    String mensaje;

    public ClientesServicio() { }

    public ClientesServicio(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public void setMensaje(String mensaje) {
        this.mensaje = mensaje;
    }


    public void afterPropertiesSet() throws Exception {
        System.out.println("DESPUÉS DE INICIO");
    }

    public void destroy() throws Exception {
        System.out.println("ANTES DEL FIN");

    }

}
Como podemos apreciar, este bean implementa las ya citadas interfaces, InitializingBean y DisposableBean, lo cual nos obliga a darle cuerpo a los métodos afterPropertiesSet y destroy. En nuestro caso, al funcionalidad será didática, y tan solo imprimiremos por consola dos mensajes: uno que nos indica el final del inicio, y otro el principio del fin.

Si revisamos la ejecución, Spring ha ejecutado los métodos en el orden que cabía esperar:

En primer lugar, podemos ver la ejecución del método afterPropertiesSet, cuyo resultado es la línea DESPUÉS DEL INICIO.

Posteriormente, encontramos la impresión del propio mensaje.

Por último, como parte del mecanismo del cierre del contexto, se ha invocado el método destroy, dando como resultado el mensaje ANTES DEL FIN.
Ambos interfaces no tienen porque implementarse de forma conjunta; si necesitamos añadir algún tipo de funcionalidad solámente al inicio o al fin, podemos implmentar el interface necesario.

De las tres formas de implementar el manejo del ciclo de vida, esta es la menos adecuada, ya que acopla nuestro código a Spring. Cualquiera de las dos siguientes es más recomendable.

8.3 Uso de de las propiedades init-method y destroy-method
También podemos conseguir esta mismo funcionalidad sin necesidad de implementar ninguna interfaz adicional, y haciendo uso de la configuración XML.

Ambas propiedades esperan como valor el nombre de un método del bean (normalmente, definido como void). Dicho método será el que se ejecute, correspondientemente, tras la inicialización o antes de la destrucción del objeto.

Con tan solo unas pequeñas modificaciones, podemos comprobar el uso de estas propiedades con el código anterior:

Modificamos la clase ClientesServicio, y eliminamos la implementación de los interfaces, así como los correspondientes métodos, de forma que nos quede el siguiente código:
package com.openwebinars.lifecycle;

public class ClientesServicio {

    String mensaje;

    public ClientesServicio() { }

    public ClientesServicio(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public void setMensaje(String mensaje) {
        this.mensaje = mensaje;
    }

}
Añadimos al mismo los métodos que queremos que se ejecuten durante el ciclo de vida. Podemos llamarlos initBean y destroyBean (el nombre puede ser arbitrario). En cada uno de ellos, tan solo escribiremos un mensaje por consola:

package com.openwebinars.lifecycle;

public class ClientesServicio {

    String mensaje;

    public ClientesServicio() { }

    public ClientesServicio(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public void setMensaje(String mensaje) {
        this.mensaje = mensaje;
    }

    public void initBean()  {
        System.out.println("DESPUÉS DE INICIO");
    }

    public void destroyBean() {
        System.out.println("ANTES DEL FIN");

    }

}
Modificamos el fichero XML para añadir los atributos init-method y destroy-method, asignándole los valores correspondientes:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="clientesServicio" class="com.openwebinars.lifecycle.ClientesServicio"
        init-method="initBean" destroy-method="destroyBean">
        <property name="mensaje" value="Un mensaje"></property>
    </bean>
</beans>
Ejecutamos, y comprobamos que el resultado es el mismo.

8.4 Uso de de las anotaciones @PostConstruct y @PreDestroy
En este caso, el uso de las anotaciones y el código XML es fácilmente intercambiable, ya que tan solo tenemos que sustituir la propiedad XML por la anotación correspondiente sobre el método adecuado. Como podemos imaginar:

@PostConstruct se ejecutará tras la inicialización y
@PreDestroy se ejecutará antes de finalizar.
Estas anotaciones no son propias de Spring, sino que pertenecen al estándar JSR-250 de Java.

En segundo lugar, añadimos las anotaciones sobre el código Java:

package com.openwebinars.lifecycle;

import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;

public class ClientesServicio {


    String mensaje;

    public ClientesServicio() { }

    public ClientesServicio(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public void setMensaje(String mensaje) {
        this.mensaje = mensaje;
    }


    @PostConstruct
    public void initBean()  {
        System.out.println("DESPUÉS DE INICIO");
    }

    @PreDestroy
    public void destroyBean() {
        System.out.println("ANTES DEL FIN");

    }

}
Si al tratar de importar las depedencias de javax.annotation.PostConstruct y javax.annotation.PreDestroy comprobamos que STS no las localiza, es posible que tengamos que revisar con que versión de Java está configurado el proyecto. A partir de Java 6 lo tenemos disponible. Para cambiar la versión del JDK asociada a nuestro proyecto, podemos seguir los siguientes pasos:

Botón derecho sobre el proyecto > Properties

En la lista de la izquierda, seleccionamos Java Build Path, y de entre las pestañas de la derecha, seleccionamos Libraries.

Hacemos clic una vez sobre JRE System Library y pulsamos el botón Edit.

Seleccionamos, en Execution environment, alguna versión de Java superior o igual a la 6.
Java 8 es muy recomendable, puesto que ha incorporado novedades muy chulas, como el uso de funciones lambda, métodos default en las interfaces, mejoras en el tratamiento de fechas, nuevas excepciones…
Si ejecutamos ahora nos daremos cuenta de que… OUCH! ¿Y mis mensajes? Pues ha sucedido lo siguiente: para que Spring se encargue de escanear los beans en búsqueda de las anotaciones @PostConstruct y @PreDestroy, tenemos que decírslo explícitamente. Esto lo hacemos declarando un nuevo bean en nuestro fichero XML.

    <bean class="org.springframework.context.annotation.CommonAnnotationBeanPostProcessor"></bean>
Se trata de un bean especial (hay que indicar que no le establecemos la propiedad id) definido por Spring y que se encargará de escanear nuestros demás beans en la búsqueda de anotaciones definidas por la JSR-250, entre ellas, @PostConstruct y @PreDestroy.

8.5 Uso de BeanPostProcessor
El interfaz BeanPostProcessor define métodos callback que pueden ser implementados para añadir nuestra propia lógica de instanciación, de resolución de dependencias, etc. Si necesitas implementar alguna lógica después de que Spring container finalice la instanciación, configuración e inicialización del bean, se pueden conectar una o más implementaciones de BeanPostProcessor.

Object postProcessAfterInitialization(Object bean, String beanName): se ejecutará este código después de la inicialización de cualquier bean del contenedor.

Object postProcessBeforeInitialization(Object bean, String beanName): se ejecutará este código antes de la inicialización de cualquier bean del contenedor.
Para usarlo, tenemos que crear una clase propia, que implemente la interfaz org.springframework.beans.factory.config.BeanPostProcessor:

package com.openwebinars.beanpostprocessorsample;

import org.springframework.beans.BeansException;
import org.springframework.beans.factory.config.BeanPostProcessor;

public class CustomBeanPostProcessor implements BeanPostProcessor {

    public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
        System.out.println(String.format("Bean %s inicializado satisfactoriamente".toUpperCase(), beanName));
        return bean;
    }

    public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
        System.out.println(String.format("Inicializando bean %s".toUpperCase(),beanName));
        return bean;
    }

}
Además, lo tenemos que registrar en el fichero de configuración del contenedor, para que Spring lo pueda gestionar:

    ...
    <bean class="com.openwebinars.beanpostprocessorsample.CustomBeanPostProcessor"></bean>
    ...
Se pueden añadir tantos BeanPostProcessor como estimemos necesarios, para realizar diferentes tareas: loggin, validaciones, etc..



9.1 JavaConfig
Ya que esta va a ser la forma de configurar que menos vamos a usar por ahora, la aprenderemos primero.

Spring soporta el uso de la configuración mediante anotaciones sin tener que modificar (si no se desea) el código fuente. Para ello, hace uso, básicamente, de dos anotaciones: @Configuration y @Bean.

La anotación @Bean se usa para indicar a un metodo que va a instanciar, configurar e inicializar un nuevo objeto gestionado por Spring IoC container. Podemos decir, sin ningún lugar a dudas, que la anotación @Bean realiza la misma tarea que el elemento <bean> en la configuración por XML.

Si anotamos una clase con @Configuration, estamos diciendo que su principal propósito será la definición de una serie de beans.

Un ejemplo de fichero de configuración simple sería el siguiente:

@Configuration
public class AppConfig {

    @Bean
    public MyService myService() {
        return new MyServiceImpl();
    }

}
La clase AppConfig realiza las mismas tareas que el siguiente XML:

<beans>
    <bean id="myService" class="com.acme.services.MyServiceImpl"/>
</beans>
9.2 Anotaciones
También vamos a poder maridar el uso de anotaciones de forma conjunta con la configuración XML (y así evitar la creación de un fichero JavaConfig).

Configuración de los beans de escaneo de anotaciones
Para no tener que añadir a nuestro fichero de configuración referencias complejas a beans que define Spring, y que sirven, independientemente, para usar las diferentes anotaciones, podemos uasr un elemento que es capaz de resumir todas ellas en una línea de código, de forma que no tendremos que recordar si tenemos que registrar este u otro bean. El código es el siguiente: 
<context:annotation-config />
 Si lo añadimos en nuestro fichero, podremos comprobar que STS nos lanza un error, ya que no tenemos definido el namespace con prefijo context. Para ello, vamos a pulsar sobre la pestaña Namespaces del fichero bean.xml y seleccionaremos context tal y como podemos ver en la siguiente figura:

Selección del namespace context


Además, para que Spring escanee automáticamente un determinado paquete en busca de clases que estén anotadas como beans necesitamos otra anotación más: 
<context:component-scan base-package=""></context:component-scan>
 El valor de la propiedad base-package lo marcará la ruta del paquete donde tengamos ubicados los beans.
@Component es la anotación más básica, e indica que una clase será tratada como un bean. Estudiaremos más en profundidad esta anotación en la lección sobre estereotipos. Si la acompañamos de la anotación @Value, podemos inyectar algunos valores iniciales en nuestro bean.

@Component
public class Mundo {

    @Value("Hola Mundo!")
    private String saludo;

    public Mundo() { } 

    //...

}
A continuación, trabajaremos con las siguientes anotaciones

@Required: indicará que tenemos que satisfacer la dependencia en la configuración.

@Autowired: realiza la misma función que la propiedad autowire del elemento <bean>.

@Qualifier: que usada junto a @Autowired nos permite afinar más en la inyección automática.
9.2.1 Anotación @Required
La anotación @Required va a indicar que una determinada propiedad debe ser establecida en tiempo de configuración, a través de alguno de los mecanismos que ya conocemos:

Un elemento <property>

Un elemento <constructor-arg>

Autowiring
El contenedor lanzará una excepción si la propiedad afectada del bean no ha sido seteada. Esto nos permitirá evitar, desde una etapa muy temprana, excepciones del tipo NullPointerException.

    @Required
    private Provincia provincia;
9.2.2 Anotaciones @Autowire y @Qualifier
Estas anotaciones nos van a permitir realizar la inyección automática de beans, al igual que aprendimos a realizarlo en las lecciones anteriores a través de XML.

9.2.2.1 @Autowired
Podemos sustituir la anotación @Autowired, que es propia de Spring, con la anotación @Inject, que es propia del JSR330. Estas anotaciones son escaneadas de la misma forma que las anotaciones Spring. Tan solo hay que añadir los jar necesarios a nuestro classpath, mediante la siguiente dependencia: 
<dependency>
    <groupId>javax.inject</groupId>
    <artifactId>javax.inject</artifactId>
    <version>1</version>
</dependency>
Podemos usar la anotación @Autowired tanto para constructores, como para métodos setter:

public class MovieRecommender {

    private final CustomerPreferenceDao customerPreferenceDao;

    @Autowired
    public MovieRecommender(CustomerPreferenceDao customerPreferenceDao) {
        this.customerPreferenceDao = customerPreferenceDao;
    }

    // ...
}
 
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }
    // ...

}
Por defecto, el autowiring convierte las propiedades a las que afecta en @Required. Si queremos cambiar dicho comportamiento por defecto, lo podemos hacer mediante la siguiente propiedad de la anotación:

public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired(required=false)
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // ...

}
9.2.2.2 @Qualifier
Esta anotación nos permitirá afinar el trabajo a la hora de realizar la inyección de dependencias automática.

Supongamos que modificamos el fichero de configuración, beans.xml, de forma que registramos dos poblaciones diferentes:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.3.xsd">


    <context:annotation-config />

    <context:component-scan base-package="com.openwebinars.anotaciones.beans"></context:component-scan>

    <bean id="Sevilla" class="com.openwebinars.anotaciones.autowire.Provincia">
        <property name="nombre" value="Sevilla"></property>
    </bean>

    <bean id="SevillaCapital" class="com.openwebinars.anotaciones.autowire.Poblacion">
        <property name="nombre" value="Sevilla"></property>
    </bean>

    <bean id="MairenaAljarafe" class="com.openwebinars.anotaciones.autowire.Poblacion">
        <property name="nombre" value="Mairena del Aljarafe"></property>
    </bean>

    <bean id="cliente" class="com.openwebinars.anotaciones.autowire.Cliente">
        <property name="id" value="1"></property>
    </bean>

    <bean id="persona" class="com.openwebinars.anotaciones.autowire.Persona">
        <property name="nombre" value="Luismi"></property>
    </bean>


</beans>
Para indicarle, explícitamente, a Spring, cual es el bean que debe inyectar como dependencia, podemos usar la anotación @Qualifier sobre el código Java:

package com.openwebinars.anotaciones.autowire;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;

public class Persona {

    private String nombre;

    @Autowired
    @Qualifier("MairenaAljarafe")
    private Poblacion poblacion;

    public Persona() {
    }

    public Persona(String nombre, Poblacion poblacion) {
        this.nombre = nombre;
        this.poblacion = poblacion;
    }

    //...
}
De esta forma, la inyección del bean MairenaAljarafe se realiza correctamente en el bean Persona.

9.3 ¿Qué configuración es mejor? Anotaciones vs. XML
La introducción del enfoque de configuración basado en anotaciones planteó la pregunta de si dicho enfoque es mejor que XML. La respuesta inmedianta es que depende. Si profundiamos algo más en la respuesta, podemos decir que cada uno tiene sus ventajas, y por lo general será el desarrollador el responsable de elegir cual le conviene. Por como están definidas, las anotaciones proporcionan una gran cantidad de información in situ, de forma que la configuración es más concisa y breve. Sin embargo, XML es la mejor opción para conectar componentes sin tocar su código fuente y recompilarlos. Unos desarrolladores prefieren tener la información sobre la configuración cerca del código al que afecta, y otros argumentan que de esa forma está descentralizada y es más complicada de controlar.


No importa la elección, puesto que Spring soporta todas sus opciones con ambas; incluso utilizar ambas a la vez. Vale la pena destacar que el uso de anotaciones junto con la configuración de los beans a través de código java (JavaConfig) permite usar las anotaciones de forma no invasiva, sin necesidad de tocar el código fuente de las clases afectadas.
Spring Tool Suite soporta el uso de todos los métodos.



10.1 @Component y otras anotaciones de estereotipos
Spring nos provee de varias anotaciones de estereotipos: @Component, @Service, @Controller y @Repository (de esta última hablaremos en el bloque de Spring Data). @Component es un estereotipo genérico para cualquier componente manejado por Spring. @Repository, @Service y @Controller son especializaciones de @Component para casos de uso más específicos, de forma que las clases anotadas con las mismas se adaptarán mejor a esos casos (por ejemplo, @Service para la capa de servicios o lógica de negocio, o @Repository para la capa DAO o de acceso a datos).

10.2 Detección automática de clases y registro de las definiciones de los beans
Spring puede detectar automáticamente clases estereotipadas y registrar sus correspondientes BeanDefinition en nuestro contenedor. Sea el siguiente ejemplo:

package org.example;

@Service
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired
    public SimpleMovieLister(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

}
 
package org.example;

@Repository
public class JpaMovieFinder implements MovieFinder {
    // omitimos la implementación para poner el acento en la definición de la clase.
}
Para autodetectar estas clases y registrarlas en los correspondientes beans, podríamos usar el siguiente código de configuración XML:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">

    <context:component-scan base-package="org.example"/>

</beans>
Esto provocará que Spring escanee todas las clases definidas en el paquete org.example en busca de beans definidos con @Component o alguna de sus especializaciones, para registrarlos como beans.

En la lección anterior, descubrimos que existía un nuevo elemento, perteneciente al namespace context, que era <context:annotation-config />; este servía para escanear las diferentes anotaciones que podíamos haber añadido a los beans que estuvieran definidos en nuestro XML. El uso de la anotación <context:component-scan ... /> incluye implícitamente a <context:annotation-config />, con lo que solamente tendríamos que utilizar <context:component-scan ... />.
10.2.1 Filtrado y personalización del escaneo de beans
Por defecto, las clases anotadas con @Component, @Repository, @Service, @Controller son las candidatas a ser detectadas. Aun así, se puede modificar esta configuración añadiendo algunos filtros. Estos pueden ser de inclusión o de exclusión mediante los elementos <context:include-filter> y <context:exclude-filter>.

Tipo de filtro	Expresión de ejemplo	Descripción
Anotación (por defecto)	org.example.SomeAnnotation	Una anotación que debe estar presente en los componentes
Asignable	org.example.SomeClass	Una clase (o interfaz) que los componentes deben extender/implementar
Expresión regular	org\.example\.Default.*	Una expresión regular que debe ser cumplida por los nombres de los componentes.
Customizado	org.example.MyFilter	Una implementación propia del interfaz org.springframework.core.type.TypeFilter.
A continuación podemos ver un ejemplo de escaneo con filtrado, en el que se incluirán todas las clases de dos paquetes que cumplan una expresión regular, y excluiremos todas aquellas clases anotadas con @Repository:

<beans>
    <context:component-scan base-package="org.example">
        <context:include-filter type="regex" 
                expression="org.example.dao.*DAO.*" />
        <context:include-filter type="regex" 
                expression="org.example.services.*Service.*" />
        <context:exclude-filter type="annotation"
                expression="org.springframework.stereotype.Repository"/>
    </context:component-scan>
</beans>
Como podemos observar:

Se incluyen todas las clases del paquete org.example.dao que contengan DAO como parte de su nombre.

Se incluyen todas las clases del paquete org.example.service que contengan Service como parte de su nombre.

Se excluyen todas las clases anotadas con @Repository.
10.3 Ámbitos mediante anotaciones
Al igual que con los objetos gestionados por Spring en general, el ámbito por defecto y más usado es Singleton. De todas formas, habrá ocasiones (en el bloque de Spring MVC lo trabajaremos en profundidad) que necesitemos modificar esta configuración con la anotación @Scope. Veamos un ejemplo

@Scope("prototype")
@Repository
public class MovieFinderImpl implements MovieFinder {
    // ...
}
10.4 Uso de la anotación @Qualifier con estereotipos
La anotación @Qualifier, que trabajamos en la lección anterior, nos permitía afinar a la hora de inyectar una dependencia con autowiring. En este ejemplo podemos ver como realizar toda la configuración con anotaciones, y no usando XML para la definición, como en la lección pasada.

@Service
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired
    @Qualifier("hibernate")
    public SimpleMovieLister(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

}
 
@Repository
@Qualifier("hibernate")
public class JpaMovieFinder implements MovieFinder {
    // ...
}


11.1 Introducción
El desarrollo de software es una tarea complicada, la cual depende en gran medida de la experiencia de las personas involucradas, en particular de los desarrolladores.

El 80% de los aportes vienen del 20% del personal.
La comprensión del software es uno de los problemas más complicados en la tarea de mantenimiento y evolución.

El 80% del esfuerzo esta en el 20% del código desarrollado.
Uno de los pilares básicos de la Orientación a Objetos en el desarrollo de software es la búsqueda de la reutilización, que tendría las siguientes ventajas:

Reducción de tiempos.
Disminución del esfuerzo de mantenimiento.
Eficiencia.
Consistencia.
Fiabilidad.
Protección de la inversión en desarrollos.
Entre los diferentes mecanismos de reutilización están:

Componentes: elemento de software suficientemente pequeño para crearse y
mantenerse pero suficientemente grande para poder utilizarse.

Frameworks: bibliotecas de clases preparadas para la reutilización que pueden utilizar a su vez componentes.

Objetos distribuidos: paradigma que distribuye los objetos de cooperación a través de una red heterogénea y permite que los objetos interoperen como un todo unificado.

Patrones de diseño: sobre este último abundaremos un poco más.
Los patrones son una forma literaria para resolver problemas de
ingeniería del software, que tienen sus raíces en los patrones de la arquitectura. Los diseñadores y analistas de software más experimentados aplican de forma intuitiva algunos criterios que solucionan los problemas de manera elegante y efectiva. La ingeniería del software se enfrenta a problemas variados que hay que identificar para poder utilizar la misma solución (aunque matizada) con problemas similares.

Según Christopher Alexander, “Cada patrón describe un problema que ocurre una y otra vez en nuestro entorno, para describir después el núcleo de la solución a ese problema, de tal manera que esa solución pueda ser usada más de un millón de veces, sin hacerlo ni siquiera dos veces de la misma forma”.

Sobre patrones de diseño existe una gran cantidad de literatura, si bien uno de los documentos más básico es el libro “Design Patterns: Elements of Reusable Object-Oriented Software” (Gang of Four, [GoF]).

11.2 Patrón MVC (Modelo-Vista-Controlador)
El patrón de arquitectura MVC (Modelo Vista Controlador) es un patrón que define la organización independiente del Modelo (Objetos de Negocio), la Vista (interfaz con el usuario u otro sistema) y el Controlador (controlador del flujo o workflow de la aplicación).

De esta forma, dividimos el sistema en tres capas donde, como explicaremos más adelante, tenemos la encapsulación de los datos, la interfaz o vista por otro y por último la lógica interna o controlador.

El patrón de arquitectura “modelo vista controlador”, es una filosofía de diseño de aplicaciones, compuesta por:

Modelo
Contiene el núcleo de la funcionalidad (dominio) de la aplicación.

Encapsula el estado de la aplicación.

No sabe nada / independiente del Controlador y la Vista.

Vista
Es la presentación del Modelo.

Puede acceder al Modelo pero nunca cambiar su estado.

Puede ser notificada cuando hay un cambio de estado en el Modelo.

Controlador
Reacciona a la petición del Cliente, ejecutando la acción adecuada y creando el modelo pertinente.
Para entender cómo funciona nuestro patrón Modelo vista controlador, se debe entender la división a través del conjunto de estos tres elementos y como estos componentes se comunican unos con los otros y con otras vistas y controladores externos a el modelo principal. Para ello, es importante saber que el controlador interpreta las entradas del usuario (tanto teclado como el ratón), enviado el mensaje de acción al modelo y a la vista para que se proceda con los cambios que se consideren adecuados

A continuación, podemos ver el patrón expresado en una imagen:



El usuario solicita, usando algún dispositivo, algún recurso. Lo puede hacer escribiendo una URL en el navegador, pulsando un botón o desencadenando otro tipo de evento. Esta solicitud es recibida por el controlador.

El controlador, una vez recibida la solicitud, pasa a procesarla. Es posible que haya una parte del código que sirva para decidir quien será el método concreto que haga este procesamiento, y si para ello, hay que extraer algún dato recibido a través de la petición. A partir de ahí, invoca al modelo, para realizar la operación solicitada.

El modelo, que es la representación de los objetos de nuestro dominio, posiblemente necesite interaccionar con el repositorio donde tengamos almacenados los datos (ficheros, base de datos relacional, NoSQL, API REST, …), pidiendo unos datos y recibiendo los mismos.

Los datos obtenidos en el paso (3) son enviados al controlador, para que estos puedan ser, en última instancia, mostrados al usuario.

Antes de ser enviados, los datos pueden ser procesados. Cuando lo hayan sido, si fuera necesario, son inyectados en la vista.

La vista, con los datos necesarios a mostrar, se entrega al usuario.
11.2.1 Ventajas y desventajas del uso de MVC
Ventajas:
Soporte para múltiples vistas. Dado que la vista se haya separada del modelo, y no hay dependencia directa entre el modelo y la vista.

Adaptación al cambio. Los requisitos de la IU tienden a cambiar más rápidamente que las reglas de negocio.

Inconvenientes:
Complejidad. El patrón introduce nuevos niveles de indirección y por lo tanto aumenta ligeramente la complejidad de la solución (Spring MVC nos permitirá mitigar esto). Complejidad también en la depuración.

Costo de actualizaciones frecuentes. Desacoplar el modelo y la vista no significa que los desarrolladores del modelo puedan ignorar la naturaleza de las vistas.
11.3 Front Controller (Controlador frontal o de fachada)
El patrón Front Controller es usado en aplicaciones web para tener un mecanismo centralizado de recepción de peticiones, que será gestionadas por un solo objeto manejador. De esta forma, este manejador puede incorporar autenticación, autorización, logging, … antes de pasar la petición a su correspondiente manejador concreto.

En este patrón intervienen las siguientes entidades:

Controlador Frontal (Front Controller): Manejador único que gestionará todas las peticiones.

Despachador (Dispatcher): El controlador frontal deberá usar un despachador, que enviará cada petición a su correspondiente manejador.

Vista (View): el objeto esperado tras la petición.
A continuación, podemos ver el patrón expresado en una imagen:



Spring MVC implementa este patrón de una forma transparente para nosotros, a través del objeto org.springframework.web.servlet.DispatcherServlet, como veremos en las próximas lecciones.

11.3.1 Ventajas y desventajas del uso de MVC
Ventajas:
Tenemos centralizado en un único punto la gestión de las peticiones.

Aumentamos la reusabilidad de código.

Mejoramos la gestión de la seguridad.

Desventajas:
La velocidad de respuesta disminuye al tener que ser procesadas las peticiones primero por el controlador.
11.4 Patrón DAO (Data Access Object)
El acceso a los datos varía dependiendo de la fuente de los datos. El acceso al almacenamiento persistente, como una base de datos, varía en gran medida dependiendo del tipo de almacenamiento (bases de datos relacionales, bases de datos NoSQL, ficheros planos, etc.) y de la implementación del vendedor.

Toda aplicación web en el mundo real necesitan utilizar datos persistentes en algún momento. Para muchas de ellas, este almacenamiento persistente se implementa utilizando diferentes mecanismos. Por ejemplo, los datos podrían residir en sitemas heredados, repositorios LDAP, etc. Otro ejemplo es donde los datos los proporcionan servicios a través de sistemas externos como los sistemas de integración negocio-a-negocio (B2B), servicios de tarjetas de crédito, APIs REST, etc.

La solución a este problema nos la proporciona el patrón DAO: utilizar un Data Access Object (DAO) para abstraer y encapsular todos los accesos a la fuente de datos. El DAO maneja la conexión con la fuente de datos para obtener y almacenar datos.

El DAO implementa el mecanismo de acceso requerido para trabajar con la fuente de datos. Los componentes de negocio que tratan con el DAO utilizan un interface simple expuesto por el DAO para sus clientes. El DAO oculta completamente los detalles de implementación de la fuente de datos a sus clientes. Como el interface expuesto por el DAO no cambia cuando cambia la implementación de la fuente de datos subyacente, este patrón permite al DAO adaptarse a diferentes esquemas de almacenamiento sin que esto afecte a sus clientes o componentes de negocio. Esencialmente, el DAO actúa como un adaptador entre el componente y la fuente de datos.

A continuación, podemos ver el patrón expresado en un diagrama de clases:



ObjetoDeNegocio representa los datos del cliente. Es el objeto que requiere el acceso a la fuente de datos para obtener y almacenar datos.

DAO es el objeto principal de este patrón. Abstrae la implementación del acceso a datos subyacente, y permite un acceso transparente a la fuente de datos.

OrigenDeDatos representa la implementación de la fuente de datos, que podría ser un SGBDR, un ORM, un repositorio XML, un API REST, …

ObjetoDelModelo representa el objeto (o colección) que queríamos obtener o modificar.
Spring nos proporciona un amplio soporte para el uso de este patrón dentro de Spring Data.




12.1 Introducción
El desarrollo de aplicaciones web implica tener un conocimiento, al menos elemental, del funcionamiento del protocolo subyacente, HTTP. El Hypertext Transfer Protocol es un protocolo orientado a transacciones y que sigue un esquema de petición-respuesta entre un cliente y un servidor. Normalmente, un cliente (por ejemplo, un navegador web) realiza la petición de un recurso, localizable mediante su URL, frente a un servidor; este, al recibir dicha petición, devolverá una respuesta.

El protocolo no tiene estado. Esto significa que durante una conexión, no tenemos información sobre que ha sucedido en conexiones anteriores. Si un cliente realiza dos veces la misma petición a un servidor, atenderá la segunda petición exactamente igual que la primera. El hecho de no almacenar estados supone ventajas e inconvenientes frente al hecho de sí hacerlo, aunque algunos autores apuntan a que ha sido parte de su éxito. A día de hoy existen mecanismos auxiliares que nos permiten almacenar información entre peticiones (como por ejemplo las cookies).



Esquema de petición - respuesta de HTTP

12.2 URLs (Unified Resource Locator)
Una URL es una forma de localizar a un recurso en internet. El formato genérico es el siguiente:

protocolo://maquina:puerto/camino/al/recurso

Usualmente, el protocolo es HTTP o HTTPS, aunque se pueden utilizar otros (como por ejemplo FTP). La máquina es el nombre de la misma o su IP. Habitualmente se utiliza un nombre (por ejemplo, openwebinars.net), que es traducido a una IP por el servicio DNS. A continuación, se indica el puerto al cual nos queremos conectar; por defecto, HTTP tiene asignado el 80, y HTTPS el 443. Por último, camino/al/recurso es la ruta en el sistema de ficheros de la máquina remota; dicha ruta será relativa al directorio marcado como raiz de la web.

12.3 Peticiones y respuetas HTTP
Una petición HTTP no es más que un mensaje que un cliente enviará a un servidor HTTP, con un formato muy específico. Este mensaje tiene siempre una estructura dividida en dos partes: la cabecera (HEADER) y el cuerpo (BODY).

Dentro de la cabecera de una petición HTTP se envía siempre una serie de datos que son necesarios para que el servidor pueda responder, a saber:

Tipo de petición: GET, POST, … (los estudiaremos más adelante).

URL del recurso solicitado

Versión del protocolo

Quién realiza la petición (User-Agent)

….
Además, podemos añadir a la cabecera algunos datos específicos para una petición determinada, y que el servidor puede procesar para realizar alguna tarea auxiliar (por ejemplo, los datos de autenticación si solicitamos un recurso protegido).

Por otro lado, el cuerpo de la petición puede que esté vacío (o no) dependiendo del tipo de la misma. Un ejemplo de contenido del cuerpo de una petición sería los campos rellenados en un formulario, un fichero adjunto, etc…

12.3.1 Métodos de peticiones HTTP
El estándar del protocolo HTTP define una serie de métodos (también conocidos como verbos), que nos ayudarán a indicar qué estamos pidiendo exactamente al servidor con respecto a un recurso:

GET: solicita al servidor que envie el recurso identificado por la URL

HEAD: pide al servidor que envíe una respuesta idéntica a la que enviaría con GET, pero sin el cuerpo de la respuesta.

POST: envía datos al servidor para que sean procesados por el recurso identificado por la URL. Los datos se deben incluir en el cuerpo de la petición.

PUT: envía un recurso determinado (un archivo) al servidor. A diferencia que POST, este método crea una nueva conexión (socket) y la emplea para enviar el recurso, lo cual resulta más eficiente que enviarlo dentro del cuerpo del mensaje.

DELETE: solicita la eliminación el recurso especificado.

TRACE: solicita al servidor que envíe un mensaje de respuesta. Se utiliza para diagnosticar problemas de conexión.

OPTIONS: pide al servidor que le indique los métodos HTTP que soporta para una determinada URL.

PATCH: se emplea para modificar parcialmente un recurso ya existente en el servidor.
Existen varios tipos de petición más (CONNECT, SEARCH, MOVE, MERGE) definidos en sus respectivos RFC, y que quedan fuera del alcance de este curso.

Las peticiones más usuales suelen ser GET y POST, aunque el auge de los servicios web de tipo RESTful, íntimamente ligados al protocolo HTTP, han retomado el uso de otras, como DELETE, PUT o PATCH.

12.3.2 Respuestas HTTP
Una respuesta del servidor tiene una estructura parecida a la de una petición, también con una cabecera y un cuerpo. Como parte de la cabecera, normalmente recibiremos:

La versión de HTTP con la que trabaja el servidor

El código de estado o de respuesta, con su correspondiente frase de explicación.

Algunas cabeceras adicionales, como el tipo de contenido que recibidos, su longitud en bytes, etc…
Como cuerpo de la respuesta, como era de esperar, recibidos el recurso localizado.

El código de estado HTTP de la respuesta se utiliza para explicar que ha sucedido a la hora de realizar la petición. Están formados por tres dígitos, y pueden ser alguno de los siguientes:

Códigos 1XX: Mensajes
100-111 Conexión rechazada

Códigos 2XX: Operación realizada con éxito
200 OK

201-203 Información no oficial

204 Sin contenido

205 Contenido para recargar

206 Contenido parcial

Códigos 3XX: Redirección
301 Mudado permanentemente

302 Encontrado

303 Vea otros

304 No modificado

305 Utilice un proxy

307 Redirección temporal

Códigos 4XX: Error por parte del cliente
400 Solicitud incorrecta

402 Pago requerido

403 Prohibido

404 No encontrado

409 Conflicto

410 Ya no disponible

412 Falló precondición

Códigos 5xx: Error del servidor
500 Error interno

501 No implementado

502 Pasarela incorrecta

503 Servicio no disponible

504 Tiempo de espera de la pasarela agotado

505 Versión de HTTP no soportada
Hemos resaltado los códigos de respuesta más usuales que podemos encontrar en el día a día con HTTP.

12.4 Lenguajes, tecnologías y estándares de la WWW
Como indicábamos más arriba, HTTP es un protocolo de transferencia de hipertexto. Pero, ¿qué es eso del hipertexto? No es más que documentos de texto que pueden hacer referencia a otros documentos de texto. A día de hoy los conocemos como páginas web. La estructura de estos documentos viene definida en el ya archiconocido lenguaje HTML, si bien no es el único utilizado a día de hoy para crear contenido en la web.

HTML: Lenguaje de marcado de hipertexto. Sirve para la definición de la estructura y el contenido de documentos de hipertexto. Al ser un lenguaje de marcado, se puede escribir en texto plano y no necesita transformarse en código objeto ni nada por el estilo. Actualmente está vigente la versión 5.

CSS: lenguaje de estilos que permite, en interacción con HTML, modificar la forma en la que se presenta el contenido definido dentro de un documento web. La versión actual es la 3.0 y permite funcionalidades increibles, como gradientes, animaciones, transformaciones…

Javascript: es un lenguaje de scripting diseñado para usarse dentro de las páginas web. Inicialmente, nos permitía interaccionar con el Modelo de Objetos del Documento (DOM), si bien se ha convertido en una tecnología de mayor importancia y envergadura de lo que sus creadores soñaron inicialmente.

XML: se trata de un metalenguaje (un lenguaje para definir lenguajes) que nos permite estructurar información mediante un lenguaje de marcado, lo cual la hace interoperable entre sistemas heterogéneos.

AJAX: La unión de XML y las peticiones asíncronas con Javascript (AJAX) han revolucionado la web hasta transformarla en la conocida como Web 2.0, permitiendo crear servicios como Google Maps, Facebook, …
Todos estos lenguajes y tecnologías que hemos descrito anteriormente son de los que, normalmente, se utilizan en el conocido como lado cliente. Al otro lado, en el servidor, también existen una serie de tecnologías muy utilizadas en la actualidad y que también deben sonarnos.

Java: esta tecnología es omnipresente, y el campo de la web no podía ser menos. Java comenzó a mitad de los 90s con la incursión de los applets, pequeños programas embebibles dentro de una página web, y que permitieron crear las primeras aplicaciones web. Posteriormente, surgieron los Servlets y la tecnología JSP, que permitió la creación de aplicaciones web empresariales orientadas a la web.

PHP: Se trata de un popular lenguaje de programación que surgió para la creación de webs de contenido dinámico. Se trata de uno de los lenguajes más flexibles y potentes conocidos a día de hoy. Algunos de los servicios más utilizados del mundo, como Facebook, están implementados con él.

Python: Es otro popular lenguaje de programación multiparadigma y de código abierto. Tiene una gran cantidad de librerías que lo hacen un gran candidato para casi cualquier proyecto. En el caso de la web, el framework más utilizado es Django.

ASP.NET: Microsoft también tiene su tecnología del lado del servidor, llamada ASP.NET. Se trata de un framework para el desarrollo de aplicaciones web. Uno de los más extendidos es el que implementa aplicaciones a través del patrón MVC.

Ruby: se trata de un lenguaje de programación multiparadigma que se creó para que fuera altamente sencillo de programar, siguiendo el “principio de la menor sorpresa”. El framework más utilizado para el desarrollo web con este lengauje es Ruby on Rails.

13.1 Software a utilizar
Java SDK 1.7 o superior (preferiblemente 1.8)

Spring Tool Suite 3.8 (la última versión liberada hasta ahora 3.8.1)

Maven 2
13.2 Implementación del proyecto
13.2.1 Paso 1: Aplicación base y configuración del entorno
Para la creación de nuestro proyectos utilizaremos Maven, si bien antes de nada tendremos que matizar un poco esto.

Lo ideal sería que pudiéramos utilizar Maven como en el primer bloque del curso, es decir, utilizando un arquetipo para comenzar nuestra aplicación web. De hecho, en su catálogo oficial, Maven ofrece uno, llamado maven-archetype-webapp, que nos permitiría comenzar a trabajar. Sin embargo, este arquetipo incluye la limitación de que la versión de servlets que soporta por defecto es la 2.3 (bastante antigua). Si tratamos de cambiar esto para poder usar una versión posterior (al menos la 2.5, o idealmente la 3.0 o 3.1), podemos comprobar como entramos en un callejón sin salida. Por ello, afrontaremos los pasos iniciales mediante una alternativa, que nos permitirá usar Maven y la versión de servlets que queramos.
13.2.1.1. Paso 1.1: Creación del proyecto
Para comenzar, vamos a crear un nuevo Dynamic Web Project. Se trata de un tipo de proyecto, proporcionado por STS (Eclipse), y orientado a la creación de una aplicación web dinámica con JavaEE.



Creación de un Dynamic Web Project

Tras seleccionarlo, pulsamos Next, y en la siguiente ventana del asistente, tan escribimos el nombre del proyecto (HelloWorldSpringMVC o el nombre que deseemos). Seleccionamos también el servidor donde se ejecutará la aplicación (por defecto, la versión 3.8 de STS incluye una instancia del servidor Pivotal tc Server, que no es más que un Tomcat tuneado). Para la versión del módulo dinámico web (Dynamic Web module version) elegimos 3.1 (esto nos permitirá usar la versión 3.1 de los servlets).



Datos iniciales del proyecto

En el siguiente paso, no tenemos que hacer nada, y tan solo pulsamos Next.



Configuración de las carpetas que se incluirán en el Build Path.

Por último, en la ventana final del asistente, marcamos la opción de generación del descriptor del proyecto (Generate web.xml deployment descriptor) y pulsamos Finish.



Generación del proyecto incluyendo el descriptor de despliegue.

Al tratarse de un proyecto Java EE, nos invitará a cambiar la perspectiva de Eclipse (la forma en que se organizan las ventanas, cuantas se visualizan inicialmente…), pero podemos declinar dicha invitación y continuar con la perspectiva Spring.

13.2.1.2 Paso 1.2: Conversión del Dynamic Web Project a un proyecto Maven
Por defecto, un proyecto de tipo Dynamic Web Project no está preparado para poder usar Maven. Sin embargo, el entorno de desarrolo nos permite transformar un proyecto de cualquier tipo en un proyecto Maven, de forma que modifica su estructura en todos los elementos necesarios, y prepara un fichero pom.xml para poder añadir las dependencias necesarias.

Para realizar la transformación, pulsamos con el botón derecho sobre el proyecto, y seleccionamos Configure > Convert to Maven project.



Conversión a un proyecto Maven.

En la siguiente ventana, no tenemos que modificar ningún dato, y tan solo pulsamos Finish.



Finalización de la conversión del proyecto Maven.

Tras finalizar la conversión, tenemos la siguiente estructura de proyecto:



Estructura del proyecto

13.2.1.3 Paso 1.3: Añadimos las dependencias
Como ya hiciéramos en el bloque pasado, vamos a trabajar con una serie de dependencias para incorporar las librerías necesarias. Maven es muy generoso, y podemos hacerlo todo a través de una sola dependencia, que es la siguiente:

<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>${org.springframework.version}</version>
</dependency>
Si echamos un vistazo en el apartado <version>, podemos observar que, en lugar de un valor concreto, estamos usando una variable. Esto nos servirá en el caso de que utilicemos más de una dependencia Spring, para que siempre utilicemos la misma versión; y también, para que en caso de querer modificar la versión, podamos hacerlo en un lugar centralizado, y dicho cambio se propague a todas las dependencias. La definición de la propiedad se realiza fuera del elemento <dependencies>, de la siguiente forma:

<properties>
    <org.springframework.version>4.3.2.RELEASE</org.springframework.version>
</properties>
También vamos a usar los servlets; de hecho, en el paso anterior, elegimos la versión 3.1. Esa es la versión que tendremos que añadir como dependencia:

<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
</dependency>
Si además queremos usar la Java Standard Tag Library, es decir, el conjunto oficial de etiquetas para JSP, tenemos que añadir su dependencia:

<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
</dependency>
Por último, si queremos utilizar Log4j como sistema de logging, añadimos la dependencia correspondiente:

<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
</dependency>
13.2.2 Paso 2: Configuración de Spring MVC
Si bien profundizaremos en la estructura de Spring MVC en las lecciones posteriores, si podemos decir que un proyecto de Spring MVC no es más que un proyecto Java EE.

13.2.2.1 Paso 2.1: Configuración del descriptor de despliegue
Como proyecto Java EE que es, necesita una configuración de los servlets que vamos a utilizar (en nuestro caso, solamente uno, que se encargará de despachar todas las peticiones de la aplicación, a modo de Front Controller). Todo ello lo haremos en el fichero Webcontent/WEB-INF/web.xml:

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" id="WebApp_ID" version="3.1">
  <display-name>HelloWorldSpringMVC</display-name>
  <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app>
De esta forma, como decíamos anteriormente, indicamos que todas las peticiones sean atendidas por el controlador frontal.

13.2.2.2 Paso 2.2: Configuración del contexto
Spring MVC necesita una definición de su contexto, y por defecto, debe estar un fichero que se llame <nombredelservlet>-servlet.xml. Es decir, si el nombre de nuestro servlet es dispatcher, el fichero de configuración, que ubicaremos en el mismo directorio, debe llamarse dispatcher-servlet.xml.

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.3.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.3.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-4.3.xsd">

    <context:component-scan base-package="com.openwebinars.helloworld" />

    <mvc:annotation-driven />

    <bean id="viewResolver"
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="viewClass"
            value="org.springframework.web.servlet.view.JstlView" />
        <property name="prefix" value="/WEB-INF/jsp/" />
        <property name="suffix" value=".jsp" />
    </bean>

</beans>
13.2.2.3 Paso 2.3: Configuración de Log4j
Como en otras ocasiones, vamos a configurar Log4j para utilizarlo como sistema de logging. Para ubicar el fichero de properties, tenemos que crear una nueva carpeta, llamada resources, dentro de Java Resources. Para ello, tenemos que hacerlo desde la configuración del Build Path (botón derecho sobre el proyecto > Propiedades > Java Build Path).



Figura XX. Configuración del Build Path.

Pulsamos sobre el botón Add Folder, y en diálogo que nos aparece, pulsamos sobre el botón Create New Folder. Damos como nombre a la carpeta resources.
Pulsamos Finish, Ok, …



Creación de la carpeta (1)



Creación de la carpeta (2)

Ahora, dentro de esta carpeta, es donde podemos ubicar el fichero de propiedades de log4j, llamado log4j.properties, y cuyo contenido puede ser el siguiente:

log4j.rootCategory=INFO, stdout

log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{ABSOLUTE} %5p %t %c{2}:%L - %m%n

log4j.category.org.springframework.beans.factory=DEBUG
A partir de ahora, vamos a definir nuestro primer controlador y una vista a mostrar.

13.2.3 Paso 3: La vista y el controlador
13.2.3.1 Paso 3.1: El controlador, una clase muy simple
Spring nos facilita mucho la creación de controladores, que podrán realizar toda la lógica de negocio de nuestra aplicación antes de enviar los datos a la vista. De hecho, como podremos comprobar, se tratará de una clase POJO (Plain Old Java Object), que no debe heredar de ninguna clase especial. Creamos una nueva clase, llamada HelloController, dentro del paquete com.openwebinars.helloworld. Veamos el código y desgranémoslo:

package com.openwebinars.helloworld;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class HelloController {

    @RequestMapping("/hello")
    public String sayHello(Model model) {        
        model.addAttribute("saludo", "Hola Mundo!!!");
        model.addAttribute("mensaje","Me llena de orgullo y satisfacción saludaros en este primer ejemplo de Spring MVC");
        model.addAttribute("url", "http://www.openwebinars.net");
        return "hello";
    }    
}
Lo primero que llama la atención es la simplicidad de la clase: es java en estado puro. Se trata una simple clase java, anotada con @Controller. Eso, unido a la configuración declarada en el fichero dispatcher-servlet.xml, harán que Spring se encargue del resto.

La clase tiene un solo método, cuya firma es public String sayHello(Model model):

Como decíamos más arriba, el tipo de retorno es String, ya que devolverá el nombre de una vista.

Como argumento, recibe un elemento de tipo Model. Sera el contenedor que nos permita añadir datos que serán transportados a la vista.

Además, está anotado con RequestMapping("/hello"). De esta forma indicamos que cualquier petición hacia la url http://máquina:puerto/HelloWorldSpringMVC/hello será procesada por este método.
Ahora, nos toca crear la vista.

13.2.3.2 Paso 3.2: Creación de la vista
Para crear la vista, vamos a crear previamente una carpeta que las almacene todas, dentro de WEB-INF, y que se llamará jsp. (También podemos eliminar la carpeta WEB-INF/lib, ya que al usar Maven, no sirve para nada).





Creación de la carpeta WEB-INF/jsp, que almacenará todas las vistas.

Ahora, ya podemos proceder a la creación de nuestro fichero de vista, que se llamará hello.jsp.







Creación del fichero JSP

Inicialmente, la plantilla que tiene definida STS para una página JSP está pensada para usar HTML4. Vamos a realizar algunos cambios:

Cambiaremos la codificación de ISO-8859-1 a UTF-8.

Vamos a usar HTML5 en lugar de HTML4.

Además, usaremos como base bootstrap, lo cual nos permitirá tener una web de apariencia profesional y responsiva con muy poco esfuerzo por nuestra parte.
Abrimos el navegador, y entramos en http://getbootstrap.com. Accedemos a Getting started y encontramos la plantilla base. Modificamos los enlaces de bootstrap, para no tener que descargar los ficheros y que los tome directamente el respositorio oficial:

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.3/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>


    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
  </body>
</html>
Ahora, vamos a definir la información que queremos visualizar. Si revisamos el código del controlador, hemos añadido al modelo:

Un saludo, que mostraremos en grande.

Un mensaje, que mostraremos debajo.

Un enlace, que usaremos para que los usuarios puedan visitar otra web.
Podemos utilizar una de las plantillas base de bootstrap para copiar el código, que es bastante fácil:

    <div class="jumbotron">
      <div class="container">
        <h1>${saludo}</h1>
        <p>${mensaje}</p>
        <p><a class="btn btn-primary btn-lg" target="_blank" href="${url}" role="button">Learn more &raquo;</a></p>
      </div>
    </div>
Además, encontramos que hemos usado Expression Language, una característica que JSP que nos permite utilizar un lenguaje sencillo para usar un JavaBean dentro de una página JSP. ${saludo} buscará dentro del contexto una variable llamada saludo, y mostrará su valor. Lo mismo sucede con ${mensaje}. Como vemos, ${url} nos sirve para definir el elemento href del enlace.

13.2.4 Paso 4: Ejecución
Una vez que tenemos definido nuestro proyecto, lo hemos configurado, y hemos añadido una vista y un controlador, vamos a pasar a ejecutarlo. Para ello, tan solo tenemos que pulsar sobre el proyecto con el botón derecho > Run As > Run on Server. Ello hará que nos aparezca el siguiente diálogo:



Diálogo de ejecución del proyecto

Tan solo pulsamos sobre Finish, y el servidor comenzará a ejecutarse, desplegandose nuestra aplicación y lanzando el navegador que esté configurado. Y ¡sorpresa! Nos encontramos con el error 404. Esto se debe a que no hemos definido una página de bienvenida. Sin embargo, si recordamos, nuestro controlador iba a escuchar la url http://maquina:puerto/nombredelproyecto/hello. Si la escribimos en el navegador, veremos que aparece nuestra esperada vista.



Hola Mundo ejecutandose



14.1 Introducción
Los controladores proveen de acceso a la aplicación que está por debajo, normalmente, a través de servicios. En principio, podemos hacer uso de las anotaciones @Controller y @RequestMapping para poder definir un controlador y como se va a acceder a él.

Por otro lado, una de las áreas donde sobresale Spring es en la separación de la vista (y su implementación) del resto del framework MVC. Por ejemplo, podemos utilizar Thymeleaf o Freemarker en lugar de un código JSP inicial. Nosotros trabajaremos con JSP, que es una tecnología sencilla y eficaz, y parte del estándar de Java EE, si bien, en esta lección, vamos a presentar otras posibidades existentes.

14.2 Definición (básica) de un controlador con @Controller
La anotación @Controller indica que una clase particular tiene el rol de un controlador. Spring no obliga a que extendamos ninguna clase base o que hagamos referencia al API de los Servlets. @Controller actua como un estereotipo de la clase anotada. El dispatcher escanea las clases anotadas y detecta las anotaciones @RequestMapping (que veremos más adelante). Para habilitar la autodetección, tenemos que definir el escaneo automático en la configuración de nuestro contenedor:

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.3.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.3.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-4.3.xsd">

    <context:component-scan base-package="com.openwebinars.springmvc" />

    <mvc:annotation-driven />

    <bean id="viewResolver"
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="viewClass"
            value="org.springframework.web.servlet.view.JstlView" />
        <property name="prefix" value="/WEB-INF/jsp/" />
        <property name="suffix" value=".jsp" />
    </bean>

</beans>
14.2.1 Mapeo de peticiones con @RequestMapping
Podemos usar la anotación @RequestMapping para mapear URLs, como /appointments, sobre una clase, o un método en particular. Normalmente, la anotación a nivel de clase sirve para mapear a un controlador de formulario; y las anotaciones a nivel de método adicionales para concretar elementos específicos de cada anotación (parámetros adicionales, verbo de la petición: GET, POST, …), etcétera.

Sea el siguiente fragmento de código de una aplicación de ejemplo:

@Controller
@RequestMapping("/profesor")
public class ProfesorController {

    @Autowired
    private ProfesorService profesorService;

    @RequestMapping(value="/list", method = RequestMethod.GET)
    public String listado(Model model) {

        model.addAttribute("profesores", profesorService.getProfesores());
        return "list";
    }

    @RequestMapping(value="/detail/{idProf}", method = RequestMethod.GET)
    public String detalle(@PathVariable("idProf") int id, Model model) {

        model.addAttribute("profesor", profesorService.getById(id));

        return "detail";
    }

    public void setProfesorService(ProfesorService profesorService) {
        this.profesorService = profesorService;
    }
}
En este ejemplo, @RequestMapping se usa en varios lugares. El primer uso es a nivel de clase que indica que todos los métodos de la misma trabajarán sobre la ruta relativa /profesor. El método listado(...) tiene una concreción de @RequestMapping: solamente acepta peticiones de tipo GET que se realicen a la url /list. El método detalle(...) tiene una concreción similar y también nos muestra otro elemento a usar con @RequestMapping: las URI templates (que aprenderemos más adelante).

La anotación @RequestMapping a nivel de clase no es obligatoria; de no haberla, todas las rutas en las anotaciones de los métodos serán absolutas y no relativas, como podemos ver en el siguiente ejemplo:

@Controller
public class ClinicController {

    private final Clinic clinic;

    @Autowired
    public ClinicController(Clinic clinic) {
        this.clinic = clinic;
    }

    @RequestMapping("/")
    public void welcomeHandler() {
    }

    @RequestMapping("/vets")
    public ModelMap vetsHandler() {
        return new ModelMap(this.clinic.getVets());
    }
}
14.2.2 Variantes compuestas de @RequestMapping
La versión 4.3 de Spring Framework introduce una serie de variantes compuestas de la anotación @RequestMapping para ayudar a simplificar los méotodos HTTP más comunes expresar mejor la semántica del método anotado. Tenemos a nuestra disposición las siguientes:

@GetMapping
@PostMapping
@PutMapping
@DeleteMapping
@PatchMapping
A continuación, podemos ver una modificación del ejemplo AppointmentsController usando las anotaciones compuestas:

@Controller
@RequestMapping("/profesor")
public class ProfesorController {

    @Autowired
    private ProfesorService profesorService;

    @GetMapping(value="/list", method = RequestMethod.GET)
    public String listado(Model model) {

        model.addAttribute("profesores", profesorService.getProfesores());
        return "list";
    }

    @GetMapping(value="/detail/{idProf}", method = RequestMethod.GET)
    public String detalle(@PathVariable("idProf") int id, Model model) {

        model.addAttribute("profesor", profesorService.getById(id));

        return "detail";
    }

    //...
}
14.2.3 ¿Qué firma debe tener un método anotado con @RequestMapping?
Los métodos manejadores, anotados con @RequestMapping, pueden tener firmas de lo más variado. La mayoría de los argumentos que pueden recibir pueden ser usados en un orden arbitario, a excepción de los de tipo BindingResult. A lo largo de las siguiente lecciones iremos usando las más usuales. Veamos las posibilidades existentes.

14.2.3.1 Tipos de argumentos soportados
Spring MVC soporta los siguientes tipos de datos como argumentos de un método anotado como @RequestMapping (destacamos en negrita los más utilizados):

Objetos request y response, del API Servlet (por ejemplo, ServletRequest o HttpServletRequest).

Objetos de sesión, del tipo HttpSession.

org.springframework.web.context.request.WebRequest o org.springframework.web.context.request.NativeWebRequest. Nos dan acceso a los objetos de tipo petición, sin necesidad del uso del API Servlet.

java.util.Locale, que nos da la información de la zona geográfica (idioma, moneda, …)

java.util.TimeZone (Java 6+) / java.time.ZoneId (en Java 8), para saber la zona horaria asociada a la petición.

java.io.InputStream / java.io.Reader para acceder al contenido de la petición en formato raw (Servlet API).

java.io.OutputStream / java.io.Writer para generar el contenido de la respuesta, también en formato raw (Serlvet API).

org.springframework.http.HttpMethod, para determinar el método (verbo) HTTP de la petición (es una enumeración).

java.security.Principal, conteniendo el usuario actualmente autenticado.

Argumentos anotados con @PathVariable para acceder a variables dentro de la URI (profundizaremos en capítulos posteriores).

Argumentos anotados con @MatrixVariable (también profundizaremos en lecciones posteriores).

Argumentos anotados @RequestParam, para acceder a los parámetros de la petición (Servlet API). Los estudiaremos con detenimiento más adelante.

Argumentos anotados con @RequestHeader para acceder a las cabeceras de la petición HTTP (Servlet API).

Argumentos anotados con @RequestBody, para acceder al cuerpo de la petición. Estos parámetros se convierten en el tipo declarado para el argumento usando objetos de tipo HttpMessageConverters.

Argumentos anotados con @RequestPart, para acceder al contenido de una petición de tipo “multipart/form-data” (lo aprenderemos junto con la subida de ficheros).

Argumentos anotados con @SessionAttribute para acceder a atributos almacenados permanentemente en la sesión, como por ejemplo el objeto usuario, en oposición al almacenamiento de objetos del modelo almacenados temporalmente en la sesión usando @SessionAttributes.

Argumentos anotados con @RequestAttribute para acceder a los atributos de la petición.

Parámetros de tipo HttpEntity<?>, para acceder a la petición HTTP (Servlet API), tanto las cabeceras como el contenido.

java.util.Map / org.springframework.ui.Model / org.springframework.ui.ModelMap para dar contenido al modelo implícito expuesto en la vista.

org.springframework.web.servlet.mvc.support.RedirectAttributes para especificar el conjunto específico de atributos a utilizar en caso de redirección.

Objetos de tipo comando o formulario, para enlazar directamente con propiedades de los beans. Se puede usar la anotación @ModelAttribute para customizar el nombre.
org.springframework.validation.Errors / org.springframework.validation.BindingResult resultados de la validación del objeto que le precede en la firma.

org.springframework.web.bind.support.SessionStatus gestión del estado para marcar el procesamiento de un formulario como completo, lo cual disparará el mecanismo limpieza de los atributos de sesión marcados por @SessionAttributes.

org.springframework.web.util.UriComponentsBuilder un builder para acceder a UriComponents (acceso seguro a las diferentes partes de la URL: host, puerto, contexto, query, … ).
14.2.3.2 Tipos de datos de retorno soportados
Destacamos en negrita los más utilizados:

Un objeto de tipo ModelAndView, con el modelo enriquecido con los objetos necesarios para la vista.

Un objeto de tipo Model, con el nombre determinado implicitamente a través de un objeto de tipo RequestToViewNameTranslator.

Un objeto de tipo Map con los valores del modelo, con el nombre determinado implicitamente a través de un objeto de tipo RequestToViewNameTranslator.

Un objeto de tipo View, con todos los valores necesarios añadidos. El método manejador debe también recibir un objeto de tipo Model y añadir a él la información a enviar a la vista.

Una cadena de caracteres (String), que es interpretada como el nombre lógico de la vista. El método manejador debe también recibir un objeto de tipo Model y añadir a él la información a enviar a la vista.

void si el método maneja la respuesta el mismo (escribiendo el contenido de la respuesta él solo, declearando un argumento de tiop ServletResponse/HttpServletResponse) o si el nombre de la vista se puede determinar a través de RequestToViewNameTranslator.

Si el método está anotado con @ResponseBody, el valor de retorno será convertido por el correspondiente HttpMessageConverters.

Un objeto de tipo HttpEntity<?> o ResponseEntity<?> provee de acceso al objeto respuesta (via Servlet API), tanto a sus cabeceras como su contenido. Este objeto será convertido por su correspondiente HttpMessageConverters.

Un objeto de tipo HttpHeaders para devolver una respuesta sin cuerpo.

Un objeto de tipo Callable<?>, si se quiere devolver la respuesta de forma asíncrona.

Un objeto de tipo DeferredResult<?> para devolver el objeto de forma asíncrona, gestionando nosotros mismos los hilos de ejecución.

Un objeto de tipo ListenableFuture<?>, similar al anterior.

Un objeto de tipo ResponseBodyEmitter para escribir varios objetos en la respuesta de forma asíncrona.

Un objeto de tipo SseEmitter

Un objeto de tipo StreamingResponseBody

Otro tipo de retorno será considerado como un objeto solo expuesto hacia la vista.
14.3 Posibles tecnologías a usar para la vista
14.3.1 Thymeleaf
Thymeleaf es un buen ejemplo de tecnología que encaja perfectamente con el framework MVC. El soporte para esta integración no lo ofrece Spring, sino el propio equipo de desarrollo de Thymeleaf.

Se trata de un motor de plantillas, que nos permite trabajar de forma que nuestro código es visualizable desde un navegador si necesidad de un servidor (no ocurre lo mismo con JSP). De esta forma, es muy fácil integrar el trabajo de maquetadores y diseñadores junto con el de los desarrolladores. Para poder trabajar de esta manera, su sintaxis se basa solamente en atributos. A continuación, podemos ver un ejemplo de una tabla que obtiene sus valores de un List<Producto> llamado listaProductos:

<table>
  <thead>
    <tr>
      <th th:text="#{msgs.cabeceras.nombre}">Nombre</th>
      <th th:text="#{msgs.cabeceras.precio}">Precio</th>
    </tr>
  </thead>
  <tbody>
    <tr th:each="prod : ${listaProductos}">
      <td th:text="${prod.nombre}">Naranjas</td>
      <td th:text="${#numbers.formatDecimal(prod.precio,1,2)}">0.99</td>
    </tr>
  </tbody>
</table>
14.3.2 Groovy Markup Templates
Si estás familiarizado con Groovy, esta puede ser otra alternativa. Groovy es un lenguaje dinámico, orientado a objetos, muy íntimamente ligado a Java. EL 99% del código Java existente puede ser compilado mediante Groovy, y el 100% del código Groovy es convertido en bytecode Java, y ejecutado en tu JVM de manera natural. Groovy simplifica la sintaxis de Java hasta lo realmente necesario para expresar lo que queremos hacer, y ademas añade una serie de métodos tremendamente útiles al JDK, convirtiendo multitud de tareas en un placer.

La sintaxis de Groovy es una especie de código Java minimalista, eliminando la mayor parte del código “innecesario” (por innecesario nos referimos al código que no es estrictamente necesario para ejecutar la acción que deseamos). Esto, que a priori podría parecernos una dificultad, haciéndonos pensar que tenemos que aprender un nuevo lenguaje, no lo es, pues como se hemos mencionado, casi todo el código Java puede ser compilado con Groovy.

Groovy Markup Template es un motor de plantillas que, en primera instancia, está pensado para generar cualquier XML. Como es de esperar, requiere que incluyamos Groovy (2.3.1+) dentro del classpath (a través de la correspondiente dependencia Maven).

A diferencia de otros generadores de plantillas, Groovy Markup Template usa un lenguaje específico (llamado DSL: Domain Specific Language) para construir la plantilla. A continuación podemos ver un sencillo ejemplo:

yieldUnescaped '<!DOCTYPE html>'
html(lang:'en') {
    head {
        meta('http-equiv':'"Content-Type" content="text/html; charset=utf-8"')
        title('My page')
    }
    body {
        p('This is an example of HTML contents')
    }
}
14.3.3 Velocity y Freemarker
Se trata de dos lenguajes de plantillas que funcionan de una forma parecida, y por eso los conoceremos de forma conjunta. Aun así, el soporte para Velocity (por parte de Apache) se abandonó hace tiempo, así que para nuevos proyectos, es más recomendable el uso de Freemarker.

Apache Freemarker

Apache Freemarker

Como podemos apreciar en la figura anterior, este tipo de lenguaje de plantillas trabaja metiendo en la coctelera dos elementos, por un lado, objetos Java, y por otro, plantillas, de forma que es capaz de ser rederizado creando una salida con los valores de los objetos inyectados dentro de las plantillas.

Cómo podemos ver en el siguiente código, tiene una sintaxis sencilla y muy similar a otras ya conocidas, como JSP+EL:

<!DOCTYPE html>

<html lang="en">

<body>
    Date: ${time?date}
    <br>
    Time: ${time?time}
    <br>
    Message: ${message}
</body>

</html>
14.3.4 JSP y JSTL
Spring nos provee de una integración eficaz y lista para usar para JSP y JSTL (sin necesidad de configuración adicional, como en las opciones anteriores). Tan solo tenemos que preocuparnos de generar nuestro código JSP y Spring será capaz de renderizar la vista.

En las próximas lecciones hablaremos de la creación de formularios para Spring con JSP-JSTL y de como configurar la resolución de la vista.


15.1 Introducción
En versiones anteriores de Spring, los programadores estaban obligados a definir uno más beans mapeadores de URLs (HandlerMapping) las peticiones entrantes a los manejadores o controladores apropiados.

La introducción del uso de las anotaciones @RequestMapping nos evita realizar esta tediosa tarea. Sin embargo, puede existir algún contexto en el que aun no interese definir nuestro propio mapeador de URLs, como por ejemplo si queremos implementar un interceptor propio.

El siguiente ejemplo nos muestra como definir un interceptor:

<beans>
    <bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping">
        <property name="interceptors">
            <bean class="example.MyInterceptor"/>
        </property>
    </bean>
<beans>
15.2 Intercepción de peticiones con un HandlerInterceptor
El manejador de mapeo de Spring incluye un manejador de interceptores, que es muy útil cuando queremos asociar una funcionalidad a determinadas peticiones.

Los interceptores, ubicados en el manejador de mapeo, deben implementar HandlerInterceptor del paquete org.springframework.web.servlet. Este interfaz define algunos métodos:

preHandle(...), que se llama antes de que se ejecute el manejador.
postHandle(...), que se llama después de que se ejecute el manejador.
afterCompletion(...) que se llama después de que se haya finalizado la petición por completo.
El método preHandle(...) devuelve un booleano, que podemos utilizar para continuar o no con la petición.

Los interceptores se pueden configurar usando la propiedad interceptors presente en todos los HandlerMapping.

El siguiente ejemplo, que podemos utilizar en el proyecto de la lección anterior, nos permite restringir el horario en el cual se aceptarán peticiones.

<beans>
    <bean id="handlerMapping"
            class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping">
        <property name="interceptors">
            <list>
                <ref bean="officeHoursInterceptor"/>
            </list>
        </property>
    </bean>

    <bean id="officeHoursInterceptor"
            class="samples.TimeBasedAccessInterceptor">
        <property name="openingTime" value="9"/>
        <property name="closingTime" value="18"/>
    </bean>
</beans>
En el caso de queramos usar la anotación <mvc:annotation-driven tendremos una dificultad, ya que esta pisa la definición del interceptor. Para poder maridar el uso de esta anotación con la definición de un interceptor, Spring MVC nos ofrece la siguiente alternativa:

<beans>
    ...
    <mvc:interceptors>
        <bean
            class="com.openwebinars.springmvc.interceptors.TimeBasedAccessInterceptor">
            <property name="openingTime" value="9" />
            <property name="closingTime" value="18" />
        </bean>
    </mvc:interceptors>
    ...
</beans>
El código Java del interceptor sería el siguiente:

public class TimeBasedAccessInterceptor extends HandlerInterceptorAdapter {

    private int openingTime;
    private int closingTime;

    public void setOpeningTime(int openingTime) {
        this.openingTime = openingTime;
    }

    public void setClosingTime(int closingTime) {
        this.closingTime = closingTime;
    }

    public boolean preHandle(HttpServletRequest request, HttpServletResponse response,
            Object handler) throws Exception {
        Calendar cal = Calendar.getInstance();
        int hour = cal.get(HOUR_OF_DAY);
        if (openingTime <= hour && hour < closingTime) {
            return true;
        }
        response.sendRedirect("http://host.com/outsideOfficeHours.html");
        return false;
    }
}



16.1 Patrones de URI templates
Las URI templates puede ser usadas para acceder convenientemente a determinadas partes de las URLs en un método anotado con @RequestMapping.

Una URI template no es más que una cadena de caracteres que expresa una URI, pero con uno o más nombres de variables. Cuando se sustituyen esas variables por valores concretos, obtenemos una URI. En Spring MVC podemos usar la anotación @PathVariable en un argumento de un método para enlazar dicho valor con una variable de la URI template:

@RequestMapping(value="/detail/{idProf}", method = RequestMethod.GET)
    public String detalle(@PathVariable("idProf") int id, Model model) {       
        model.addAttribute("profesor", profesorService.getById(id));
        return "detail";
    }
La plantilla /detail/{idProf} especifica el nombre de variable idProf. Cuando el controlador maneja esta petición, el valor de la misma es seteado con el valor encontrado en la parte adecuada de la URI. Por ejemplo, si nos llega una petición con detail/3, el valor de idProf es 3 .

Si anotamos con @PathVariable a un argumento de tipo Map<String, String>, este será seteado con todas las variables de la URI template.

Se pueden combinar URI templates en anotaciones a nivel de clase y de método, o en varias partes del método. Por ejemplo:


@Controller
@RequestMapping("/profesor")
public class ProfesorController {

    //...    

    @RequestMapping(value="/detail/{idProf}/asig/{posAsig}") 
    public String asignatura(@PathVariable("idProf") int idProf, @PathVariable("posAsig") int posAsig, Model model) {   

        model.addAttribute("asignatura", profesorService.getById(idProf).   
                                        getListadoAsignaturas().get(posAsig));

        return "asig";


    }
Un argumento anotado con @PathVariable puede ser de tipo simple: int, long, Date, etc. Spring automáticamente lo convierte al tipo de dato adecuado, o lanza una excepción de tipo TypeMismatchException si falla al hacerlo. También se puede registra el soporte para parsear tipos de datos adicionales.

Si anotamos con @PathVariable a un argumento de tipo Map<String, String>, este será seteado con todas las variables de la URI template.

@Controller
@RequestMapping("/profesor")
public class ProfesorController {

    //...

    @RequestMapping(value="/detail/{idProf}/asigMap/{posAsig}") 
    public String asignaturamap(@PathVariable Map<String, String> params, Model model) {    

        int idProf = Integer.parseInt(params.get("idProf"));
        int posAsig = Integer.parseInt(params.get("posAsig"));

        model.addAttribute("asignatura", profesorService.getById(idProf).getListadoAsignaturas().get(posAsig));

        return "asig";


    }
16.2 Parámetros de peticiones y valores de cabeceras
Podemos concretar las anotaciones para el mapeo de URLs con parámetros incluidos dentro de las cabeceras, con condiciones “header“, “!header“ o “`header=valor“. Las dos primeras nos hablan de la presencia o ausencia del parámetro, y la tercera de que tenga un valor concreto.

@Controller
@RequestMapping("/owners/{ownerId}")
public class RelativePathUriTemplateController {
    @GetMapping(path = "/pets", headers = "myHeader=myValue")
    public void findPet(@PathVariable String ownerId, @PathVariable String petId, Model model) {

            //implementación omitida
    }
}



17.1 Resolviendo la vista
Cualquiera de los métodos controladores que hemos visto debe resolver en una vista, ya sea explícitamente (devolviendo un valor: String, View, ModelAndView) o implícitamente (siguiendo una convención).

Spring proporciona la interaz ViewResolver, y algunos subtipos de la misma. La tabla completa la podemos encontrar en la documentación de Spring.

Por ejemplo, si usamos JSP, podríamos utilizar UrlBasedViewResolver o InternalResourceViewResolver. Este view resolver transforma el nombre de una vista en una URL que, tras ser despachada, es capaz de renderizar.

<bean id="viewResolver"
        class="org.springframework.web.servlet.view.UrlBasedViewResolver">
    <property name="viewClass" value="org.springframework.web.servlet.view.JstlView"/>
    <property name="prefix" value="/WEB-INF/jsp/"/>
    <property name="suffix" value=".jsp"/>
</bean>
 
@Controller
@RequestMapping("/baseurl")
public class MyController {

    @GetMapping("/method")
    public String mymethod() {

        //resto del código        

        return "test";
    }

}
Si un método devuelve la cadena de caracteres test, el despachador nos enviará finalmente a la url /WEB-INF/jsp/test.jsp.

17.2 El prefijo redirect:
Como se ha dicho antes, cuando un método del controlador devuelve una valor, este se transforma en URL y entonces somos despachados hacia la misma.

Para aquellos que provengan de programar con Servlets, les sonará la clase RequestDispatcher, que es la encargada de poder enviarnos desde un controlador (en el mundo Java, un servlet) hacia una vista.

Hablando de una forma amplia, si nosotros escribimos en nuestro navegador la url http://www.myserver.com/baseurl/method, estaremos invocando al controlador; y este, a través del valor que devuelva y el ViewResolver configurado, nos llevará a la vista. Sin embargo, en nuestro navegador, la url no habrá cambiado, y seguirá siendo http://www.myserver.com/baseurl/method.

En cambio, si en el método controlador, usamos el prefijo redirect:, esto supondrá un cambio de la url. Como norma amplia, deberíamos usar este prefijo cada vez que terminemos una gestión. Por ejemplo, si decidimos dar de alta un nuevo registro (pongamos de tipo profesor), el controlador nos debería llevar primero al formulario (GET) y de ahí al método que lo almacene en la base de datos (POST). Si todo va bien, cuando este método termine, nos debería redirigir a otra página (por ejemplo, al listado), ya que hemos terminado la gestión de alta de un profesor.

@Controller
@RequestMapping("/baseurl")
public class MyController {

    @GetMapping("/other")
    public String mymethod() {

        //resto del código        

        return "redirect:/list";
    }

}



18.1 Introducción
Desde la versión 2.0, Spring nos provee de una serie de tags para el manejo de formularios cuando usamos JSP junto con Spring Web MVC.

18.1.1 Configuración
La librería está incluida a través de la dependencia de Spring Web MVC. Para usarla, tan solo tenemos que añadir la siguiente directiva en el inicio de nuestro documento JSP:

<%@ taglib prefix="form" uri="http//www.springframework.org/tags/form" %>
Cualquier elemento que queramos usar de la librería, tendrá que ir precedido de prefijo form:.

La documentación con las etiquetas que se pueden usar la podemos encontrar en la web de Spring: spring-form JSP Tag Library

¿Qué tal si aprendemos con un ejemplo? Vamos a añadir el código necesario a nuestro proyecto de ejemplo, para incluir un formulario y una página de visualización del mismo.

18.2 Ejemplo de aplicación con formulario
Vamos a trabajar con nuestro proyecto de base, para añadirle un nuevo formulario y una página de visualización de datos.

18.2.1 Configuración
En primer lugar, nos dirigimos hacia el fichero web.xml, en el cual vamos a añadir un filtro (también conocido como interceptor), que nos va a permitir trabajar con todos los datos en UTF-8

    ...
    <filter>
        <filter-name>encoding-filter</filter-name>
        <filter-class>
            org.springframework.web.filter.CharacterEncodingFilter
        </filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
        <param-name>forceEncoding</param-name>
        <param-value>true</param-value>
        </init-param>
    </filter>

    <filter-mapping>
        <filter-name>encoding-filter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    ...
18.2.2 Modelo de datos
Nuestro formulario nos permitirá dar de alta instancias de una clase de nuestro modelo. En particular, vamos a implementar una sencilla clase Empleado, que tendrá solamente tres datos.

package com.openwebinars.springmvc.model;

public class Empleado {

    private String nombre;
    private long id;
    private String email;

    public Empleado() {

    }

    public Empleado(String nombre, long id, String email) {
        this.nombre = nombre;
        this.id = id;
        this.email = email;
    }


    public String getNombre() {
        return nombre;
    }
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
    public long getId() {
        return id;
    }
    public void setId(long id) {
        this.id = id;
    }
    public String getEmail() {
        return email;
    }
    public void setEmail(String email) {
        this.email = email;
    }

}

}
18.2.3 Interfaz de usuario (visualización)
Para no enmarañar la vista con elementos propios de bootstrap, vamos a hacer este ejemplo solo con código HTML.

Vamos a crear dos vistas: una incluirá el formulario (a la que llamaremos form.jsp), y la otra la pantalla de visualización de datos (a la que llamaremos view.jsp).

El código fuente de ambos documentos JSP es el siguiente:

view.jsp

<%@ page language="java" contentType="text/html; charset=utf-8"
    pageEncoding="utf-8"%>
<html>
    <head>
    </head>
<body>
    <h2>Información de empleado enviada</h2>
    <table>
        <tr>
            <td>Nombre :</td>
            <td>${empleado.nombre}</td>
        </tr>
        <tr>
            <td>ID :</td>
            <td>${empleado.id}</td>
        </tr>
        <tr>
            <td>Email :</td>
            <td>${empleado.email}</td>
        </tr>
    </table>
</body>
</html>
18.2.4 Interfaz de usuario (formulario)
Pasemos ahora al formulario, que es el quid de esta lección.

form.jsp

<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form"%>
<html>
    <head>
    </head>
    <body>
        <h3>Bienvenido, introduzca los detalles del empleado</h3>
        <form:form method="POST" action="addEmpleado" modelAttribute="empleadoForm">
             <table>
                <tr>
                    <td><form:label path="nombre">Nombre</form:label></td>
                    <td><form:input path="nombre"/></td>
                </tr>
                <tr>
                    <td><form:label path="id">Id</form:label></td>
                    <td><form:input path="id"/></td>
                </tr>
                <tr>
                    <td><form:label path="Email">Email</form:label></td>
                    <td><form:input path="Email"/></td>
                </tr>
                <tr>
                    <td><input type="submit" value="Submit"/></td>
                </tr>
            </table>
        </form:form>
    </body>
</html>
Como podemos observar, hemos añadido la nueva directiva, que nos permitirá trabajar con etiquetas de tipo <form:xyz></form:xyz> para construir nuestro formulario.

Si recordamos algo de nuestros conocimientos de HTML, cualquier formulario debería estar contenido en una etiqueta <form>. Spring tiene su etiqueta análoga, con la siguiente sintaxis:

<form:form modelAttribute="..." class="..." method="..." action="...">

Los atributos class, method, action son los habituales en HTML. Spring incorpora el atributo modelAttribute, que nos va a permitir indicar el nombre del objeto (de nuestro modelo) en el cual se almacenará la información del formulario. Debe coincidir con el nombre de un objeto que será añadido al modelo dentro del controlador (lo referiremos en el apartado correposdiente). En nuestro ejemplo:

<form:form method="POST" action="addEmpleado" modelAttribute="empleadoForm">
Usaremos un objeto que se llama empleadoForm.

Dentro de un formulario, podemos encontrar distintos tipos de controles. El más usual es del de tipo input. Spring también nos lo ofrece con la siguiente sintaxis:

<form:input 
    path="..." 
    id="..." 
    name="..."
    type="..."
    placeholder="..."
    class="..." />
Los atributos id, name, type, placeholder, class, … son los usuales en HTML. Spring incorpora el atributo path, que indica la ruta (dentro del objeto establecido en modelAttribute, al estilo del Expression Language de JSP) con la cual se va a mapear este campo de formulario.

18.2.4 Controlador
El controlador también incorpora algunos elementos nuevos:

package com.openwebinars.springmvc.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

import com.openwebinars.springmvc.model.Empleado;

@Controller
public class EmpleadoControlador {

    @RequestMapping(value = "/empleado", method = RequestMethod.GET)
    public String showForm(Model model) {       
        Empleado empleado = new Empleado();
        model.addAttribute("empleadoForm", empleado);

        return "form";

    }

    @RequestMapping(value = "/addEmpleado", method = RequestMethod.POST)
    public String submit(@ModelAttribute("empleadoForm") Empleado empleado,  Model model) {
        model.addAttribute("empleado", empleado);

        return "view";
    }

}
Para comprenderlo, vamos a ver el siguiente gráfico:



Como podemos comprobar, creamos una instancia de nuestro modelo, y se la pasamos al formulario, para que Spring pueda almacenar en ella los valores que se escriban en el formulario. Cuando se termina, dicha instancia, ya rellena de datos, se envía de nuevo al controlador, para que le podamos dar el tratamiento necesario.



19.1 Introducción
Spring en general, y MVC en particular, incorporan el uso del estándar JRS-303 para validación de beans. Esta validación no solo se puede usar en el contexto de la utilización de formularios, sino que podría hacerse en cualquier parte de una aplicación, incluida la capa de acceso a datos.

19.2 Dependencias Maven necesarias
Para poder usar la validación, necesitamos enlazar tanto la librería del estandar como el motor de validación (usaremos el de Hibernate).

Las dependencias son las siguientes:


        <!-- Validación -->
        <!-- https://mvnrepository.com/artifact/javax.validation/validation-api -->
        <dependency>
            <groupId>javax.validation</groupId>
            <artifactId>validation-api</artifactId>
            <version>1.1.0.Final</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-validator -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-validator</artifactId>
            <version>5.3.1.Final</version>
        </dependency>
19.3 Anotaciones disponibles para usar
La sintaxis completa de las anotaciones que podemos utilizar se puede consultar en la especificación del estándar. En particular, encontramos algunas bastante interesantes:

@NotNull - Comprueba que el valor anotado no sea nulo. Por desgracia no comprueba cadenas vacías.

@Pattern - Comprueba si una determinada cadena encaja con una expresión regular.

@Past - El elemento anotado debe ser una fecha anterior a la actual

@Min - El elemento anotado debe ser un número mayor o igual que el número especificado.

@Max - El elemento anotado debe ser un número menor o igual que el número especificado.

@NotBlank - Comprueba que la cadena anotada es no nula, y que la longitud de la misma (quitando los espacios en blanco al inicio y al final) es mayor que cero.

@Email - Comprueba que la cadena introducida sea una dirección de email válida.
19.4 Uso de properties para los mensajes de error
Cuando el usuario no introduzca convenientemente un valor en el formulario, debe recibir un mensaje de error.

En JSP, podemos especificar esto a través del tag form:errors:

    <form:errors path="atributo" cssClass="clase"></form:errors>
Podríamos hacer uso de componentes gráficos potentes, como los diálogos flotantes de bootstrap, para visualizar estos mensajes.

El texto que se visualice en el mismo puede ser definido en un fichero de properties. Esto aporta varias ventajas:

Para modificar un mensaje de error, no tenemos que modificar el código, solo un fichero de texto.

Todos los mensajes de error están ubicados en un solo fichero.

Nos permite hacer una internacionalización de estos mensajes, para modificar el idioma de los mismos.

…
Para hacer uso de un fichero de properties, tenemos que añadir un bean especial en nuestro fichero dispatcher-servlet.xml:

<!-- Este bean nos permitirá usar properties -->
    <bean id="messageSource"
        class="org.springframework.context.support.ReloadableResourceBundleMessageSource">

        <property name="basename" value="/WEB-INF/messages" />

    </bean>
La sintaxis en el fichero de properties debe ser la siguiente

ValidationAnnotation.objeto.atributo=Mensaje
Un ejemplo sería

NotEmpty.empleadoForm.nombre=Por favor introduzca el nombre del empleado
Size.empleadoForm.nombre=El nombre de un empleado debe tener entre 3 y 30 caracteres
19.5 Cambios en el controlador
Para poder implementar la validación, tenemos que añadir algunos cambios en el controlador. Veamos el siguiente trozo de código:

@RequestMapping(value = "/addEmpleado", method = RequestMethod.POST)
    public String submit(@Valid @ModelAttribute("empleadoForm") Empleado empleado,  
            BindingResult result, Model model) {

        if (result.hasErrors()) {
            return "form";
        } else {        
            model.addAttribute("empleado", empleado);
            return "view";
        }
    }
El objeto que ya estaba anotado con @ModelAttribute(...) lo tenemos que anotar también con @Valid, para indicar que deseamos recibir un objeto válido.

El siguiente parámetro en la firma del méotodo, obligatoriamente, debe ser un objeto de tipo BindingResult, que nos permitirá verificar si ha habido errores.

En caso de haberlos, el mecanismo más sencillo es devolver al usuario al formulario, donde los errores de visualización serán mostrados.




21.1 Introducción
El framework Spring soporta la integración con varios ORMs: Hiberante, JPA (Java Persistence API), JDO (Java Data Objects) para la gestión de recursos, el acceso a los datos y las estrategias de transacciones.

Spring añade muchas características a la capa ORM subyacente que se utilice. Entre los beneficios de usar Spring están:

Fácil testeo, a través del módulo de testeo de Spring.

Excepciones comunes: cada ORM puede implementar su juego de excepciones en particular. Spring Data unifica el mismo.

Gestión de recursos general: uso integrado de objetos SessionFactory, EntityManagerFactory, DataSource, …

Gestión de transacciones integrada: se pueden gestionar las transacciones a través de anotaciones o de XML.
21.2 JPA, ¿qué es exactamente?
El Java Persistence API es un estándar de Java EE para la persistencia de datos. La versión 2.1 se encuentra definida en el estándar JSR338. Frente al maremagnum de ORM que han ido surgiendo en el mercado, JPA proporciona un estándar robusto para realiza el mapeo objeto-relacional y acceder a diferentes almacenes de datos.

21.3 Dependencias
Para el uso de Spring Data JPA tenemos que añadir las siguientes dependencias Maven:

    <dependency>
      <groupId>javax.transaction</groupId>
      <artifactId>jta</artifactId>
      <version>1.1</version>
    </dependency>
    <dependency>
      <groupId>org.springframework.data</groupId>
      <artifactId>spring-data-jpa</artifactId>
      <version>1.10.5.RELEASE</version>
    </dependency>
La primera, nos permitirá hacer uso de las transacciones, lo cual es necesario en JPA. La segunda, nos permitirá, de forma propiamente dicha, usar JPA.

En los diferentes ejemplos, utilizaremos como implementación subyacente de JPA el motor de ORM Hibernate. Y como base de datos, usaremos H2 (una base de datos que se puede embeber dentro de un proyecto, y que nos facilitará el uso de una base de datos relacional). Las dependencias a añadir son las siguientes:

    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-core</artifactId>
      <version>5.1.0.Final</version>
    </dependency>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-entitymanager</artifactId>
        <version>5.1.0.Final</version>
    </dependency>
    <dependency>
      <groupId>com.h2database</groupId>
      <artifactId>h2</artifactId>
      <version>1.4.193</version>
    </dependency>
Spring JPA, disponible en el paquete org.springframework.orm.jpa ofrece una manera fácil para el uso de JPA, y soporta varias formas de configuración. Vamos a proponer una que sea lo más sencilla posible.

21.4 Configuración
El fichero dispatcher-servlet.xml, que hasta ahora tenía unas pocas líneas de código, se va a ver engrosado con la definición de varios beans que necesitamos para usar Spring Data JPA.

En primer lugar, tenemos que definir el origen de datos con el que vamos a trabajar; en nuestro caso, será una base de datos H2. El código para definir el bean es el siguiente:
    <bean id="dataSource"
        class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName" value="org.h2.Driver" />
        <property name="url" value="jdbc:h2:./ejemplo" />
        <property name="username" value="sa" />
        <property name="password" value="" />
    </bean>
En segundo lugar, tenemos que definir el adaptador de JPA a una implementación concreta. En nuestro caso, la implementación de JPA que usaremos será la de Hibernate. El código de configuración del bean es el siguiente:
    <bean id="jpaVendorAdapter"
        class="org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter">
        <property name="showSql" value="true" />
        <property name="generateDdl" value="true" />
        <property name="database" value="H2" />
    </bean>
En tercer lugar, tenemos que configurar el Entity Manager. Este se construye sobre los dos beans anteriores; también tenemos que proporcionarle la ruta del paquete donde se definen las clases que serán almacenadas en la base de datos (las entidades, de las que hablaremos en la próxima lección)
    <bean id="entityManagerFactory"
        class="org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean">
        <property name="dataSource" ref="dataSource" />
        <property name="jpaVendorAdapter" ref="jpaVendorAdapter" />
        <!-- spring based scanning for entity classes -->
        <property name="packagesToScan" value="com.openwebinars.springmvc.model" />
    </bean>
Todo el ir y venir de información desde o hacia la base de datos se hace de forma transaccional. Para ello, tenemos que definir el gestor de transacciones, y además, indicar que estas transacciones podrán ser definidas mediante anotaciones. El código de configuración es el siguiente:
    <!-- Configure the transaction manager bean -->
    <bean id="transactionManager" class="org.springframework.orm.jpa.JpaTransactionManager">
        <property name="entityManagerFactory" ref="entityManagerFactory" />
    </bean>

    <!-- Enable annotation driven transaction management -->
    <tx:annotation-driven />
Por último, hay que indicar las clases que serán repositorios de datos. Sobre ellas abundaremos en las lecciones siguientes. El código de configuración es:
    <jpa:repositories base-package="com.openwebinars.springmvc.repo"></jpa:repositories>
	
	
	22.1 Introducción
En el contexto de JPA en general, y de Spring Data Jpa, una entidad no es más que una clase java que será susceptible de ser gestionada por un Entity Manager, y por ende, de ser transformada de objeto a fila de una tabla de una base de datos relacional. A esta operación se le conoce como mapeo objeto-relacional.

Un repositorio es un bean especial que nos permitirá realizar una serie de operaciones con una entidad, como guardar una nueva, editar o eliminar una existente, o buscar de entre el almacén de esa entidad entre las que cumplan una determinada condición.

22.2 Entidades
Como decíamos antes una entidad no será otra cosa que la representación de una tabla de una base de datos en una clase; por ende, los objetos de esa clase, representarían las filas de esa tabla de una base de datos relacional.

Para que una clase Java sea tratada como entidad, tenemos que usar algunas anotaciones. Veamos un ejemplo:

package com.openwebinars.springmvc.model;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name="STUDENT")
public class Student {


    @Id
    @GeneratedValue(strategy=GenerationType.AUTO)
    @Column(name="studentId")
    private long id;
    @Column
    private String first_name;
    @Column
    private String last_name;

    //Getters, setters, ...

}
Las anotaciones está definidas por JPA en el paquete javax.persistence. Las más usuales son:

@Entity: nos permite indicar que esta clase debe ser tratada como una entidad

@Table(name=...): indica que esta entidad se mapea con una tabla en la base de datos subyacente. El nombre se indica como propiedad de la anotación.

@Id y @GeneratedValue: indica que un determinado atributo de la clase es la clave primaria de la tabla subyacente, es decir, el atributo que identifica a cualquier objeto de esa clase.

 @GeneratedValue nos dice que ese valor será autogenerado por la base de datos.

@Column: nos permite indicar que un atributo de la clase será tratado como una columna de la base de datos.
22.3 Repositorios
Cómo decíamos en la introducción, un repositorio será un bean que nos permitirá realizar diversas operaciones con las entidades.

En Spring Data existe una gran jerarquía de repositorios:



Solo vamos a entrar en detalle en el último, ya que incluye las funcionalidades de los anteriores.

Para usar este repositorio, tan solo tenemos que extenderlo, creando una interfaz para gestionar una determinada entidad:

package com.openwebinars.springmvc.repo;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

import com.openwebinars.springmvc.model.Student;

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

}
Como podemos comprobar, el código anterior es muy simple. Tan solo destaca:

El interfaz queda anotado con @Repository. Es un estereotipo de Spring y sirve para que, posteriormente, el bean pueda ser escaneado como repositorio, y usado en cualquier otra clase (por ejemplo, un controlador).

A la hora de extender la interfaz, hay que incluir dos clases:
Student, el tipo de entidad que va a ser gestionada

El tipo de dato del atributo que esté marcado como @Id en dicha clase.
22.4 Uso de repositorios y entidades
Para usar un repositorio, tan solo tenemos que inyectarlo e invocar alguno de sus métodos. Veamos un ejemplo en un controlador:

@Controller
public class StudentController {

    @Autowired
    private StudentRepository studentRepository;

    //resto del código
}
Para realizar alguna operación concreta, como listar o salvar, tan solo tenemos que invocar el método adecuado:

    //...

    @RequestMapping(value = "/list", method = RequestMethod.GET) 
    public String listStudents(Model model){

        model.addAttribute("listaEstudiantes", studentRepository.findAll());

        return "list";
    }

    //....

    @RequestMapping(value = "/addStudent", method = RequestMethod.POST)
    public String submit(@ModelAttribute("studentForm") Student student,  Model model) {

        studentRepository.save(student);
        return "redirect:/list";
    }

    //...
En las próximas lecciones veremos que operaciones podemos con un repositorio y como podemos extenderlo fácilmente.



23.1 Introducción
Muchos ORM, si bien facilitan el trabajo de acceso a una base de datos relacional, necesitan de múcho código muy similar para la generación de diferentes consultas a la base de datos, que vayan más allá de obtener todos los registros de un mismo tipo, o uno en particular. Vamos a comprobar como Spring Data JPA es muy potente, y tan solo con ser cuidadosos en la definición de la firma de los métodos de búsqueda, será capaz de implementar el código por sí mismo.

23.2 Creación de consultas
Por defecto, cualquier repositorio que creemos, y que herede de JpaRepository<T, ID>, tendrá por defecto algunos métodos de búsqueda; pero ¿y si queremos implementar alguno más específico? Tendremos que añadir algunos métodos más a nuestro repositorio.

El mecanismo de construcción de consultas de Spring Data procesará el nombre de los métodos que añadamos a nuestro repositorio, para construir consultas. En particular, eliminará los prefijos find...By, read...By, query...By, y get...By del nombre del método, y procesará el resto.

Veamos un ejemplo a continuación:


@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    /* Realizar la búsqueda en base al nombre */
    public List<Student> findByFirstName(String firstName);

    //resto del código

}
Spring se encarga de escanear, y procesar el nombre del método, de manera que:

Elimina el prefijo findBy
Procesa el resto, comprendiendo que queremos buscar entidades Student que tengan un determinado FirstName (que es una propiedad del bean Student).
El nombre del método actuará a modo de cláusula WHERE en una sentencia SELECT de SQL.

Se pueden combinar varias restricciones añadiendo al nombre del método And y Or. También se puede añadir una ordenación diferente a la por defecto, añadiendo al final del nombre del método ...OrderByXXXXXXXAsc o ...OrderByXXXXXXXDesc y el nombre del atributo sobre el que vamos a ordenar.

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    /* Realizar la búsqueda en base al nombre */
    public List<Student> findByFirstName(String firstName);

    /* Realizar la búsqueda en base al apellido */
    public List<Student> findByLastName(String lastName);

    /* Realizar la búsqueda en base al nombre y el apellido */
    public List<Student> findByFirstNameAndLastName(String firstName, String lastName);

    /* Realizar la búsqueda en base al nombre y el apellido, y ordenar los resultados descendentemente por apellido  */
    public List<Student> findByFirstNameAndLastNameOrderByLastNameDesc(String firstName, String lastName);

}
La pregunta es: ¿no tenemos que darle cuerpo a esos métodos de búsqueda? La respuesta es que NO. Spring Data se encarga de construirlos, descargándonos de mucho trabajo.







	24.1 Introducción
La persistencia de entidades con Spring Data es muy sencilla. Los diferentes repositorios, en particular JpaRepository, implementan los métodos necesarios para crear o editar entidades, y también para eliminarlas.

24.2 Almacenar una nueva instancia de una entidad
El proceso de almacenamiento de una nueva entidad es el más sencillo de todos. Si tenemos definido un repositorio como el del ejemplo:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //Resto del código

}
Tan solo tendremos que invocar al método save(...) del mismo para que Spring JPA se encargue de almacenar la instancia de la clase Student en la base de datos, como por ejemplo en este controlador:

@Controller
public class StudentController {

    //resto del código

    @RequestMapping(value = "/addStudent", method = RequestMethod.POST)
    public String submit(@ModelAttribute("studentForm") Student student,  Model model) {

        studentRepository.save(student);
        return "redirect:/list";
    }

    //resto del código
}
24.3 Editar una instancia de una entidad
Para editar una entidad, lo primero que debemos hacer es añadir los métodos equals y hashCode a nuestra clase entidad. Spring Tool Suite puede autogenerarlos si lo deseamos, a traves del menú Source > Generate hashCode() and equals()

Para poder editar una entidad, primero tenemos que localizarla (por ejemplo, con el método findOne(...)), cambiar alguno de sus valores, y almacenarla. Podemos ver el código a continuación:


    @RequestMapping(value = "/edit/{id}", method = RequestMethod.GET)
    public String showFormEdit(@PathVariable("id") Long id, Model model) {

        Student student = studentRepository.findOne(id);
        model.addAttribute("studentForm", student);
        model.addAttribute("op", "edit");

        return "form";
    }
Este método controlador recoge el Id de la entidad que queremos modificar desde la URL. Suele ser una de las opciones más comunes. A través de este Id, podemos encontrar facilmente la entidad, ya que es su clave primaria.

Para editarla, lo más comun en las aplicaciones Spring MVC es hacerlo a través de un formulario. En el mismo, tenemos que incluir, entre los campos a modificar el Id (a diferencia de cuando creamos uno nuevo). Para que el usuario no modifique manualmente este Id, lo cargaremos como un campo oculto (hidden):

<form:form method="POST" action="${not empty op ? '../edit' : 'addStudent'}" modelAttribute="studentForm">
    <form:hidden path="id"/>
    <!-- Resto del formulario -->
</form:form>
De esta forma, el dato pasa del controlador al formulario, y volverá al controlador cuando pulsemos el botón de enviar.

Por último, el código de modificación sería el siguiente:

    @RequestMapping(value = "/edit", method = RequestMethod.POST)
    public String submitEdit(@ModelAttribute("studentForm") Student student,  Model model) {

        studentRepository.save(student);
        return "redirect:/list";
    }
Pero, ¡si es el mismo método que para guardar! Efectivamente, Spring Data JPA utiliza el mismo, ya que es capaz de diferenciar de si la entidad no existe, y tiene que crearla; o si existe, y lo que debe hacer es editarla.

24.4 Eliminar una instancia de entidad
Elimnar una entidad es un proceso fácil, ya que el interfaz JpaRepository nos provee de algunos métodos, en particular delete(...), con varias firmas. A continuación podemos ver un ejemplo:

    @RequestMapping(value = "/delete/{id}", method = RequestMethod.GET)
    public String delete(@PathVariable("id") Long id, Model model) {

        studentRepository.delete(id);

        return "redirect:/list";
    }
En este caso, usamos la implementación que nos permite eliminar una instancia de entidad a partir de su Id (clave primaria).


25.1 Introducción
La capacidad de creación de consultas que tiene Spring Data JPA es muy amplio. En lecciones anteriores hemos visto como usar una pequeña parte. En esta lecciones profundizaremos en la creación de consultas de diferentes formas, incluidas las consultas nativas.

25.2 Creación de consultas en base al nombre
Este método, que ya estudiamos en la lección 23, permitía crear una consulta con tan solo ser cuidadoso en la definición del nombre del método:

Por ejemplo:


public interface UserRepository extends Repository<User, Long> {

  List<User> findByEmailAddressAndLastname(String emailAddress, String lastname);
}
Esta consulta nos permitiría localizar usuarios en base a su correo electrónico y sus apellidos.

La lista de palabras que podemos utilizar es muy amplia:

Palabra	Ejemplo	JPQL
And	findByLastnameAndFirstname	… where x.lastname = ?1 and x.firstname = ?2
Or	findByLastnameOrFirstname	… where x.lastname = ?1 or x.firstname = ?2
Is,Equals	findByFirstname,findByFirstnameIs,findByFirstnameEquals	… where x.firstname = ?1
Between	findByStartDateBetween	… where x.startDate between ?1 and ?2
LessThan	findByAgeLessThan	… where x.age < ?1
LessThanEqual	findByAgeLessThanEqual	… where x.age <= ?1
GreaterThan	findByAgeGreaterThan	… where x.age > ?1
GreaterThanEqual	findByAgeGreaterThanEqual	… where x.age >= ?1
After	findByStartDateAfter	… where x.startDate > ?1
El resto de la tabla la podemos encontrar en la documentación oficial de Spring Data

25.3 JPQL
JPQL es un lenguaje de consulta, de estructura similar a SQL, pero orientado a objetos, y que nos permite definir consultas sobre un Entity Manager. De facto, es el lenguaje de consulta que podemos utilizar desde nuestra aplicación. para consultar las entidades almacenadas en nuestra base de datos realacional

25.3.1 Named Queries
En ocasiones, tendremos la necesidad de definir una o varias consultas que usaremos en más de un lugar a lo largo de nuestra aplicación. Si bien, una manera de hacer esto sería al estilo del apartado 25.2, es posible que no podamos usar el mismo porque:

Venimos del mundo SQL y nos sentimos más cómodos escribiendo una consulta

La consulta es muy específica y no podemos construirla con el procesamiento automático de Spring Data

Queremos usar SQL nativo

…
Una consulta con nombre (named query) será una consulta JPQL que definiremos junto con la entidad, y que podremos utilizar posteriormente.

La forma de definir esta consulta es la siguiente:

@Entity
@NamedQuery(name = "Student.findById", query = "select s from Student s where s.id = ?1")
@Table(name="STUDENT")
public class Student {

    //resto del código de la clase    

}
Para invocar la consulta, tan solo tenemos que añadir un nuevo método en nuestro repositorio:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    /* Realizar la búsqueda en base al id */
    public Student findById(Long id);

}
Spring Data resolverá, en base al nombre de este método, que debe usar la consulta con nombre para ejecutarlo.

25.3.2 Uso de @Query
El uso de consultas con nombre es una buena aproximación cuando trabajamos con un pequeño número de consultas. Si este número crece, una mejor aproxiamción es el uso de la anotación @Query. Esta nos va a permitir definir la consulta JPQL dentro del repositorio, y asociada al método que lo va a ejecutar.

Por ejemplo, el método anterior, pero definido con JPQL sería así:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    /* Realizar la búsqueda en base al id */
    @Query("select s from Student s where s.id = ?1")
    public Student findById(Long id);

}
25.3.2.1 Uso de LIKE con @Query
Este tipo de consultas nos permite en el uso del operador LIKE, para verificar si una columna coincide con un patrón. Por ejemplo, si quisiéramos comprobar si un valor comienza con la cadena de caracteres que le proporcionamos, podríamos hacer uso de LIKE y el operador %:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    //resto del código 

    /* Realizar la búsqueda si el apellido comienza con una cadena */
    @Query("select s from Student s where s.lastName = ?1%")
    public List<Student> findByLastNameStartsWith(String lastName);

}
25.3.2.2 Consultas nativas
La anotación @Query nos permite también el uso de consultas nativas SQL, incluyendo la propiedad nativeQuery=true.

Un ejemplo de consulta nativa sería el siguiente:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    //resto del código 

    /* Realizar la búsqueda si coincide el nombre */
    @Query("SELECT * FROM STUDENTS WHERE FIRST_NAME = ?1", nativeQuery = true)
    public List<Student> findByFirstName(String firstName);

}
25.3.3 Uso de parámetros con nombre
En todos los ejemplos anteriores, los parámetros a incluir dentro de las consultas han sido definidos con un índice (por ejemplo ?1). Sin embargo, hay ocasiones donde es más clarificador usar un nombre para los mismos:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    //resto del código 

    /* Realizar la búsqueda si coincide el nombre y el apellido */
    @Query("select s from Student s where s.firstName = :firstname or u.lastname = :lastname")
    public List<Student> findByFirstNameOrLastName(
            @Param("firstname") String firstName, 
            @Param("firstname") String lastName);

}
Como podemos comprobar, hemos sustituido los parámetros con índice por una cadena de caracteres, que lleva como prefijo dos puntos (:firstname). Esto hace que JPQL intreprete que debe ser sustituido por un parámetro. Para hacer uso de este parámetro dentro del método, usamos la anotación @Param, mediante la cual asignamos el parámetro a uno de los valores que se proporcionan al método.

25.3.3 Uso de consultas de modificación
Todas las secciones anteriores nos mostraban como realizar consultas que solamente recuperan datos. Para crear una consulta que nos permita modificarlos, tenemos que añadir la anotación @Modifiying. Esto nos permitirá elaborar una consulta JPQL con la que poder añadir, modificar o eliminar datos. Un ejemplo de consulta de modificación sería la siguiente:

@Repository
public interface StudentRepository extends JpaRepository<Student, Long>{

    //resto del código    

    /*
     * CONSULTAS AVANZADAS
     */

    //resto del código 

    /* Actualizar el nombre y el apellido */
    @Modifying
    @Query("update Student s set s.firstName = ?1, s.lastName = ?2 where s.id = ?3")
    int setFirstNameAndLastNameFor(String firstname, String lastname, Long id);

}
Para que esta consulta se ejecute en un context transaccional (es decir, para no tener que ocuparnos nosotros del manejo de las transacciones), tenemos que anotar con @Transactional el método controlador que invoque a esta consulta:

    @RequestMapping(value = "/edit", method = RequestMethod.POST)
    @Transactional
    public String submitEdit(@ModelAttribute("studentForm") Student student,  Model model) {

        studentRepository.setFirstNameAndLastNameFor(student.getFirstName(), student.getLastName(), student.getId());
        return "redirect:/list";
    }




26.1 Introducción
Más de veinte lecciones después de comenzar el curso, estamos en disposición de decir que estamos duchos en este framework. Si miramos hacia atrás, veremos que somos capaces de construir un proyecto para el desarrollo de una aplicación web que consulta una base de datos relacional embebida dentro de nuestro proyecto. Pero, ¿qué tareas de soporte hemos venido desarrollando manualmente hasta ahora?

26.2 Tareas necesarias a la hora de desarrollar un proyecto Spring
Si bien en ocasiones hemos utilizado como plantilla un proyecto anterior, la creación de un proyecto Spring nos ha conllevado algunas o todas las siguientes tareas:

Definir un proyecto en Spring Tool Suite: Dependiendo del tipo de aplicación que quisiéramos realizar, un proyecto Java o Web.

Convertir el proyecto en un proyecto Maven: que nos permitiera el uso del gestor de dependencias, entre otros elementos.

Conocer las dependencias de los módulos que íbamos a utilizar, así como la mejor versión de los mismos.

Configurar algunas carpetas, como la de recursos; los ficheros de propiedades del log, etc…

Definir algunos elementos en el fichero de configuración de beans, como el uso de etiquetas para MVC.

Definir algunos beans complejos, como la configuración para el uso de Spring Data

….
Como podemos observar, la cantidad de tareas es grande. Y si nos cronometráramos para medir el tiempo de todas estas tareas, veríamos que estamos invirtiendo mucho en algunas cosas que seguramente podrían estar automatizádas, dejándonos tiempo a nosotros para poder implementar nuestra aplicación.

Spring Boot viene a nuestro rescate, permitiéndonos realizar las tareas que indicamos en el listado anterior y muchas más, de una forma fácil e intuitiva para el programador.



27.1 ¿Qué es Spring Boot?
Como hemos podido comprobar, Spring tiene una amplia cantidad de módulos que implican multitud de configuraciones. Estas configuraciones pueden tomar mucha tiempo, pueden ser desconocidas para principiantes y, sobre todo, suelen ser repetitivas. La solución a todos estos inconvenientes es Spring Boot, que aplica el concepto de Convention over Configuration (CoC).

Convención sobre configuración
Convención sobre Configuración, también conocido como CoC es un paradigma de programación de software que busca minimizar el número de decisiones que un desarrollador necesita hacer, ganando así en simplicidad pero no perdiendo flexibilidad por ello.
Fuente: Wikipedia
La Convención sobre Configuración es un paradigma que minimiza las decisiones que tienen que tomar los desarrolladores, simplificando así las tareas a realizar. Con todo, no se pierde la flexibilidad, ya que aunque existen unos valores por defecto, siempre podemos configurar de forma extendida. De esta manera, podemos evitar muchas de las tareas repetitivas de un proyecto.

27.2 ¿Cómo comenzar a utilizar Spring Boot?
Para comenzar a usar Spring Boot necesitamos un proyecto Maven, al que le indicaremos que herede de una de las plantillas de Spring Boot.

<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.4.2.RELEASE</version>
</parent>
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
Podemos copiar este fragmento de código, actualizado a la última versión, desde la web de Spring Boot
Con las etiquetas <parent></parent> indicamos que nuestro fichero POM hereda del de Spring Boot. La dependencia spring-boot-starter-web es necesaria para poder empezar con un proyecto web; a medida que crezca el proyecto serán necesarias algunas más.

Si queremos modificar la configuración por defecto, normalmente podremos añadir el fichero application.properties en la carpeta src/main/resources del proyecto.

Para la configuración avanzada, tenemos que añadir componentes que sustituirán a los de autoconfiguración.

27.3 Primer ejemplo
Para terminar con un primer ejemplo, y comprobar la potencia de Spring Boot y lo que tenemos por delante para aprender, podemos ver el siguiente código:

package com.openwebinars.springboot;


import org.springframework.boot.*;
import org.springframework.boot.autoconfigure.*;
import org.springframework.stereotype.*;
import org.springframework.web.bind.annotation.*;

@Controller
@EnableAutoConfiguration
public class SampleController {

    @RequestMapping("/")
    @ResponseBody
    String home() {
        return "Hello World!";
    }

    public static void main(String[] args) throws Exception {
        SpringApplication.run(SampleController.class, args);
    }
}
Si lo ejecutamos, podremos comprobar como hemos creado una aplicación Spring MVC en muchísimo menos tiempo.

28.1 Introducción
La convención sobre configuración es un paradigma muy sencillo que se usa principalmente en programación. Significa que el entorno en el que trabajamos (sistemas, librerías, idioma, …) asume muchas situaciones lógicas por defecto; y si nosotros las tomamos como tal en lugar de tener que explicitarlas cada vez, la programación se vuelve una tarea más sencilla y productiva, pudiendo poner el foco en lo importante.

La meta es decrementar el número de decisiones que el programador debe tomar y eliminar la complejidad de tener que configurar todas y cada una de las áreas en el desarrollo de una aplicación. El resultado inmediato es que se pueden crear más cosas en menos tiempo.

Algunos entornos de programación altamente productivos, como Ruby on Rails, Groovy on Grails o similar utilizan este concepto. Si sigues las convenciones establecidas, se puede desarrollar una aplicación Ruby o Groovy en mucho menos tiempo y con tan solo unas pocas líneas de código.

Por otro lado, si queremos ignorar las convenciones, podemos escribir el código de configuración nosotros mismos. Aun así, las convenciones no son arbitrarias y han sido desarrolladas por una comunidad de programadores de alto nivel, por lo que rara vez tendremos la sensación de necesitar invertir nuestro tiempo en modificarlas.

De hecho, el concepto de convención sobre configuración es, de alguna manera, una forma básica de entender cualquier trabajo estructurado, y que incluso utilizan algunas metodologías de productividad en el trabajo como GTD (Getting Things Done).

28.2 Convención sobre configuración en Spring
Spring Boot nos va a permitir tener definidas una serie de configuraciones por defecto que serán muy útiles. Aunque las vamos a ir aprendiendo en los siguientes apartados, podemos echar un vistazo a dos de los tres pilares de un proyecto Spring MVC: controladores y modelos.

Por ejemplo, el uso de uno de los componentes de Spring Boot nos permitirá no tener que definir el mapeo de URLs con un controlador específico, obteniendo estas de la url, de forma que:

WelcomeController se mapearía con cualquier petición a /welcome*

HomeController se mapearía con cualquier petición a /home*

RegisterController se mapearía con cualquier petición a /register*

Si se sigue la convención de nombre el controlador como XXXXXController, la clase correspondiente nos evita la tediosa tarea de definir y mantener una lista potencialmente larga de URLs mapeadas.

En el caso del modelo, podemos añadir objetos o colecciones de los mismos a un modelo sin necesidad de darle un nombre, ya que Spring generará automáticamente un nombre (una clave) para los mismos. La estrategia para la generación de este nombre es la convención sobre configuración. Si queremos evitar este nombre por defecto, podemos proporcionarle nosotros uno explícitamente:


@Controller
public class TheController {

    @GetMapping("/")
    public String controllerMethod(Model model) {

        model.addAttribute(new MyObject1());
        model.addAttribute("name", new MyObject2());

        return "view";
    }
}

29.1 Introducción
Spring Initializr es un servicio ofrecido por Spring mediante el cual podemos generar rápidamente, y desde una web, un proyecto Spring con todos los elementos necesarios. Es altamente configurable y muy efectivo, y como resultado obtenemos un fichero zip que podemos descargar y, cuyo contenido, es un proyecto listo para comenzar.

29.2 Generación de un proyecto Spring Boot con Spring Initializr
Para generar un nuevo proyecto tan solo tenemos que entrar en http://start.spring.io/ e introducir los datos necesarios.

En nuestro caso, para generar un proyecto sencillo, tan solo tendríamos que introducir:

Tipo de proyecto: Maven Project

Versión de Spring Boot: la actual (1.4.2)

Group: com.openwebinars.springboot

Artifact: el nombre del proyecto (por ejemplo, InitializrDemo)

Dependencies: escribimos aquellas que necesitemos. Para un proyecto web sencillo, podemos escribir Web.
Con estos elementos, ya podemos generar el proyecto, pulsando sobre el botón correspondiente.



29.3 Importación del proyecto en STS
Esta carcasa de proyecto que nos hemos descargado puede ser importada desde Spring Tool Suite. En este caso, tenemos que indicarle que el tipo de proyecto que estamos importando es un proyecto Maven.



30.1 Introducción
Spring Boot incorpora una serie de nuevas anotaciones que nos ayudarán sobre todo a simplificar el trabajo de configuración. Veamos todo lo que podemos hacer.

30.2 Anotación @SpringBootApplication
La anotación @SpringBootApplication habilita a Spring para escanear componentes y para configurar los mismos. De hecho, la anotación @SpringBootApplication combina otras tres anotaciones:

@Configuration (anotación de Spring): designa una clase como clase de configuración, para realizar este proceso basado en Java (en lugar de hacerlo con XML). Aunque no hay una opción mejor, los usuarios de Spring Boot suelen realizar la configuración basándose en Java en lugar de XML.

@ComponentScan (anotación de Spring): habilita el escaneo de componentes, de forma que los controladores u otras clases serán automáticamente descubiertas y registradas como beans en el contenedor de dependencias.

@EnableAutoConfiguration (anotación de Spring Boot): esta pequeña anotación podría llamarse @Magia, ya que es la línea de configuración que hace que Spring Boot se autoconfigure. Esta anotación nos evita de realizar múltiples operaciones de configuración por nuestra cuenta.
30.3 Configuración para poder usar JSP en la vista
Por defecto, los proyectos que nos descarguemos desde Spring Initializr no vienen preparados para trabajar con JSP tal cual hemos estado trabajando hasta ahora, si bien la configuración que hay que hacer es muy poca. Los pasos a seguir son:

Añadir algunas dependencias que hacen falta:
<dependency>
  <groupId>org.apache.tomcat.embed</groupId>
  <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
<dependency>
  <groupId>javax.servlet</groupId>
  <artifactId>jstl</artifactId>
</dependency>
Configurar, en el fichero de properties, el prefijo y sufijo para la vista. Esta operación ya la realizábamos antes en el fichero de configuración de beans.
application.properties
spring.mvc.view.prefix=/WEB-INF/jsp/
spring.mvc.view.suffix=.jsp
Crear la carpeta donde van a alojarse los ficheros JSP. Esta debe estar, por fuerza (por la definición del estándar de JSP) dentro de WEB-INF, así que la podemos crear en la ruta src/main/webapp/WEB-INF/jsp
De esta forma, nuestro proyecto de Spring Boot está listo para usar JSP tal y como lo hemos venido usando.



31.1 Spring Starter Project
El entorno de desarrollo Spring Tool Suite incorpora un asistente para la creación de proyectos, de forma que si es nuestro IDE, no tenemos la obligación de utilizar el servicio Spring Initializr.

La opción de menú para crear un nuevo proyecto se encuentre en File > New > Spring Starter Project. Si pulsamos sobre él, entraremos en un asistente donde podemos definir los elementos del proyecto, así como los diferentes módulos de Spring que vamos a usar.

Como ejemplo, podemos crear un proyecto y copiar el código desarrollado en algunas de las lecciones de JPA (por ejemplo, la número 22)


32.1 Introducción
En Spring Boot tenemos varias formas de ejecutar nuestra aplicación. Es viene motivado por algunas razones:

Aunque ya lo hemos podido comprobar anteriormente, los proyectos de Spring Boot no de despligan en Tomcat, sino que le dan la vuelta a esta situación y son ellos los que llevan un servidor embebido. Esto nos da muchas facilidades a la hora de ejecutar una aplicación.

El fichero que se genera a partir de un proyecto Spring Boot, por defecto, no es un fichero .WAR (Web Application Archive) sino un .JAR (Java Application Archive). Esto nos permitirá incluso lanzar nuestra aplicación desde la línea de comandos con solo unos pocos parámetros, frente a los .WAR que suelen llevar un mecanismo de deploy algo más complejo.
32.2 Ejecución a través del IDE
Es la forma más sencilla que tenemos de ejecutar nuestro proyecto. Tan solo tenemos que hacer click derecho con el ratón sobre el proyecto, y escoger, o bien la opción Java Application o la opción Spring Boot App. Esta segunda es algo más recomendable.



Esto provocará que se lance la aplicación, como podemos ver en la consola:



32.3 Ejecución a través de Maven
Maven también nos permitirá lanzar nuestra aplicación, a través del goal spring-boot:run definido por el asistente de Spring Tool Suite.

Como muchos usuarios no tendrán la interfaz mediante línea de comandos de maven, se puede lanzar también desde el IDE. Para ello, tenemos que crear una nueva Configuración de Ejecución en el menú Run As > Run Configurations:



Esta ejecución tardará algo más en lanzarse, ya que probablemente se descargue explícitamente todas las dependencias que el proyecto necesita:



Una vez finalizado el proceso, también se ejecutará la app con normalidad.



33.1 Empaquetando un JAR
Un archivo JAR es un archivo que permite contener y ejecutar aplicaciones Java. Las siglas están escogidas para que coincida con la palabra inglesa “jar” (tarro). Estos ficheros están comprimidos con formato ZIP.

Normalmente, un fichero JAR ejecutable debe contener todo el bytecode de la aplicación, las librerías, recursos, etc… que vaya a utilizar. Para que sea ejecutable, debe incluir un manifiesto, con una entrada que indique qué clase es el punto de entrada.

Para ejecutarlo, lo más común es hacerlo desde la línea de comandos

java -jar foo.jar
Existen muchas formas de construir un fichero Jar, en particular, usando algunos IDEs como Eclipse.

Nosotros vamos a jugar con la ventaja de que trabajamos con Maven, ya que él se encargará de realizar el trabajo por nosotros.

33.2 Ejemplo
En este caso, vamos a construir un JAR a partir de una de las aplicaciones de ejemplo de Spring. Para ello, tendremos que pulsar en File > New > Import Spring Getting Started Content.

En particular, vamos a trabajar con el proyecto, Rest Service, con los parámetros que indica la siguiente imagen:



Al pulsar sobre el botón Finish, STS se descarga el contenido del proyecto y lo pone a nuestra disposición.

La guía de este proyecto la podemos encontrar en esta url. Básicamente, el proyecto genera un servicio web REST capaz de producir contenido en JSON (ya hablaremos más adelante de servicios web; ahora, más que como hace las cosas el proyecto, vamos a ejecutarlo y convertirlo en un jar). El contenido tiene la siguiente estructura:

{"id":1,"content":"Hello, World!"}
33.3 Obtención del fichero JAR
Como hemos dicho anteriormente, Maven hará el trabajo por nosotros, ya que una de las metas, install, se encargará de generarlo y guardarlo en la carpeta target. Para ejecutar esta meta, pulsamos con el botón derecho del ratón sobre el proyecto, Run As > Maven install.



En la consola, empezarán a aparecer muchas líneas, hasta que finalmente obtengamos algo así:



Si abrimos cualquier terminal (por ejemplo, el interno de Spring Tool Suite), podemos ejecutar la aplicación mediante el comando:

java -jar C:\Users\Openwebinars\Desktop\EjemplosCompletos\gs-rest-service-complete\target\gs-rest-service-0.1.0.jar
Cuando en la consola indique que el proyecto está cargado, podemos acceder con el navegador a la dirección http://localhost:8080/greeting, y podremos ver el contenido.




34.1 Introducción
Los starters son una serie de descriptores de dependencias que podemos incluir en nuestras aplicaciones. De un plumazo, podemos obtener todos los módulos de Spring que necesitemos, sin tener que pararnos a buscar código de ejemplo o copiar y pegar decenas de dependencias.

Por ejemplo, si quiero comenzar un proyecto usando Spring y JPA para acceder a la base de datos, tan solo tengo que incluir la dependencia spring-boot-starter-data-jpa en mi proyecto, y todo estará listo.

34.2 El nombre de un starter
Todos los starters oficiales1 siguen un patrón similar en su nombre: spring-boot-starter-*, donde el asterisco representa el tipo de aplicación. El nombre intenta ser lo más autodescriptivo posible y ayudar a localizar el starter más adecuado.

El listado completo de starters pom lo podemos encontrar en http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#using-boot-starter.

Como es natural, podemos añadir más de una dependencia a un starter pom para construir, por ejemplo, un proyecto web y con acceso a datos JPA.

1: Existen en internet decenas de starters no oficiales y ofrecidos por la comunidad de desarrolladores, de los cuales Spring no se hace responsable.





36.1 Introducción
Hemos visto varias maneras diferentes de configurar una aplicación Spring MVC con Spring Boot, y sería bueno repasarlas de nuevo para diferenciar la una de la otra.

36.2 Spring Initializr
Spring Initializr es un servicio ofrecido por Spring mediante el cual podemos generar rápidamente, y desde una web, un proyecto Spring con todos los elementos necesarios.

Si necesitamos una aplicación web que utilice base de datos, lo normal es que necesitemos una configuración como esta:



El fichero obtenido lo podemos descomprimir e importar como un proyecto Maven.

Recordemos que si queremos usar JSP, tenemos que añadir algunas dependencias más:

    <dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-jasper</artifactId>
    </dependency>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>jstl</artifactId>
    </dependency>
36.3 Asistente de Spring Tool Suite
La herramienta Spring Tool Suite nos provee de un asistente, muy similar a la interfaz de Spring Initializr, que nos permite crear, in situ, un proyecto de Spring Boot, incluyendo las depedencias de los módulos que seleccionemos:



36.4 Starter POMs
Esta tercera vía nos permite crear un proyecto Maven o uno a partir del asistente de STS, pero agrupar las dependencias que vamos a necesitar a partir de un starter POM. Spring define una serie de starters oficiales, cuyo nombre siempre es spring-boot-starter-*, donde podemos sustuir el asterisco por web, jpa, mobile, …

En nuestro caso, tendríamos que añadir las dependencias a spring-boot-starter-weby spring-boot-starter-data-jpa

36.5 Configuración por defecto
En cualquiera de los casos anteriores, Spring Boot ofrece una configuración por defecto, que no está mal conocer, aunque sea a vista de pájaro:

Inclusion de los beans ContentNegotiatingViewResolver y BeanNameViewResolver.

Soporte para servir contenido estático, incluidos web jars

Registro automático de beans Converter, GenericConverter y Formatter.

Soporte para HttpMessageConverters.

Soporte para index.html estático

Soporte para customizar el Favicon


37.1 Introducción
Spring Boot puede usarse como una herramienta clásica de comandos en línea.

37.2 Instalación
37.2.1 Instalación de Maven
En primer lugar, tenemos que descargarnos maven. Lo podemos hacer desde el siguiente enlace http://maven.apache.org/download.cgi. La versión actual la encontramos (en binario comprimido en ZIP) en la siguiente url http://apache.rediris.es/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.zip.

Lo más fácil, en un entorno Windows, es descomprimir el fichero y guardar la carpeta en el directorio raiz. Como tarea de soporte, sería bueno añadir la carpeta \bin dentro de la variable Path, para poder invocar la herramienta mvn desde cualquier punto del sistema de ficheros.

En un entorno Mac o Linux se puede obtener Maven a través de los gestores de paquetes:

Los usuarios de OSX, si usan Homebrew, pueden ejecutar brew install maven.

Los usuarios de Ubuntu pueden ejecutar sudo apt-get install maven.
37.2.2. Instalación de Spring Boot
Se puede descargar Spring CLI del repositorio de Spring. En la url http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/ podremos encontrar siempre la última versión. Actualmente, podemos descargarla en el siguiente enlace http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/1.4.2.RELEASE/spring-boot-cli-1.4.2.RELEASE-bin.zip.

Lo podemos descargar en cualquier ubicación. Para mostrar otro ejemplo, diferente al del apartado anterior, lo vamos instalar en la carpeta de usuario (en mi caso c:\Users\OpenWebinars). También deberíamos añadir la ruta a la carpeta bin como parte de la variable de entorno PATH.

37.3 Utilización de Spring Boot CLI
Si bien el sistema CLI es utilizado, sobre todo, por los programadores Groovy, los programadores Java también se pueden valer de él, sobre todo aquellos que son amantes de la línea de comandos, o los que quieren automatizar algún tipo de proceso.

37.3.1 Creación de un nuevo proyecto
Para crear un nuevo proyecto con Spring Boot CLI tan solo tenemos que crear un nuevo directorio en la ubicación que queramos. Una vez creado, ejecutamos la siguiente línea:

c:\...>spring init -d=web project-dir
Este comando creará una carpeta, llamada project-dir en la ubicación correspondiente, e iniciará el proyecto como un proyecto web. La lista de plantillas disponibles se puede obtener mediante el siguiente comando:

c:\...>spring init --list
Si lo que queremos es obtener un proyecto web y jpa, la sintaxis sería:

c:\...>spring init -d=web,jpa project-dir
La sintaxis es muy variable, y tiene muchas opciones. Por ello, siempre que queramos podemos consultar la ayuda con el siguiente comando:

c:\...>spring help [<nombre-del-comando>]
Cualquier proyecto generado de esta forma puede ser importado después en Spring Tool Suite, como un proyecto Maven.

En el fondo, este tipo de instalación no es más que un atajo a Spring Initializr, que nos evita entrar en la web y tener que escribir sobre el formulario las opciones, y que incluso nos da el fichero descomprimido.

37.3.2 Ejecución de un proyecto
La herramienta CLI también nos permite ejecutar proyectos. Como ejemplo, hemos añadido en el directorio correspondiente la siguiente clase, que hemos editado a mano:

package com.example;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
class ThisWillActuallyRun {

    @RequestMapping("/")
    @ResponseBody
    public String home() {
        return "Hello World!";
    }

}
Para ejecutar el proyecto, tan solo tenemos que ponernos un nivel por encima del directorio project-dir, y ejecutar el siguiente comando:

c:\...>spring run <project-dir>
Esto provocará que Spring escanee el proyecto, localice el punto de entrada y lance la aplicación.

37.3.3 Otras opciones de Spring Boot CLI
El comando spring tiene algunas opciones más:

spring test: lanza los test de un determinado proyecto

spring jar: crea un jar ejecutable del proyecto

spring war: crea un war ejecutable del proyecto

spring install: instala dependencias dentro del proyecto

spring uninstall: desinstala dependencias del proyecto

spring shell: inicial una consola propia dentro de la consola, lo que nos permite invocar los comandos sin llamar a spring


39.1 Introducción
REST (Representational State Transfer, Transferencia de estado representacional) es una arquitectura de software, orientada a la creación de servicios web escalables. El término fue acuñado por Roy Fielding, y ha revolucionado la forma de realizar servicios web.

39.2 Interfaz uniforme
REST es una interfaz que se apoya totalmente sobre el protocolo HTTP (del que ya hablamos anteriormente). Nos permite crear servicios y aplicaciones que pueden ser usadas por cualquier dispositivo que entienda HTTP (a día de hoy, múltiples dispositivos lo hacen), por lo que es más simple y convencional que esquemas de servicios web más clásicos, como SOAP o XML-RPC.

El lenguaje REST habla de recursos (en inglés resources), y estos son identificados mediante URIs (Uniform Resource Identifiers). Conceptualmente, los recursos se separan de su representación (es decir, del formato en el que se proveen a los clientes). De hecho, REST no exige ningún formato de salida específico, si bien lo más natural es encontrar XML (cada vez menos) y JSON (que casi podríamos decir que es un estándar de facto).

El interfaz uniforme de acceso a cualquier servicio REST viene definido por un conjunto de operaciones y un conjunto de tipos de contenido.

39.3 Métodos y verbos
Aunque más delante profundizaremos, REST realiza un uso de los métodos de HTTP para la gestión de recursos:

Método	Función	Operación
GET	Solicitar un recurso	Read
POST	Crear un nuevo recurso	Create
PUT	Actualizar o modificar un recurso	Update
DELETE	Borrar un recurso	Delete
39.4 ¿Cómo crear una interfaz basada en REST?
Como decíamos antes, REST pone énfasis en el recurso, y no en métodos (por hacer una comparación con el lenguaje, REST hablaría sustantivos, y otros estándares de servicios web, como SOAP, hablaría verbos). De esta forma, REST utiliza URIs para obtener recursos.

Si por ejemplo estuviéramos trabajando con ún recurso de tipo Empleado, y realizados un buen proceso de abstracción, podríamos decir que tendríamos dos tipos de recursos:

Empleado (Una URI por empleado completo)

TodosEmpleados (Listado de todos los empleados)
Según la tabla anterior, si combinarmos los recursos y los métodos, obtendríamos lo siguiente:

Recurso	Método	Representación
Empleado	GET	Representación de un empleado
Empleado	PUT	Representación de un empleado
Empleado	DELETE	-
TodosEmpleados	GET	Representación de la lista de empleados
TodosEmpleados	POST	Representación de un empleado
Si esto lo llevamos a un plano real, y transformamos las URIs en URLs, podríamos crear una interfaz REST completa.

URL	Método	Representación
http://www.service.com/api/empleado/{id}	GET	Representación de un empleado
http://www.service.com/api/empleado/{id}	PUT	Representación de un empleado
http://www.service.com/api/empleado/{id}	DELETE	-
http://www.service.com/api/empleado	GET	Representación de la lista de empleados
http://www.service.com/api/empleado	POST	Representación de un empleado
Como podemos comprobar, la URL para obtener un empleado sería:

http://www.service.com/api/empleado/123
y no sería del estilo:

http://www.service.com/api/getEmpleado?id=123
En REST, los recursos se expresan como nombres, y no como verbos.

39.5 Servicios autodescriptivos
Idealmente, un cliente de un servicio REST necesitaría conocer a priori solo una URL, la de entrada al servicio. El resto de operaciones serían guiadas por las representaciones por las que se van navegando:

Hiperenlaces a otros recursos

Plantillas de consulta/actualización que permitan operar sobre otros recursos (algo parecido a un formulario de búsqueda)
Además, las representación debería devolverse en un formato conocido a priori por el máximo número de clientes. De esta forma, desacoplamos lo máximo posible el cliente y el servidor, siendo lo más funcionales posibles.



40.1 Introducción
El modelo cliente/servidor que propone REST permite la separación entre las preocupaciones del cliente (como por ejemplo, la interacción con el usuario) y las del servidor (como por ejemplo, el almacenamiento de datos). Este desacoplamiento garantiza que siempre que se establezca una interfaz REST entre ambos, el desarrollo de los dos sistemas se puede realizar casi de forma independiente.

40.2 Arquitectura cliente/servidor
REST, al descansar sobre el protocolo HTTP, se implementa bajo la arquitectura cliente/servidor. Esta es un modelo de aplicación distribuida (es decir, varias máquinas tienen que colaborar entre sí), en el que las tareas se reparten entre los elementos que proveen recursos o servicios (llamados servidores) y los demandantes, llamados clientes.



Los servidores, de forma genérica, pueden ser de dos tipos: con estado o sin estado. Un servidor con estado, como su nombre indica, puede recordar que un cliente ya realizó una petición específica de forma que, si realiza una misma petición dos veces, el resultado de ejecutar la petición por segunda vez sea diferente al de la primera vez. Un servidor sin estado no es capaz de guardar información entre las peticiones. Todos los servidores HTTP son servidores sin estado, y por ende, cualquier servidor REST que implementemos también.

40.3 Cliente REST y Servidor REST
Como ya hemos dicho anteriormente, REST nos servirá para ofrecer recursos a través de un servicio web. Es decir, REST va a permitir a dos sistemas (potencialmente) heterogéneos (es decir, con plataformas diferentes) colaborar para consumir o producir datos. Veamos los siguientes gráficos:





De los anteriores gráficos podemos inferir varias cosas:

Un cliente REST puede ser cualquier cosa: efectivamente, cualquier dispositivo con un cliente HTTP (a día de hoy, hay miles de ellos) podría serlo (un smartphone, un pc, una placa de arduino…).

Los clientes realizan peticiones y los servidores producen respuestas: este será el esquema básico de trabajo con REST. Cualquier cliente que necesite un recurso lanzará una petición, y el servidor le enviará una representación de ese recurso como respuesta.

Se utiliza un formato de representación inteligible para todos: como decíamos en alguna lección anterior, JSON es casi un estándar de facto en el mundo REST. Los clientes son libres de buscar la mejor manera de interpretarlo (JacksonMapper, GSON, …)
En las próximas lecciones podremos aprender como Spring nos ofrece facilidades tanto para la elaboración de servidores REST, que expongan recursos; como la creación de clientes REST, que fácilmente podrán consumirlos.


41.1 Introducción
¡Pongámonos manos a la obra! Para ello, vamos a realizar nuestro primer endpoint. En el mundo REST, un endpoint no es más que la exposición de un recurso a través de un servicio web, del cual puede consumir un cliente.

41.2 ¿Qué vamos a construir?
Vamos a construir un servicio que aceptará una petición HTTP GET a la url:

http://localhost:8080/greeting
y responderá con una representación JSON de un greeting:

{"id": 1, "content": "Hello, World!"}
Se podrá customizar el saludo con un parámetro, name, que será opcional en la URL.

http://localhost:8080/greeting?name=User
y entonces, el servicio responderá:

{"id":1,"content":"Hello, User!"}
41.3 Importación del proyecto
Al igual que hicimos en la lección 33, vamos a importar un proyecto desde el repositorio de ejemplos de Spring. En particular, vamos a trabajar con el proyecto, Rest Service, con los parámetros que indica la siguiente imagen:



41.4 Nuestro modelo
El proyecto tiene una única clase modelo, Greeting:

public class Greeting {

    private final long id;
    private final String content;

    public Greeting(long id, String content) {
        this.id = id;
        this.content = content;
    }

    public long getId() {
        return id;
    }

    public String getContent() {
        return content;
    }
}
Cómo podemos ver, no tiene ningún tipo de anotación. Spring (gracias a Spring Boot) se encargará de realizar la transformación mediante JacksonMapper.

41.5 El controlador
En este caso, el controlador hace uso de alguna anotación especial. En particular, utiliza @RestController. Esta anotación indicará, nueva en Spring 4.X, indica que se trata de un controlador especial, donde todo lo que sea devuelto será un objeto de nuestro dominio, y no una vista. Es un atajo del uso conjunto de @Controller y @ResponseBody.


@RestController
public class GreetingController {

    private static final String template = "Hello, %s!";
    private final AtomicLong counter = new AtomicLong();

    @RequestMapping("/greeting")
    public Greeting greeting(@RequestParam(value="name", defaultValue="World") String name) {
        return new Greeting(counter.incrementAndGet(),
                            String.format(template, name));
    }
}
41.6 Algunas modificaciones
Para probar que este servicio puede escalar de una forma sencilla, y devolver un objeto más complejo, podemos añadir algunas propiedades más a nuestra clase modelo, si modificar ninguna línea de código más. Siempre y cuando Jackson Mapper sea capaz de transformar el objeto, obtendremos una respuesta JSON correcta..



42.1 REST y el patrón Modelo-Vista-Controlador
Si rescatamos lo que estudiamos en la lección 11 sobre el patrón MVC, recordaremos que se trata de un patrón arquitectónico (es decir, en la forma de organizar el código), de manera que el código queda definido en Modelo (Objetos de Negocio), la Vista (interfaz con el usuario u otro sistema) y el Controlador (controlador del flujo o workflow de la aplicación).



Si trasladamos esto a lo que hemos introducido en las lecciones anteriores sobre servicios REST, podemos inferir lo siguiente:

Dentro de una aplicación MVC, nuestro modelo serán los recursos de los que habla REST.

Ya que el modelo RESTful utiliza HTTP y sus verbos para la gestión de recursos, el controlador tendrá una gran importancia para recibir y tratar las diferentes peticiones.

La vista, de la cual habla el patrón MVC, no va a ser prácticamente nunca HTML o algún sistema de templates, que tan bien soporta Spring, sino un lenguaje que permita el intercambio de datos entre sistemas heterogéneos (como JSON o XML).
42.2 MVC en el cliente y la potencia de REST
Por un lado, de sobra es sabido que cada vez más diferentes tipos de dispositivos son capaces de acceder a contenidos en internet. De la mano, están surgiendo cada vez más tecnologías, como por ejemplo Angular, que nos permiten implementar MVC de una forma diferente a la clásica. Y lo mismo podríamos decir de Android, iOS, etc…

De esta forma, de alguna manera podríamos decir que el patrón MVC se ha multiplicado, para quedar implementado en el lado cliente, de forma que el lado servidor queda solo para surtir de datos en JSON.

Gracias a todas estas tecnologías, la arquitectura REST se está convirtiendo en un referente a la hora de desarrollar software.



43.1 Introducción
Como hablábamos en lecciones anteriores, un servicio web REST que se precie ofrecerá, para un recurso concreto, la posibilidad de hacer todos los métodos CRUD, a través de los correspondientes verbos HTTP. Por ejemplo para un recurso Empleado (empleadoId, nombre, apellidos, fechaNacimiento) debería exponer, entre otras URLs:

URL	verbo HTTP	Respuesta
http://www.server.com/api/empleado	GET	Obtener los datos de todos los empleados
http://www.server.com/api/empleado/{id}	GET	Obtener los datos del empleado {id}
43.2 Desarrollo de los servicios
Partiendo de un proyecto base orientado a web, que podremos construir con el asistente de STS, comenzamos desarrollando nuestra clase modelo:

public class Empleado {

    private long id;
    private String nombre;
    private String apellidos;
    private Date fechaNacimiento;

    public Empleado() {}


    public Empleado(long id, String nombre, String apellidos, Date fechaNacimiento) {
        this.id = id;
        this.nombre = nombre;
        this.apellidos = apellidos;
        this.fechaNacimiento = fechaNacimiento;
    }

    public long getId() {
        return id;
    }

    public void setId(long id) {
        this.id = id;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getApellidos() {
        return apellidos;
    }

    public void setApellidos(String apellidos) {
        this.apellidos = apellidos;
    }

    public Date getFechaNacimiento() {
        return fechaNacimiento;
    }

    public void setFechaNacimiento(Date fechaNacimiento) {
        this.fechaNacimiento = fechaNacimiento;
    }

}
Un controlador capaz de exponer los servicios que hemos indicado más arriba sería como este:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    List<Empleado> repo;

    @GetMapping("/empleado")
    public List<Empleado> list() {
        return repo;
    }

    @GetMapping("/empleado/{id}") 
    public Empleado getEmpleado(@PathVariable Long id) {
        if (id > 0 && id <= repo.size()) {
            return repo.get((int) (id-1));
        }

        return null;
    }


    @PostConstruct
    private void init() {

        repo = new ArrayList<Empleado>();
        repo.add(new Empleado(1L, "Pepe", "Gotera", new Date()));
        repo.get(0).getCitas().add(new Cita(1L, "Reunión de trabajo", new Date()));
        repo.get(0).getCitas().add(new Cita(2L, "Visita a un cliente", new Date()));

        repo.add(new Empleado(2L, "Otilio", "García", new Date()));
        repo.get(1).getCitas().add(new Cita(3L, "Visita a un proveedor", new Date()));

        repo.add(new Empleado(3L, "Mortadelo", "Gómez", new Date()));
        repo.add(new Empleado(4L, "Filemón", "Guzmán", new Date()));
        repo.add(new Empleado(5L, "Super", "López", new Date()));
    }


}
Como almacén de datos, hemos creado un repositorio estático dentro de una lista.

De esta forma, la invocación de los servicios produciría como resultado, directamente, un JSON. Por ejemplo, si invocamos mediante una petición GET a:

http://localhost:8080/api/empleado
tendremos como resultado:

[{"id":1,"nombre":"Pepe","apellidos":"Gotera","fechaNacimiento":1479152095985,"citas":[{"id":1,"texto":"Reunión de trabajo","fecha":1479152095985},{"id":2,"texto":"Visita a un cliente","fecha":1479152095985}]},{"id":2,"nombre":"Otilio","apellidos":"García","fechaNacimiento":1479152095985,"citas":[{"id":3,"texto":"Visita a un proveedor","fecha":1479152095985}]},{"id":3,"nombre":"Mortadelo","apellidos":"Gómez","fechaNacimiento":1479152095985,"citas":[]},{"id":4,"nombre":"Filemón","apellidos":"Guzmán","fechaNacimiento":1479152095985,"citas":[]},{"id":5,"nombre":"Super","apellidos":"López","fechaNacimiento":1479152095985,"citas":[]}]
43.3 Servicios anidados
En muchas ocasiones nos encontraremos en la situación de que dos clases modelo tienen una asociación de composición entre ellas, de forma que la primera tendrá dentro una colección de instancias de la segunda.

Utilizando el esquema REST, es buena práctica definir los servicios de la siguiente forma:

/api/outer/{id}/nested
De esta forma, indicamos que queremos todas las instancias del recurso nested asociadas a la instancia {id} del recurso outer.

En el contexto de nuestro ejemplo, vamos a crear una segunda clase, para manejar las citas de un empleado:

public class Cita {

    private Long id;
    private String texto;
    private Date fecha;

    public Cita() { }

    public Cita(Long id, String texto, Date fecha) {
        this.id = id;
        this.texto = texto;
        this.fecha = fecha;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getTexto() {
        return texto;
    }

    public void setTexto(String texto) {
        this.texto = texto;
    }

    public Date getFecha() {
        return fecha;
    }

    public void setFecha(Date fecha) {
        this.fecha = fecha;
    }

}
Y vamos a añadir a la clase empleado todo lo necesario para almacenar y gestionar estas citas:

public class Empleado {
    //resto de atributos
    private List<Cita> citas;

    //resto de código

    public Empleado(long id, String nombre, String apellidos, Date fechaNacimiento) {
        this.id = id;
        this.nombre = nombre;
        this.apellidos = apellidos;
        this.fechaNacimiento = fechaNacimiento;
        this.citas = new ArrayList<Cita>();
    }


    public List<Cita> getCitas() {
        return citas;
    }


    public void setCitas(List<Cita> citas) {
        this.citas = citas;
    }

    //resto del código

}
Para exponer las citas, tendríamos que añadir dos nuevos métodos en el controlador, que devuelvan una instancia de Cita y una colección List<Cita>.

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    //resto del código

    @GetMapping("/empleado/{id}/cita")
    public List<Cita> getCitasEmpleado(@PathVariable Long id) {
        if (id > 0 && id <= repo.size()) {
            return repo.get((int) (id-1)).getCitas();
        }

        return null;
    }

    @GetMapping("/empleado/{idE}/cita/{idC}")
    public Cita getCitaEmpleado(@PathVariable Long idE, @PathVariable Long idC) {
        Cita result = null;

        if (idE > 0 && idE <= repo.size()) {
            List<Cita> citas = repo.get((int) (idE-1)).getCitas();
            if (citas != null) {
                for (Cita c : citas) 
                    if (c.getId() == idC)
                        result = c;
            }
        }

        return result;
    }

    //resto del código


}

44.1 Recursos y representación de los datos
Cuando pensamos en un API, es muy normal pensar en sus endpoints, es decir, en sus URLs. Con REST, si tienes una URL, entonces tienes un recurso. Por ello, en el ejemplo de la lección anterior, /api/empleado/1 nos proporcinaba un empleado, y /api/empleado nos proporcionaba una lista de ellos (una colección también se puede considerar como un recurso).

44.1.1 Representación
Ahora que hemos entendido los recursos, hablemos de representación de los mismos. Supongamos que un cliente realiza una petición GET al ejemplo de la lección anterior, /api/empleado/1, donde la respuesta JSON será:

{"id":1,"nombre":"Pepe","apellidos":"Gotera","fechaNacimiento":1479152095985,"citas":[{"id":1,"texto":"Reunión de trabajo","fecha":1479152095985},{"id":2,"texto":"Visita a un cliente","fecha":1479152095985}]}
Este es el recurso empleado, ¿verdad? ¡ERROR! Esto es justo una representación del recurso. En este caso, el servidor la devuelve en un formato (JSON), pero la podría haber devuelto en otros, com XML, HTML, … Esto funcionaría también con otras peticiones, como POST, en la que es el cliente el que envía datos al servidor.

Este es exactamente el motivo por el que la web funciona, y funciona como lo hace. Una página HTML no es un recurso, sino solamente una representación del mismo. Cuando nosotros enviamos información en un formulario, estamos enviando una representación diferente hacia el servidor.

Un recurso puede tener diferentes representaciones. Por ejemplo, podríamos volvernos locos y querer implementar un API que solicitara las representaciones en HTML, XML o JSON de cualquier recurso.

Una representación no es más que una forma de explicar el estado actual de un recurso, en un formato legible para una máquina. Y sí, hemos usado la palabra estado, ya que cuando el cliente hace la anterior petición GET, obtiene un JSON con la representación actual, es decir, los datos actuales.

En lenguaje REST, un cliente y un servidor intercambian representaciones de un recurso, que reflejan el estado actual o deseado de un recurso. REST es una manera de que dos máquinas transfieran el estado de un recurso a traves de sus representaciones.

45.1 Formato de la respuesta por defecto
Como hemos visto en la lección anterior, es nuestro servidor el que se encarga de devolver una representación del recurso al que queremos acceder. Por defecto, esta representación es en JSON.

45.2 Obtener la respuesta en XML
Cambiar la representación, es decir, el formato, de la respuesta de petición de un recurso con Spring es tremendamente fácil. Spring Boot ha configurado nuestro proyecto para añadir todos los HttpMessageConverters necesarios. Tan solo tenemos que hacer dos pequeñas tareas:

45.2.1 Añadir dependencias
Tenemos que añadir una nueva dependencia al pom.xml, con la librería que se encargará de realizar la transformación.

        <dependency>
            <groupId>com.fasterxml.jackson.dataformat</groupId>
            <artifactId>jackson-dataformat-xml</artifactId>
        </dependency>
45.2.2 Añadir las anotaciones de JAXB
Esta librería utiliza las etiquetas de JAXB (Java Architecture for XML Binding) para realizar la serialización y deserialización de instancias de java en cadenas XML y viceversa.

Nuestra clases (sin perjuicio para la transformación en JSON) quedarían ahora de la siguiente forma:

package com.openwebinars.springrest.model;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;

import javax.xml.bind.annotation.XmlElement;
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement(name="empleado")
public class Empleado {

    //resto del código   

    @XmlElement
    public List<Cita> getCitas() {
        return citas;
    }


    @XmlElement
    public long getId() {
        return id;
    }

    @XmlElement
    public String getNombre() {
        return nombre;
    }

    @XmlElement
    public String getApellidos() {
        return apellidos;
    }


    @XmlElement
    public Date getFechaNacimiento() {
        return fechaNacimiento;
    }

    //resto del código   


}
 
package com.openwebinars.springrest.model;

import java.util.Date;

import javax.xml.bind.annotation.XmlElement;
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement
public class Cita {

    //resto del código

    @XmlElement
    public Long getId() {
        return id;
    }

    @XmlElement
    public String getTexto() {
        return texto;
    }

    @XmlElement
    public Date getFecha() {
        return fecha;
    }

    //resto del código

}
Por último, para obtener la salida en XML, tenemos que indicárselo explícitamente en la petición. La forma más transparente de hacerlo es incluyendo en la misma una cabecera: Accept : application/xml.

45.3 Cambios en la configuración de salida del JSON
Nuestro proyecto, creado con Spring Boot bajo el paradigma CoC (Convención sobre configuración), tiene una configuración por defecto para la salida en JSON que puede ser modificada si lo deseamos.

Para ello, tenemos que crear una clase que extienda a WebMvcConfigurerAdapter, y anotarla con @Configuration y @EnableWebMVC.

@Configuration
@EnableWebMvc
public class JsonConfiguration extends WebMvcConfigurerAdapter {
    @Override
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {
        converters.add(new MappingJackson2HttpMessageConverter(
                new Jackson2ObjectMapperBuilder().propertyNamingStrategy(PropertyNamingStrategy.LOWER_CASE)
                        .serializationInclusion(Include.NON_NULL).build()));

        converters.add(new MappingJackson2XmlHttpMessageConverter());
    }
}
De esta forma, en lugar de utilizar la estrategia camel case para generar los nombres de las propiedades, obtendríamos como salida todos ellos en minúscula.



46.1 Introducción
Hasta ahora todo ha ido sobre ruedas pero, ¿qué sucede si solicitamos un recurso que no existe? ¿o si realizamos una petición que no sea correcta? REST, al descansar sobre HTTP, utiliza los códigos de respuesta de este protocolo para gestionar las posibles contingencias.

46.2 Códigos de respuesta
El protocolo HTTP va mucho más allá de lo que estamos acostumbrados a usarlo. De hecho, toda respuesta a una petición, debe llevar siempre aparejado un código de respuesta. Si todo va OK, este código será 200. La respuesta de error más conocida es la 404, que está asociada a un recurso no encontrado. Rescatemos los códigos de respuesta más usuales de la lección sobre HTTP:

Códigos 1XX: Mensajes
100-111 Conexión rechazada

Códigos 2XX: Operación realizada con éxito
200 OK

201-203 Información no oficial

204 Sin contenido

205 Contenido para recargar

206 Contenido parcial

Códigos 3XX: Redirección
301 Mudado permanentemente

302 Encontrado

303 Vea otros

304 No modificado

305 Utilice un proxy

307 Redirección temporal

Códigos 4XX: Error por parte del cliente
400 Solicitud incorrecta

402 Pago requerido

403 Prohibido

404 No encontrado

409 Conflicto

410 Ya no disponible

412 Falló precondición

Códigos 5xx: Error del servidor
500 Error interno

501 No implementado

502 Pasarela incorrecta
503 Servicio no disponible

504 Tiempo de espera de la pasarela agotado

505 Versión de HTTP no soportada
Como podemos comprobar, ya en su día marcábamos los más interesantes, que serán los que más utilicen los diferentes servicios REST.

46.3 Formas de implementar la gestión de errores
Por ser el más frecuente, nos vamos a centrar en el error 404 (recurso no encontrado)

46.3.1 A través del objeto HttpServletResponse
Como ya dijimos en las lecciones de Spring MVC, la firma de los métodos dentro de un controlador es muy variable, ya que pueden (o no) recibir muchas cosas. Entre ellas está un objeto de tipo HttpServletResponse. Este objeto representa la respuesta que va a ser enviada al cliente. Si modificamos directamente el código de la respuesta, enviaremos una respuesta con código 404 al cliente, si bien la respuesta estará vacía.

    @GetMapping("/empleado/{id}") 
    public Empleado getEmpleado(@PathVariable Long id, HttpServletResponse response) {
        if (id > 0 && id <= repo.size()) {
            return repo.get((int) (id-1));
        } else {
            response.setStatus(404);
            return null;
        }
    }
Si comprobamos con una petición al servicio con el ID de un empleado que no exista (por ejemplo, 78), obtenedremos un error 404.

46.3.2. A través del manejo de excepciones
Spring incluye un gran número de excepciones para el manejo de errores asociados a los códigos de respuesta. En la documentación oficial los podemos consultar. Uno de ellos, NoHandlerFoundException, es invocado cuando intentamos realizar una petición a un controlador que no existe. Si en el método, lanzamos la excepción cuando no encontremos una cita (por ejemplo, por invocar a la url /api/empleado/2/cita/123), obtendremos un error 404, aparejado de un mensaje, en JSON, con una descripción genérica del error.

    @GetMapping("/empleado/{idE}/cita/{idC}")
    public Cita getCitaEmpleado(@PathVariable Long idE, @PathVariable Long idC,  HttpServletRequest request) throws NoHandlerFoundException {
        Cita result = null;

        if (idE > 0 && idE <= repo.size()) {
            List<Cita> citas = repo.get((int) (idE-1)).getCitas();
            if (citas != null) {
                for (Cita c : citas) 
                    if (c.getId() == idC)
                        result = c;
            }
        } 
        if (result != null)
            return result;
        else 
            throw new NoHandlerFoundException("GET", request.getRequestURL().toString(), null);
    }
46.3.2.1 Modificación del mensaje de error
Ya que la descripción del mensaje de error que hemos obtenido es genérica, es razonable pensar en cambiarlo. La forma más fácil es a través de las anotaciones @ExceptionHandler y @ResponseStatus. De esta forma, para este controlador puenteamos la gestión de una excepción en particular, devolviendo un determinado código de respuesta, y modificando el mensaje a nuestro antojo. Estas dos anotaciones se las podemos añadir a un método privado del controlador, que en sí, no tiene por qué hacer nada.

    @ResponseStatus(value=HttpStatus.NOT_FOUND, reason="La cita no existe")
    @ExceptionHandler(NoHandlerFoundException.class)
    public void citaInexsistente() {
        //vacío
    }
46.3.2.2 Creación de nuestras propias clases de excepción
En último lugar, pero no por ello menos importante, ya que es uno de los modelos más recomendables, podemos pensar en crear nuestras propias clases que hereden de RuntimeException, y anotadas con @ResponseStatus. De esta forma, en lugar de lanzar una excepción genérica, lanzaríamos una definida por nosotros.

    @ResponseStatus(value=HttpStatus.NOT_FOUND, reason="El empleado no existe")
    private class EmpleadoNotFoundException extends RuntimeException {

        private static final long serialVersionUID = -5798132769496018860L;

    }
Si queremos modificar el mensaje para que pueda recibir parámetros, podemos añadir un constructor que utilice uno de los de la clase base:

    @ResponseStatus(value=HttpStatus.NOT_FOUND)
    private class EmpleadoNotFoundException extends RuntimeException {

        private static final long serialVersionUID = -5798132769496018860L;

        public EmpleadoNotFoundException(Long id) {
            super(String.format("El empleado %d no existe",id));            
        }

    }
	
	
	
	47.1 Operaciones CRUD en servicios REST
A continuación, vamos a presentar cual debería ser la arquitectura completa de un servicio para un determinado recurso, para que pueda realizar todas las operaciones CRUD (crear, obtener, actualizar y borrar).

URL	Método HTTP	Descripción	Código de respuesta correcta
/api/empleados	GET	Obtener la lista de todos los empleados	200 OK
/api/empleado/{id}	GET	Obtener los datos del empleado {id}	200 OK
/api/empleado	POST	Crear un nuevo empleado	201 Created
/api/empleado/{id}	PUT	Modificar un empleado existente	200 OK
/api/empleado/{id}	DELETE	Eliminar un empleado existente	200 OK
47.2 Datos para el proyecto
Vamos a crear un nuevo proyecto Spring Boot con el asistente de STS. Marcamos las opciones Web, Jpa y H2.

En el fichero application.properties añadimos las siguientes propiedades

spring.datasource.url=jdbc:h2:./ejemplo-spring-boot
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver
Esto nos permitirá crear una base de datos que funcionará en memoria.

47.3 Clases del proyecto
El código usado en el proyecto se va a parecer, en primera instancia, a cualquier proyecto Web/JPA que pudiéramos crear:

Empleado.java


@Entity
public class Empleado {

    @Id
    @GeneratedValue(strategy=GenerationType.AUTO)
    private long id;
    @Column
    private String nombre;
    @Column
    private String apellidos;
    @Column
    private Date fechaNacimiento;


    public Empleado() {}


    public Empleado(long id, String nombre, String apellidos, Date fechaNacimiento) {
        this.id = id;
        this.nombre = nombre;
        this.apellidos = apellidos;
        this.fechaNacimiento = fechaNacimiento;
    }

    public Empleado(String nombre, String apellidos, Date fechaNacimiento) {
        this.nombre = nombre;
        this.apellidos = apellidos;
        this.fechaNacimiento = fechaNacimiento;
    }

    //getters y setters


    //hashCode y equals también han sido autogenerados

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + ((apellidos == null) ? 0 : apellidos.hashCode());
        result = prime * result + ((fechaNacimiento == null) ? 0 : fechaNacimiento.hashCode());
        result = prime * result + (int) (id ^ (id >>> 32));
        result = prime * result + ((nombre == null) ? 0 : nombre.hashCode());
        return result;
    }


    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Empleado other = (Empleado) obj;
        if (apellidos == null) {
            if (other.apellidos != null)
                return false;
        } else if (!apellidos.equals(other.apellidos))
            return false;
        if (fechaNacimiento == null) {
            if (other.fechaNacimiento != null)
                return false;
        } else if (!fechaNacimiento.equals(other.fechaNacimiento))
            return false;
        if (id != other.id)
            return false;
        if (nombre == null) {
            if (other.nombre != null)
                return false;
        } else if (!nombre.equals(other.nombre))
            return false;
        return true;
    }

}
EmpleadoRepository.java

@Repository
public interface EmpleadoRepository extends JpaRepository<Empleado, Long>{

}
El controlador es el que va a verse algo modificado para que nos sirva a modo de controlador de Servicio REST:

EmpleadoController.java

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;


    @GetMapping("/empleados")
    public List<Empleado> list() {
        List<Empleado> result = empleadoRepository.findAll();
        if (result != null)
            return result;
        else
            throw new EmpleadoNotFoundException();
    }

    @GetMapping("/empleado/{id}") 
    public Empleado getEmpleado(@PathVariable Long id) {
        Empleado result = empleadoRepository.findOne(id);
        if (result != null)
            return result;
        else
            throw new EmpleadoNotFoundException(id);
    }

    @PostMapping("/empleado")
    public Empleado createEmpleado(/* ... */) {
        return null;
    }

    @PutMapping("/empleado/{id}")
    public Empleado updateEmpleado(/* ... */) {
        return null;
    }


    @DeleteMapping("/empleado/{id}")
    public Empleado deleteEmpleado(/* .... */) {
        return null;
    }


    @ResponseStatus(value=HttpStatus.NOT_FOUND)
    private class EmpleadoNotFoundException extends RuntimeException {

        private static final long serialVersionUID = 7295910574475009536L;


        public EmpleadoNotFoundException() {
            super("No existe ningún empleado");
        }

        public EmpleadoNotFoundException(Long id) {
            super(String.format("No existe ningún empleado con el ID = %d", id));
        }

    }

}
Como elementos a destacar:

El uso de la anotación @RestController. Nos permite indicar que este controlador es especial, y que se usa como controlador de servicio REST.
Los métodos createEmpleado, updateEmpleado y deleteEmpleado, cuya explicación en profundidad dejamos para las siguientes lecciones.
La definición, como clase privada (esto lo hemos hecho por simplicidad, ya que dicha excepción no se va a utilizar en otra clase diferente), de la excepción EmpleadoNotFoundException, mediante la cual vamos a sobreescribir el comportamiento por defecto del error 404, enviando al usuario un mensaje de error propio.
En la clase Application.java hemos añadido un código que solo sirve para que, al iniciar la aplicación, la base de datos se rellene con algunos datos iniciales de empleados. Se ha hecho uso de las anotación @Bean, que nos permitía definir un bean dentro de un método (véase la lección de JavaConfig); dentro hace uso de Java 8 y sus expresiones lambda, si bien este contenido queda fuera del alcance de este curso. El bean es de tipo CommandLineRunner, propio de Spring Boot, y nos permite ejecutar un bloque de código al iniciarse una aplicación mediante SpringApplication.run(...).

Aplication.java

@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @Bean
    CommandLineRunner init(EmpleadoRepository empleadoRepository) {

        String[][] data = {
                {"José", "García Martínez", "01/01/1975"},
                {"Manuel", "Pérez Díaz", "10/10/1978"},
                {"Luis Miguel", "López Magaña", "18/09/1982"},
                {"Alberto", "Jiménez Sarmiento", "03/03/1973"},
                {"Carlos", "Ruiz Santos", "02/12/1978"},
                {"Martín", "López Alfaro", "04/05/1976"},
                {"María", "Martínez Sánchez", "14/07/1983"},
                {"Luisa", "Milán Llanes", "28/08/1978"}
        };

        final DateFormat df = new SimpleDateFormat("dd/MM/yyyy");

        return (evt) -> Arrays.asList(data)
                .forEach(a -> {

                    try {
                        empleadoRepository.save(new Empleado(a[0], a[1], df.parse(a[2])));
                    } catch (Exception e) {                     
                        e.printStackTrace();
                    }
                });
    }
}


48.1 Introducción a RequestBody y ResponseBody
En las lecciones anteriores hemos podido aprender que la anotación @RestController, era, de algún modo, una anotación compuesta, que nos evitaba tener que usar @Controller y @ResponseBody.

La anotación @ResponseBody, usada en un método particular (podemos ver la lección en la que creamos nuestro primer servicio REST) nos permitía indicarle a Spring que el tipo de retorno del método debía ser la respuesta que enviara al cliente, de forma que tenía que buscar entre sus Http Converters el mejor candidato para realizar esta operación.

Conozcamos un poco mejor las anotaciones ResponseBody y RequestBody y como podemos utilizarlas para en los servicios REST en general, y en la creación de recursos en particular.

48.1.1 Peticiones y respuestas: RequestEntity y ResponseEntity
Como ya pudimos trabajar en la lección sobre HTTP, este protocolo trabaja con un esquema de petición y respuesta. Ambas tienen la misma estructura, con dos partes bien diferenciadas: la cabecera y el cuerpo. En una respuesta, la cabecera nos indicará diferentes parámetros (código de respuesta, fecha, tipo de dato, datos del servidor), y el cuerpo contendrá el recurso que esperamos. Una petición, por ejemplo, de tipo POST, tendrá una cabecera, con sus correspondientes parámetros (URL hacia la cual lanzamos la petición, fecha, cliente, …) y un cuerpo (el recurso que enviamos al servidor para que sea dado de alta). Una de tipo GET, por ejemplo, tendrá por norma el cuerpo vacío.

La clase RequestEntity<> que nos provee Spring representa una petición, dándonos acceso a su cabecera y a su cuerpo; análogamente, ResponseEntity<> nos da acceso a su estructura. Estas clases son paramétrizadas, es decir, esperan otro tipo de clase dentro de los ángulos. Por ejemplo, RequestEntity<Empleado> sería un tipo de dato petición, que llevará dentro una instancia de Empleado.

48.2 ¿Cuándo escoger usar las anotaciones y cuando las clases?
Veamos, asociado al alta de un nuevo recurso, como sería la implementación del servicio. Recordemos primero su estructura:

URL	Método HTTP	Código de respuesta correcta	Códigos de respuesta errónea
/api/empleado	POST	201 Created	400 Bad Request
409 Conflict
48.2.1 Implementación con anotaciones
La forma más fácil de implementación de este servicio sería a través del uso de @RequestBody. Veamos el código:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @PostMapping("/empleado")
    public Empleado createEmpleado(@RequestBody Empleado empleado, HttpServletResponse response) {
        Empleado nuevo = new Empleado(empleado.getNombre(), 
            empleado.getApellidos(), 
            empleado.getFechaNacimiento());
        response.setStatus(201);
        return empleadoRepository.save(nuevo);
    }

    //resto del código


}
De esta forma, evitamos errores de duplicidad obviando el ID del empleado (ya que este se autogenera en la base de datos). Para enviar el código de respuesta, usamos el esquema más básico, a través de HttpServletResponse. Pero, ¿cómo realizaríamos la gestión de errores? Tendríamos que revisitar la lección 45, aunque podemos ver otra forma de implementación.

48.2.2 Implementación con RequestEntity<> y ResponseEntity<>
Una posible implementación, haciendo uso de estas clases, sería la siguiente:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @PostMapping("/empleado")
    public ResponseEntity<?> createEmpleado(RequestEntity<Empleado> reqEmpleado) {
        Empleado empleado = reqEmpleado.getBody();

        if (empleadoRepository.findOne(empleado.getId()) != null) {
            return new ResponseEntity<String>("El empleado con ID " + empleado.getId() + " ya existe",
                    HttpStatus.CONFLICT);
        } else {
            return new ResponseEntity<Empleado>(empleadoRepository.save(empleado), HttpStatus.CREATED);
        }
    }

    //resto del código
}
En este caso, podríamos enviar un mensaje de error (que no iría en JSON, ya que sería solamente un String) en caso de que el empleado ya existiera. En lugar de usar la anotación @RequestBody usaríamos una instancia de la clase RequestEntity<Empleado>; y devolveríamos una instancia de ResponseEntity<?>. Como podemos observar, el constructor de esta última que hemos utilizado acepta el código de respuesta a devolver, haciendo fácil la gestión de situaciones de error.

Una mejora de esta implementación, para gestionar peticiones erróneas, sería esta última:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @PostMapping("/empleado")
    public ResponseEntity<?> createEmpleado(RequestEntity<Empleado> reqEmpleado) {

        if (reqEmpleado.getBody() == null) {
            return new ResponseEntity<ErrorRest>(new ErrorRest("Formato de petición incorrecto. Debe enviar los datos del empleado a dar de alta"),
                    HttpStatus.BAD_REQUEST);
        }

        Empleado empleado = reqEmpleado.getBody();

        if (empleadoRepository.findOne(empleado.getId()) != null) {
            return new ResponseEntity<ErrorRest>(new ErrorRest("El empleado con ID " + empleado.getId() + " ya existe"),
                    HttpStatus.CONFLICT);
        } else {
            return new ResponseEntity<Empleado>(empleadoRepository.save(empleado), HttpStatus.CREATED);
        }
    }

    //resto del código
}
¿Qué elementos han cambiado?

Comprobamos si el cuerpo de la petición tiene datos; en caso de no tenerlos, sería una petición errónea (400 Bad Request).
Tanto para el error 400, como para el 409 (Conflict), devolvemos una instancia de una clase. Es muy simple, pero nos permite que la representación que reciba el usuario sea en JSON, dando un tratamiento sistemático a la devolución de respuestas.
ErrorRest.java

public class ErrorRest {

    private String mensaje;

    public ErrorRest() { }

    public ErrorRest(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public void setMensaje(String mensaje) {
        this.mensaje = mensaje;
    }

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + ((mensaje == null) ? 0 : mensaje.hashCode());
        return result;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        ErrorRest other = (ErrorRest) obj;
        if (mensaje == null) {
            if (other.mensaje != null)
                return false;
        } else if (!mensaje.equals(other.mensaje))
            return false;
        return true;
    }
}



49.1 Actualización de recursos
Veamos, asociado a la actualización de un recurso, como sería la implementación del servicio. Recordemos primero su estructura:

URL	Método HTTP	Código de respuesta correcta	Códigos de respuesta errónea
/api/empleado/{id}	PUT	200 OK	400 Bad Request
404 Not Found
Sin entrar en disquisiciones más teóricas sobre HTTP y lo que definen los documentos RFC sobre los diferentes tipos de peticiones, nosotros vamos a tomar como determinación devolver la instancia de Empleado ya modificado.

En este caso, el código fuente necesario en el controlador sería:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @PutMapping("/empleado/{id}")
    public ResponseEntity<?> updateEmpleado(@PathVariable Long id, RequestEntity<Empleado> reqEmpleado) {

        if (reqEmpleado.getBody() == null) {
            return new ResponseEntity<ErrorRest>(new ErrorRest("Formato de petición incorrecto. Debe enviar los datos del empleado a modificar"),
                    HttpStatus.BAD_REQUEST);
        }

        if (empleadoRepository.findOne(id) != null) {
            Empleado empleado = reqEmpleado.getBody();
            Empleado aActualizar = new Empleado(id, empleado.getNombre(), empleado.getApellidos(), empleado.getFechaNacimiento());
            return new ResponseEntity<Empleado>(empleadoRepository.save(aActualizar), HttpStatus.OK);
        } else {
            return new ResponseEntity<ErrorRest>(new ErrorRest("El empleado a modificar no existe"),
                    HttpStatus.NOT_FOUND);
        }

    }

    //resto del código
}
Podemos observar que:

Por norma, desde Spring nos recomiendan que una petición PUT reciba el ID de la instancia que va a ser modificada como parte de la URL; y que dentro de la petición (en su cuerpo), reciba los datos a modificar. Por ello la firma del método es updateEmpleado(@PathVariable Long id, RequestEntity<Empleado> reqEmpleado).
Al igual que en la anterior lección, si el cuerpo de la petición viene vacío, lanzaremos un error 400 Bad Request.
Si la instancia que vamos a modificar existe en el repositorio, la modificamos, y enviamos como respuesta un código 200 OK.
En caso contrario, enviamos un mensaje de error con el código 404 Not Found.
49.2 ¿Actualización o inserción?
No queda demasiado claro, escarbando entre el RFC correspondiente, y viendo lo que la comunidad de desarrolladores implementa, si un servicio PUT debería ser capaz de crear o no una nueva instancia. Como algunos autores comentan que si, a continuación podemos ver cual sería la implementación de los métodos correspondientes:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @PutMapping("/empleado")
    public ResponseEntity<?> updateEmpleado(RequestEntity<Empleado> reqEmpleado) {

        if (reqEmpleado.getBody() == null) {
            return new ResponseEntity<ErrorRest>(new ErrorRest("Formato de petición incorrecto. Debe enviar los datos del empleado a modificar"),
                    HttpStatus.BAD_REQUEST);
        }
        Empleado empleado = reqEmpleado.getBody();
        if (empleadoRepository.findOne(empleado.getId()) != null) {         
            Empleado aActualizar = new Empleado(empleado.getId(), empleado.getNombre(), empleado.getApellidos(), empleado.getFechaNacimiento());
            return new ResponseEntity<Empleado>(empleadoRepository.save(aActualizar), HttpStatus.OK);
        } else {
            Empleado nuevoEmpleado = new Empleado(empleado.getNombre(), empleado.getApellidos(), empleado.getFechaNacimiento());
            return new ResponseEntity<Empleado>(empleadoRepository.save(nuevoEmpleado), HttpStatus.CREATED);
        }

    }

    @PutMapping("/empleado/{id}")
    public ResponseEntity<?> updateEmpleado(@PathVariable Long id, RequestEntity<Empleado> reqEmpleado) {

        if (reqEmpleado.getBody() == null) {
            return new ResponseEntity<ErrorRest>(new ErrorRest("Formato de petición incorrecto. Debe enviar los datos del empleado a modificar"),
                    HttpStatus.BAD_REQUEST);
        }

        Empleado empleado = reqEmpleado.getBody();
        if (empleadoRepository.findOne(id) != null) {
            Empleado aActualizar = new Empleado(id, empleado.getNombre(), empleado.getApellidos(), empleado.getFechaNacimiento());
            return new ResponseEntity<Empleado>(empleadoRepository.save(aActualizar), HttpStatus.OK);
        } else {
            Empleado nuevoEmpleado = new Empleado(empleado.getNombre(), empleado.getApellidos(), empleado.getFechaNacimiento());
            return new ResponseEntity<Empleado>(empleadoRepository.save(nuevoEmpleado), HttpStatus.CREATED);
        }

    }

    //resto del código
}




50.1 Borrado de recursos
Veamos, asociado a la actualización de un recurso, como sería la implementación del servicio. Recordemos primero su estructura:

URL	Método HTTP	Código de respuesta correcta	Códigos de respuesta errónea
/api/empleado/{id}	DELETE	200 OK	404 Not Found
Al igual que en la lección anterior, sin entrar en disquisiciones más teóricas sobre HTTP y lo que definen los documentos RFC sobre los diferentes tipos de peticiones, nosotros vamos a tomar como determinación devolver la instancia de Empleado ya eliminado.

En este caso, el código fuente necesario en el controlador sería:

@RestController
@RequestMapping("/api")
public class EmpleadoController {

    @Autowired
    EmpleadoRepository empleadoRepository;

    //resto del código

    @DeleteMapping("/empleado/{id}")
    public ResponseEntity<?> deleteEmpleado(@PathVariable Long id) {

        Empleado aBorrar = empleadoRepository.findOne(id);
        if (aBorrar != null) {
            empleadoRepository.delete(aBorrar);
            return new ResponseEntity<Empleado>(aBorrar, HttpStatus.OK);
        } else {
            return new ResponseEntity<ErrorRest>(new ErrorRest("El empleado a borrar no existe"),
                    HttpStatus.NOT_FOUND);
        }

    }

    //resto del código
}
50.2 Servicio completo
De esta forma, ya tendríamos nuestro servicio totalmente completo:

URL	Método HTTP	Descripción	Código de respuesta correcta
/api/empleados	GET	Obtener la lista de todos los empleados	200 OK
/api/empleado/{id}	GET	Obtener los datos del empleado {id}	200 OK
/api/empleado	POST	Crear un nuevo empleado	201 Created
/api/empleado/{id}	PUT	Modificar un empleado existente	200 OK
/api/empleado/{id}	DELETE	Eliminar un empleado existente	200 OK

51.1 Spring Data Rest
Imagina que todo lo que hemos hecho en las últimas lecciones se pudiera generar automáticamente. ¿No sería maravilloso? ¡Spring nos lo va a permitir a través de Spring Data Rest!

Spring Data Rest es en sí una aplicación Spring MVC diseñada para exponer nuestros repositorios como servicios web REST con un mínimo esfuerzo, siguiendo el principio HATEOAS (Hypermedia As The Engine Of Application State). Resumido en pocas palabras, un cliente que quisiera acceder a nuestro servicio, no necesita ningún conocimiento previo del mismo, y podrá navegar a través de hipermedia. Podríamos decir que es una forma genérica de exponer recursos a través de servicios web.

51.2 Dependencias
Para el uso de Spring Data Rest tenemos que añadir una dependencia a nuestro pom.xml

<dependencies>
  ...
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-rest</artifactId>
  </dependency>
  ...
</dependencies>
La magia de Spring Data Rest es que si usamos Spring Boot, ya no tenemos que configurar nada más para que se autogenere el servicio web; tan solo con incluir esta dependencia será suficiente. ¿No es maravilloso?

51.3 Ejemplo
A modo de ejemplo, vamos a utilizar el proyecto de una Getting Started Guide de Spring (https://github.com/spring-guides/gs-accessing-data-rest.git). También se puede importar desde Spring Tool Suite, como hemos hecho en otras ocasiones.

Si comprobamos el código fuente del mismo, no puede ser más simple:

@Entity
public class Person {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private long id;

    private String firstName;
    private String lastName;

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
}
 
@RepositoryRestResource(collectionResourceRel = "people", path = "people")
public interface PersonRepository extends PagingAndSortingRepository<Person, Long> {

    List<Person> findByLastName(@Param("name") String name);

}
La anotación @RepositoryRestResource no sería necesaria con la configuración por defecto; se añade para sobreescribir el comportamiento por defecto del componente que transforma de singular en plural, para cambiar la palabra persons por people.

Al tener añadida la dependencia de Spring Data Rest, no necesitamos implementar un controlador para tener nuestro servicio REST.

Añadimos algunos datos de ejemplo a la base de datos, de forma que el fichero Application.java queda de la siguiente forma:

@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @Bean
    CommandLineRunner init(PersonRepository personRepository) {

        String[][] data = {
                {"José", "García Martínez"}, {"Manuel", "Pérez Díaz"},
                {"Luis Miguel", "López Magaña"}, {"Alberto", "Jiménez Sarmiento"},
                {"Carlos", "Ruiz Santos"}, {"Martín", "López Alfaro"},
                {"María", "Martínez Sánchez"}, {"Luisa", "Milán Llanes"}};

        return (evt) -> Arrays.asList(data)
                .forEach(a -> {            
                        Person p = new Person();
                        p.setFirstName(a[0]);
                        p.setLastName(a[1]);
                        personRepository.save(p);                    
                });     
    }  
}
Si ejecutamos la aplicación, y nos conectamos a la URL http://localhost:8080 obtendremos la bienvenida al servicio web, en formato JSON

{
  "_links": {
    "people": {
      "href": "http://localhost:8080/people{?page,size,sort}",
      "templated": true
    },
    "profile": {
      "href": "http://localhost:8080/profile"
    }
  }
}
Dentro de _links vemos que está expueso el servicio web de personas. Nos indica además que cuando lo consultemos, podemos usar los parámetros de paginación, cantidad de resultados y ordenación.

Si accedemos a la URL http://localhost:8080/people, obtendremos como resultado:

{
  "_embedded": {
    "people": [
      {
        "firstName": "José",
        "lastName": "García Martínez",
        "_links": {
          "self": {
            "href": "http://localhost:8080/people/1"
          },
          "person": {
            "href": "http://localhost:8080/people/1"
          }
        }
      },
      ...
    ]
  },
  "_links": {
    "self": {
      "href": "http://localhost:8080/people"
    },
    "profile": {
      "href": "http://localhost:8080/profile/people"
    },
    "search": {
      "href": "http://localhost:8080/people/search"
    }
  },
  "page": {
    "size": 20,
    "totalElements": 8,
    "totalPages": 1,
    "number": 0
  }
}
Algunos resultados se han obviado para no alargar el documento.

Si accedemos al la URL search :

{
  "_links": {
    "findByLastName": {
      "href": "http://localhost:8080/people/search/findByLastName{?name}",
      "templated": true
    },
    "self": {
      "href": "http://localhost:8080/people/search"
    }
  }
}
Dentro del repositorio, hay definido un método de búsqueda. También tiene su exposición como servicio web (de forma automática).

Si realizamos algún tipo de búsqueda, por ejemplo: http://localhost:8080/people/search/findByLastName?name=García Martínez, el resultado sería:

{
  "_embedded": {
    "people": [
      {
        "firstName": "José",
        "lastName": "García Martínez",
        "_links": {
          "self": {
            "href": "http://localhost:8080/people/1"
          },
          "person": {
            "href": "http://localhost:8080/people/1"
          }
        }
      }
    ]
  },
  "_links": {
    "self": {
      "href": "http://localhost:8080/people/search/findByLastName?name=Garc%C3%ADa%20Mart%C3%ADnez"
    }
  }
}
También podemos crear nuevos recursos.

Si realizamos una petición POST, que incluya como cabecera Content-Type:application/json y como cuerpo:

{  "firstName" : "Frodo",  "lastName" : "Bolsón" }
La respuesta sería la siguiente:

{
  "firstName": "Frodo",
  "lastName": "Bolsón",
  "_links": {
    "self": {
      "href": "http://localhost:8080/people/9"
    },
    "person": {
      "href": "http://localhost:8080/people/9"
    }
  }
}
Además, como cabecera de la respuesta, también se incluye la URI del nuevo recurso.

Por último, decir que también soporta peticiones de tipo PUT (actualización total), PATCH (actualización parcial) y DELETE (borrado).



52.1 Introducción
Si alguno de vosotros viene del mundo Java EE, o ya ha hecho sus pinitos en la programación de aplicaciones empresariales Java, se habrá preguntado: ¿es que Spring no utiliza JAX-RS? Vayamos por partes.

52.2 JAX-RS (Java Api for RESTful Web Services)
JAX-RS es un api del lenguaje Java para la creación de servicios web RESTful, y está incluido de forma oficial en Java EE desde la versión 6. Actualmente está publicada la versión 2.0, que cumple con el documento JSR339. Funciona a base de anotaciones para transformar una clase Java en un recurso.

Al tratarse de un estándar, y no una implementación, existen diferentes implementaciones de terceros, entre las que destacan:

Apache CFX, implementación de Apache

RestEasy, implementación de JBoss

Jersey, siendo la implementación de referencia de Oracle y una de las más utilizadas por la comunidad de desarrolladores.
52.3 ¿Son comparables JAX-RS y Spring MVC?
Esta pregunta es clave, ya que la respuesta quizá no es la esperada. Spring MVC (incluyendo el soporte para servicios REST) no es más que un framework para el desarrollo rápido de aplicaciones web (o APIs REST), mientras que JAX-RS es todo un estándar, con diferentes implementaciones concretas. De hecho, existen gran cantidad de proyectos que utilizan Spring, incluyendo MVC, y que desarrollan los servicios web a través de JAX-RS, conjugando ambas tecnologías.

Algunos análisis comparados de una implementación con ambas tecnologías (en los que no vamos a entrar, ya que son excesivamente teóricos), arrojan que prácticamente cualquier aspecto que queramos implementar con uno de ellos, lo podremos implementar con el otro.

52.4 Entonces, ¿cuál de los dos debo usar?
No existe una respuesta clara a esta pregunta, ya que va a depender de muchos factores:

La madurez tecnológica de los desarrolladores: si nuestro equipo es joven en el uso de Spring, pero tiene madurez tecnológica en el uso de JAX-RS (por ejemplo, con Jersey), sería buena idea invertir esa madurez en un ahorro de tiempo.

Si nuestro proyecto se está desarrollando totalmente con Spring, en todos los niveles (Web, Acceso a Datos, Orientación a Aspectos, Mensajería, …), sería positivo plantearse el uso de Spring MVC para los servicios Rest.

Si queremos tener flexibilidad a la hora de cambiar la implementación concreta del motor de nuestro servicio web, entonces deberíamos plantearnos usar JAX-RS. Como hemos visto anteriormente, existen diferentes implementaciones que pueden variar en velocidad, documentación, funciones auxiliares, …

A favor de Spring, también podemos decir que tiene detrás una comunidad de desarrolladores gigantesca, una gran documentación y mucha literatura: libros, blogs, foros, etc… que podrían declinar la balanza en su favor.

54.1 Autenticación básica HTTP
Este esquema es el más simple de todos en la especificación HTTP. Se basa en pasar una combinación username:password en la cabecera Authorization. Cuando un cliente envía una petición a un servicio REST que requiere autenticación sin esta cabecera, responderá con un código 401 Not authorized.

La combinación username:password suele codificarse en Base64. Por ejemplo, para la cadena luismi:lopez, la cabecera a incluir debería ser

Authorization: Basic bHVpc21pOmxvcGV6
Para realizar pruebas, se puede usar esta web, que permite realizar las transformaciones String -> Base64
Este sistema es muy básico, y poco seguro. El usuario y contraseña no se encriptan, solo se codifican, y es fácilmente decodificable. Este esquema es solo recomendable cuando se trabaja bajo HTTPS (HTTP seguro).

54.1.1 Uso de la autenticación básica en Spring
En primer lugar, tendremos que indicar en el pom.xml que vamos a usar Spring Security:

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>
A continuación, debemos configurar la seguridad. Lo podemos hacer extendiendo la clase WebSecurityConfigurerAdapter:

@EnableWebSecurity
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication().withUser("luismi").password("lopez").roles("USER");        
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {

        http.authorizeRequests()
            .anyRequest().authenticated()
            .and().httpBasic();

    }

}
Esta configuración (excesivamente sencilla y no propicia para producción) nos ilustra el uso de Spring Security. Definimos un usuario/contraseña en memoria (luismi/lopez). Además, le indicamos a Spring que todas las peticiones de esta aplicación MVC deben ser autenticadas usando el esquema HTTP Básico.

54.2 Autenticación basada en Token
Otro esquema más utilizado a día de hoy es la autenticación basada en token. Esta no forma parte del estándar HTTP pero es un método común de autenticación.

En este esquema descansa en que el servidor necesitará, para responder convenientemente a las peticiones un token (una cadena de caracteres larga). Este token lo obtendrán los clientes autenticándose en el servicio correspondiente mediante un usuario y contraseña. El token puede tener caducidad, para que no pueda ser reutilizado eternamente si algún usuario malicioso lo consiguiera; además, puede ser encriptado con algún algoritmo de seguridad.

A día de hoy, las clases ofrecidas por Spring (Security) son muy abstractas, y necesitan de mucho código por nuestra parte para implementarlo. Spring Security queda fuera del alcance de este curso. Si alguno de vosotros quiere profundizar, os recomendamos dos de las implementaciones más modernas de autenticación usando Token:

OAuth2: Es un estándar open source de autorización que permite el acceso de aplicaciones de terceros a recursos. Es muy popular entre las aplicaciones sociales (Facebook, Twitter, …). Para más información, podemos buscar en el módulo de Spring Security OAuth.

JWT: Json Web Token es otro mecanismo simple usado para comprobar si la ifnormación enviada en las peticiones puede ser verificada y es de confianza usando una firma digital. Si queremos más información podemos acceder a https://jwt.io.




55.1 Autorización
La autorización es casi una consecuencia lógica de la autenticación. Estos dos conceptos son ofrecidos ocasionalmente de forma conjunta, pero realmente apuntan a dos requisitos diferentes de la seguridad en servicios web. La autenticación valida la identidad de los usuarios; la autorización maneja que operaciones tienen derecho a realizar los mismos. La autorización, a veces, se maneja a través de usuarios y roles, como vamos a realizar nosotros.

55.2 Autorización en Spring
Hay dos aproximaciones diferentes para implementar la autorización en Spring:

El mapeo de URLs

La anotación de recursos
Vamos a trabajar sobre ambas dos:

55.2.1 Mapeo de URLs
Basándonos en el ejemplo de la lección anterior, podemos modificar la clase Securityconfig para declarar un mapeo de URLs explícito:

@EnableWebSecurity
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {

    private final String REALMNAME = "MY_REALMNAME";

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication().withUser("luismi").password("lopez").roles("USER")
            .and().withUser("admin").password("admin").roles("ADMIN");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {

        http.csrf().disable()
            .authorizeRequests()
            .antMatchers(HttpMethod.GET,"/api/hello").hasRole("USER")
            .antMatchers(HttpMethod.GET,"/api/admin/hello").hasRole("ADMIN")
            .antMatchers(HttpMethod.POST,"/api/admin/hello").hasRole("ADMIN")
            .and().httpBasic();

    }

}
Con esta nueva versión, solamente los usuarios con rol ADMIN pueden acceder al recurso situado en /api/admin/hello.

Para tener usuarios con rol ADMIN, hemos añadido uno nuevo, con las credenciales “admin/admin”.

55.2.2 Anotaciones de recursos
Por contra de una configuración centralidad, como la del apartado anterior, podemos usar anotaciones para controlar el acceso a los diferentes recursos directamente sobre las clases. Para ello, hacemos uso de la anotación org.springframework.security.access.prepost.PreAuthorize.

Veamos un ejemplo:

@RestController
@RequestMapping("api")
public class SampleController {

    @PreAuthorize("hasAnyRole('ADMIN','USER')")
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello World!";
    }

    @PreAuthorize("hasRole('ADMIN')")
    @GetMapping("/admin/hello")
    public String sayHelloForAdmins() {
        return "Hello World, Mr. Admin";
    }

    @PreAuthorize("hasRole('ADMIN')")
    @PostMapping("/admin/hello")
    public String submitGreet(@RequestBody String greet) {
        return "The recieved greet is " + greet;
    }

}
De esta forma, podemos dar una configuración particular a cada recurso. Para poder usar la anotación @PreAuthorize(...) tenemos que incluir alguna modificación en nuestro fichero de configuración:

@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {


    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication().withUser("luismi").password("lopez").roles("USER")
            .and().withUser("admin").password("admin").roles("ADMIN");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {


        http.csrf().disable()
            .authorizeRequests()
            .anyRequest().authenticated()
            .and()
            .httpBasic();


    }

}
Destaca, sobre todo, el uso de la anotación @EnableGlobalMethodSecurity(prePostEnabled = true), que nos permitirá gestionar la autorización a través de anotaciones.


56.1 Introducción
Hasta ahora hemos venido desarrollando la parte servidora de los servicios web. Spring nos ofrece también los elementos necesarios para construir un cliente rest, a través de la clase RestTemplate.

56.2 RestTemplate
Esta clase, que en principio puede resultar hasta mágica, nos va a permitir, en la mayoría de las ocasiones en una sola línea de código:

Conectar con una URL

Enviarle una petición con un determinado método HTTP

Además, si fuera necesario, incluir determinadas cabeceras en dicha petición

Recoger la respuesta que ofrezca el servicio Web

Procesar la misma para obtener, si fuera necesario, un objeto de nuestro modelo.
Método HTTP	Método RestTemplate
DELETE	delete(java.lang.String, java.lang.Object...)
GET	getForObject(java.lang.String, java.lang.Class<T>, java.lang.Object...)
getForEntity(java.lang.String, java.lang.Class<T>, java.lang.Object...)
HEAD	headForHeaders(java.lang.String, java.lang.Object...)
OPTIONS	optionsForAllow(java.lang.String, java.lang.Object...)
POST	postForLocation(java.lang.String, java.lang.Object, java.lang.Object...)
postForObject(java.lang.String, java.lang.Object, java.lang.Class<T>, java.lang.Object...)
PUT	put(java.lang.String, java.lang.Object, java.lang.Object...)
cualquiera	exchange(java.lang.String, org.springframework.http.HttpMethod, org.springframework.http.HttpEntity<?>, java.lang.Class<T>, java.lang.Object...)
execute(java.lang.String, org.springframework.http.HttpMethod, org.springframework.web.client.RequestCallback, org.springframework.web.client.ResponseExtractor<T>, java.lang.Object...)
Para mejor consulta de los métodos disponibles, podemos profundizar viendo su JavaDoc

56.3 Ejemplo de uso de RestTemplate
Para ejemplificar su uso, vamos a implementar una aplicación capaz de consultar el servicio web https://restcountries.eu/rest/v1/all, que nos devolverá un listado con todos los paises del mundo y una gran cantidad de información más sobre ellos (entre otros, su codificación oficial ISO-3166).

Si vemos la estructura de un solo pais en JSON:

 {
        "name": "Spain",
        "topLevelDomain": [
            ".es"
        ],
        "alpha2Code": "ES",
        "alpha3Code": "ESP",
        "callingCodes": [
            "34"
        ],
        "capital": "Madrid",
        "altSpellings": [
            "ES",
            "Kingdom of Spain",
            "Reino de España"
        ],
        "relevance": "2",
        "region": "Europe",
        "subregion": "Southern Europe",
        "translations": {
            "de": "Spanien",
            "es": "España",
            "fr": "Espagne",
            "ja": "スペイン",
            "it": "Spagna"
        },
        "population": 46439864,
        "latlng": [
            40,
            -4
        ],
        "demonym": "Spanish",
        "area": 505992,
        "gini": 34.7,
        "timezones": [
            "UTC",
            "UTC+01:00"
        ],
        "borders": [
            "AND",
            "FRA",
            "GIB",
            "PRT",
            "MAR"
        ],
        "nativeName": "España",
        "numericCode": "724",
        "currencies": [
            "EUR"
        ],
        "languages": [
            "es"
        ]
    }
OMG! ¿Cómo trasladar todo esto a clases POJO Java? La respuesta es fácil: podemos usar el servicio http://www.jsonschema2pojo.org/, que recibe un fragmento de JSON, y nos devuelve las clases Java necesarias para modelarlo.

Si queremos realizar la petición de estos datos, y visualizarlos en una tabla, necesitaríamos un controlador como el siguiente:

import javax.net.ssl.HttpsURLConnection;
import javax.net.ssl.SSLContext;
import javax.net.ssl.TrustManager;
import javax.net.ssl.X509TrustManager;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.client.RestTemplate;

@Controller
public class MyRestClientController {

    final String urlList = "https://restcountries.eu/rest/v1/all";

    @GetMapping("/list")
    public String listCountries(Model model) {

        enableSSL();

        RestTemplate restTemplate = new RestTemplate();

        Country[] lista = restTemplate.getForObject(urlList, Country[].class);

        model.addAttribute("lista", lista);

        return "list";
    }


    private void enableSSL() {
        TrustManager[] trustAllCerts = new TrustManager[]{
            new X509TrustManager() {
                public java.security.cert.X509Certificate[] getAcceptedIssuers() {
                    return null;
                }

                public void checkClientTrusted(
                        java.security.cert.X509Certificate[] certs, String authType) {
                }

                public void checkServerTrusted(
                        java.security.cert.X509Certificate[] certs, String authType) {
                }
            }
        };

        try {
            SSLContext sc = SSLContext.getInstance("SSL");
            sc.init(null, trustAllCerts, new java.security.SecureRandom());
            HttpsURLConnection.setDefaultSSLSocketFactory(sc.getSocketFactory());
        } catch (Exception e) {
        }
    }

}
El método enableSSL es un método auxiliar, que hemos desarrollado para poder conectarnos a un servicio https sin tener que instalar su certificado. De todo el código, la linea interesante es:

    Country[] lista = restTemplate.getForObject(urlList, Country[].class);
Usando RestTemplate, obtenemos de una url un objeto de tipo Country[], es decir, un array con todos los países. Pasamos este array con el modelo a la vista, que sería como sigue:

<%@ page language="java" contentType="text/html; charset=utf-8"
    pageEncoding="utf-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>

    <!-- Resto del código -->

    <div class="container">
        <div class="row">
            <table
                class="table table-bordered table-striped table-hover table-condensed table-responsive">
                <thead>
                    <tr>
                        <th>Código Alfa 2</th>
                        <th>Código Alfa 3</th>
                        <th>Nombre</th>
                        <th>Capital</th>
                        <th>Bandera</th>
                    </tr>
                </thead>
                <tbody>
                    <c:forEach items="${lista}" var="pais">
                        <tr>
                            <td>${pais.alpha2Code}</td>
                            <td>${pais.alpha3Code}</td>
                            <td>${pais.name}</td>
                            <td>${pais.capital}</td>
                            <td><img src="https://github.com/adamoliver/Country-Flags-ISO-3/blob/master/gif/${fn:toLowerCase(pais.alpha3Code)}.gif?raw=true" /></td>
                        </tr>
                    </c:forEach>
                </tbody>
            </table>

        </div>
    </div>

    <!-- Resto del código -->
Aprovechando que otro usuario de github, adamoliver, pone a nuestra disposición las bandera de cada pais con su código Alfa 3, podemos pintarlas también en nuestra tabla.


57.1 Introducción
En las lecciones 53, 54 y 55 hablamos sobre seguridad en servicios web con Spring. Vamos ahora a tratar de implementar una de las soluciones propuestas, para acceder desde un cliente a un servicio web securizado con Http Basic.

57.2 Accediendo con seguridad
La clae RestTemplate que hemos usado en la lección anterior, nos permite implementar la seguridad Http Basic de una forma sencilla: añadiendo la cabecera de autorización con la cadena username:password codificada en base 64.

Si queremos enviar una petición http con unas cabeceras en particular, podemos hacer uso del método RestTemplate.exchange(), que entre otros parámetros, recibe un org.springframework.http.HttpHeaders. Dentro de este último, podemos añadir la cadena de autenticación. Si vemos el siguiente código:

    @SuppressWarnings("serial")
    private HttpHeaders createHeaders(String username, String password) {
        return new HttpHeaders() {
            {
                String auth = username + ":" + password;
                byte[] encodedAuth = Base64.encodeBase64(auth.getBytes(Charset.forName("UTF-8")));
                String authHeader = "Basic " + new String(encodedAuth);
                set("Authorization", authHeader);
            }
        };
    }
Como vemos, nos sirve de método auxiliar, para generar el objeto HttpHeaders con un usuario y contraseña que le proporcionemos. Codificamos en Base64 mediante la clase org.apache.tomcat.util.codec.binary.Base64.

Para realizar la petición, el código sería:

    @GetMapping("/admin")
    public String adminHello(Model model) {

        RestTemplate restTemplate = new RestTemplate();

        ResponseEntity<?> response = restTemplate.exchange(urlAdminHello, HttpMethod.GET,
                new HttpEntity<String>(createHeaders("admin", "admin")), String.class);

        model.addAttribute("saludo", response.getBody());

        return "adminhello";
    }
De esta manera, enviarmos una petición GET, enviando las cabeceras de autorización correctas, para recibir así la respuesta (en este caso, una cadena de caracteres).





















 https://github.com/OpenWebinarsNet/curso_java_mvc


