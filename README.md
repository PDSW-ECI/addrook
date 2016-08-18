##Escuela Colombiana de Ingeniería

###Procesos de Desarrollo de Software - PDSW
####Ejercicio - Patrones estructurales

JDBC es un API de Java que permite que las aplicaciones Java interactúen con bases de datos SQL. La siguiente figura muestra los componentes de dicho API:

![](http://docstore.mik.ua/orelly/linux/sql/figs/MSQL.1401.gif)

Donde para este ejercicio son de resaltar: 

* [Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html): abstrae una conexión a la base de datos.
* [Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html): representa una sentencia SQL básica.
* [PreparedStatement](http://docs.oracle.com/javase/7/docs/api/java/sql/PreparedStatement.html): representa una sentencia SQL precompilada.

El siguiente, es un ejemplo de cómo con un objeto Connection se puede crear un nuevo PreparedStatement, y cómo con este último se envía una sentencia INSERT al motor de base de datos:

```SQL
PreparedStateement ps= connection.prepareStatement(
              "INSERT INTO TABLE" +
              "VALUES(12,332,44)");
ps.execute();
```

En este repositorio se tienen los fuentes de una libreta electrónica, la cual hace uso de una base de datos embebida SQLite para hacer la persistencia de los datos. Para ejecutarla:

```bash
mvn exec:java -Dexec.mainClass="org.mhaidarh.addressbook.view.AddrookSimpleDBApp"
```

Esta aplicación tiene un problema: la persistencia de esta aplicación (clases Person/PersonQueries) es provista por una librería externa (revise el archivo pom.xml), de manera que no se conoce a ciencia qué sentencias SQL se están generando (lo que algunas veces dificulta la identificación de errores).

###Ejercicio

Se necesita identificar las sentencias SQL que está generando la aplicación, sin que esto afecte la funcionalidad de la misma. 

1. Identifique... qué patrón estructural es aplicable en este caso?
2. De acuerdo con patrón elegido, qué clases del diagrama anterior se usarían, y que rol cumplirían.
3. Haga la implementación del patrón, de manera que cada vez que se ejecute la aplicación, se genere un archivo de LOGs (de texto) en donde quede registro de las sentencias generados durante el uso de la misma.


