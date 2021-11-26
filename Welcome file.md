# Java Fxml && h2 con ECLIPSE IDE
## INSTALAR PLUGIN H2 Hydrogen ECLIPSE
1 Instalar un plugin: 
`Help>Eclipse MarketPlace
escribir h2 e instalar Hydrogen 1.0.1`
![Hydrogen Icom](https://marketplace.eclipse.org/sites/default/files/styles/ds_medium/public/default_images/default_2.png)
https://marketplace.eclipse.org/content/hydrogen
(si no aparece hacer click abajo en "Browse for more solutions y buscar en la ventana emergente") 

## Instalar el Software proveniente de h2

    Help>Insatall New Software 

![enter image description here](https://huongdanjava.com/wp-content/uploads/2021/08/install-glassfish-server-in-eclipse-1.png)
Pegar el siguiente enlace donde aparezca 

**Name por defecto**`(el que aparezca)`
**Location:**`https://ci.eclipse.org/datatools/job/org.eclipse.datatools_master/lastSuccessfulBuild/artifact/site/target/repository/` 

https://ci.eclipse.org/datatools/job/org.eclipse.datatools_master/lastSuccessfulBuild/artifact/site/target/repository/
Aceptar , seleccionar TODAS LAS OPCIONES e instalar.

## Configurar h2

    Window>Perspective>Open Perspective>Others>Database Development
En el panel de la izquierda **Data Source Explorer** se nos abrirá un apartado llamado **Database Connections**
Database Connections(right-click)>New...>Select Generic JDBC...(next)>Add new driver(arriba-combobox derecha)>(seleccionar el por defecto y cambiar nombre a "h2 driver")>
Pestaña de jar list> Seleccionar el h2 jar o el zip

Pestaña de properties> 
<a href="https://imgbb.com/"><img src="https://i.ibb.co/NNGNMbx/image.png" alt="image" border="0"></a>
**CORREGIR DRIVER POR org.h2.Driver**

## Creacion de una base de datos de ejemplo
Con el paso anterior se creo una conexion a una base de datos por ello podremos empezar a crear las tablas por codigo java.
Para hacerlo compatible con javafx es necesario realizar los siguiente pasos
[si se quiere hacer en un maven normal se ha de configurar el pom con ]

    <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <version>1.4.200</version>
    </dependency>
            
  Al crear database1 en el paso anterior y hacer click en Test Connection no deberia de dar error.

## Abriendo un proyecto javafx existente 
Descargar del repositorio de github el proyecto whiteProjectFx o similar....
Entrar en eclipse File>Open Project From File System> Directory >"seleccionar carpeta de proyecto">abrir

Se abriran dos veces uno con una pequeña jota de icono o con el nombre duplicado(el que nos interesa)
<a href="https://imgbb.com/"><img src="https://i.ibb.co/FqzXJGS/image.png" alt="image" border="0"></a>
Esperamos a que se descargue todo (abajo a la derecha aparece el proceso)
Añadirmos la dependencia al pom
<a href="https://ibb.co/9Y7Rv40"><img src="https://i.ibb.co/ZT0yJgr/image.png" alt="image" border="0"></a>
ABRIMOS LA CLASE **HelloAplication.java**
**EJECUTAR**
## Ejecución
Crear una tabla aprovechando el código
En la clase HelloController.java
Dentro del metodo OnHelloButtonClick();
podemos colocar este script de ejemplo

     try(Connection conexionDataBase = DriverManager.getConnection("jdbc:h2:~/database1", "root","")){
        Statement statement = conexionDataBase.createStatement();
        String sql = "CREATE TABLE IF NOT EXISTS games"+
                "(id INTEGER auto_increment,"+
                "nombre VARCHAR(255),"+
                "desarrollador VARCHAR(255),"+
                "descripcion VARCHAR(255),"+
                "valoracion VARCHAR(255),"+
                "plataforma VARCHAR(255),"+
                "pegi VARCHAR(255))";
        System.out.println("TABLA CREADA");
    }catch (Exception e) {
    	System.out.println("LA CREACION DE LA TABLA DE DATOS HA FALLADO");
	}

Window>Open Perspective...Database Development...

Hacer click derecho y **desconectar** base de datos antes de ejecutar
**Ejecutar** y comprobar que funciona

**Si no se pueden importar las Clases o metodos relacionados con sql revisad que el module info aparece la linea requires java.sql;**

<a href="https://ibb.co/wM3pHv1"><img src="https://i.ibb.co/Lnb9wGf/image.png" alt="image" border="0"></a>
 **ERROR AÑADIR         statement.executeUpdate(sql); una linea antes de TABLA CREADA...**
EJECUCIÓN

<a href="https://ibb.co/qdXBdBH"><img src="https://i.ibb.co/Y3Y2325/image.png" alt="image" border="0"></a>

PARA VER LAS TABLAS HAY QUE RECONECTAR LA BASE DE DATOS CON EL CLICK DERECHO


https://github.com/JmJDrWrk/Eclipse-JavaFx-Tutorial/blob/main/Captura.PNG

# FIN

😂 COLABORACIÓN 😂
https://github.com/Tito82 -- Titolas

Jésus

El tío de delante
...


# PARA EMPEZAR UN NUEVO PROYECTO
## Plugin e(fx)clipse
Instalar desde el marketplace como el primer plugin
## Descargar la version de javafx para nuestro OS 
Descargar desde este enlace en formato SDK
https://gluonhq.com/products/javafx/

## Creamos un proyecto de javafx 
New>Project>Java Fx Project
<a href="https://imgbb.com/"><img src="https://i.ibb.co/NWLpsnz/image.png" alt="image" border="0"></a> 


-- Click derecho > Build Path > Modules > Add External jar (Seleccionar todos los jar de la carpeta bin del java fx)

<a href="https://ibb.co/j4g8T7f"><img src="https://i.ibb.co/f04X2mF/image.png" alt="image" border="0"></a>
<a href="https://ibb.co/fCtCq0t"><img src="https://i.ibb.co/SK0K5v0/image.png" alt="image" border="0"></a>
y Ejecutar
