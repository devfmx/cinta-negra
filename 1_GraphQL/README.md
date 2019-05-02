# GRAPHQL

## ¿Qué es ?

* GraphQL es a data query language and runtime para enviar y solicitar data a Mobile apps y Web apps desde 2012. 

* Es una arquitectura que se basa en definición de Tipos y Atributos (cada operación debe tener un tipo y atributos)


* A Diferencia de REST, GraphQL necesita de Clientes Especiales


* Tiene diferentes operaciones  llamadas  **Query** (Read)  y **Mutation** (Create,Update y Delete)

* Solo utiliza método **POST** para realizar cualquier operación.

* Fue creado por Facebook y liberado en 2015.


## Ventajas

* Tiene una forma declarativa de obtener data.

* Se envía solo la información que se necesita.

* Una única  fuente de la verdad.

* Amigable con Frameworks y Lenguajes.

* Auto Documentación.

* No necesita versionamiento.

* Fuertemente Tipado.

* Un comunidad creciendo día con día.


## ¿Quiénes lo usan?

* **Facebook:** [Graph API](https://developers.facebook.com/docs/graph-api/)

* **GitHub:** [Github API v4](https://developer.github.com/v4/)
  
* **New York Times:** [React and GraphQL at the NYTimes](https://softwareengineeringdaily.com/2018/10/22/react-and-graphql-at-the-nytimes/)

* **Coursera:** [Coursera's GraphQL API Evolution](https://www.graphql.com/articles/coursera-graphql)

* **Yelp:** [Yelp GraphQL API](https://www.yelp.com/developers/graphql/guides/intro)

## Problemas que resuelve

### Problema Nº 1: Varias peticiones en un solo viaje.

 En REST cuando se envia a un recurso con relaciones (One To One, One To Many, Many To Many), Las relaciones en el JSON son representadas por el ID del recurso haciendo que sea necesario hacer otra petición para obtener información del recurso relacionado, esto se vuelve un problema cuando son muchos recursos relacionados a los que se tiene que acceder para dar más detalle en el cliente.

![Some Trips in a row](https://drive.google.com/uc?export=download&id=19w_aMLwV-fzlxguoz23dSA1dsllKskBr)

**Posible Solución:** Crear un endpoint */newsfeed/* 

### Problema Nº 2: Data innecesaria

Si tenemos una aplicación de un blog donde tenemos un atributo llamado “views_count”  que en una nueva version vamos a quitar de la aplicacion, pero debemos seguir  soportando las viejas versiones de la aplicación , entonces la nuevas versiones no aceptan views_count, pero las viejas versiones Si. Al quitar de la api el campo "views_count", las viejas aplicaciones tendran problemas y si dejamos el campo es data innecesaria que hace mas pesado nuestro JSON.

![Ejemplo nuevas versiones](https://drive.google.com/uc?export=download&id=1jVmLvo2yysicY6QRp7OJq5FKBJduvAN_)

#### Problemas

* Quitar **views_count**  de newsfeed/ no es una opción

* Viejas versiones no podrían funcionar si retiramos **views_count**
#NullPointException

* Las nuevas versiones no necesitan **views_count**, pero la viejas versiones si por lo tanto newsfeed/ sigue mandando **views_count.**

* **Posible Solución:** Crear un endpoint que pueda recibir por query parameter qué campos se deben enviar

### Problema 3: Documentar una REST API puede volverse un problema.

Muchas veces documentar una API, se vuelve todo un problema, ya que necesitas librerias  para  poder generar documentación automatizada. Aparte es muy difícil hacer que los primeros acercamientos con la API por parte de los clientes se de una manera orgánica, en cocaciones termina siendo frustrante para los desarrolladores y para los clientes.


* ¿Comó permites a otros explorar la api?
* Como hacer una documentación entendible y fácil para los clientes.
* Se vuelve un problema cuando la comunidad no sabe ocupar la api y puede producir errores.


## REST vs GRAPHQL

Comparativa entre una peticion **REST** y una peticion de  **GraphQL**.

![REST vs GRPAHQL](https://s3.us-east-2.amazonaws.com/andrewmcburney-blog-images/multiple_requests.png)

## GRAPHQL - CRUD - QUERY

Los **Query** son utilizados para obtener recursos ya sea de forma de objetos o en forma de colleciones.

**Estructura:**
![query estructura](https://cdn-images-1.medium.com/max/1600/1*yI_ZuOy0-22q6pdgVlytCA.png)

Ejemplos:

**Github Example**
![Github Example Request](https://andela.com/wp-content/uploads/2017/08/new.png)


**Ejemplo simple**
![Ejemplo simple](https://www.oreilly.com/library/view/learning-graphql/9781492030706/assets/lgql_0101.png)


## GRAPHQL - CRUD - MUTATION

Se ocupan para crear, modificar y borrar recursos, son muy similares a los query, pero con la diferencia de que es necesario enviar parámetros para poder realizar una operación.

Ejemplos:

**Creando un articulo**
![](https://www.amazeelabs.com/sites/default/files/inline-images/violation.png)

**Modificando un articulo**
![](https://www.amazeelabs.com/sites/default/files/inline-images/update-article.png)

**Eliminando un articulo**
![](https://www.amazeelabs.com/sites/default/files/inline-images/delete-article.png)

## GRPAHQL - SUBSCRIPTIONS 

Las subscripciones en GraphQL son eventos en tiempo real que se ejecutan cuando un recurso es creado, borrado o modíficado.

![GraphQL Subscription](https://cdn-images-1.medium.com/max/1600/1*kuYILfooxacG-wq9gWZteQ.png)

## Clientes 

### Apollo 
![](https://novemberfive.co/images/2018/07/12/001-001%20-%20visual%20@2x-1.png)

### Relay(React)
![](https://i0.wp.com/softwareengineeringdaily.com/wp-content/uploads/2015/09/relay-architecture-copy1.png?resize=720%2C315&ssl=1)

## Links 

* [Documentación de  GRPAHQL](http://graphql.org/)
* [Medium](https://medium.com/search?q=graphql)
* [Repo oficial de GRPAHQL](https://github.com/facebook/graphql)
* [Documentacion de Apollo](https://www.apollodata.com/)
* [Introducción a GRPAHQL](https://github.com/mugli/learning-graphql)
* [GraphCOOL](https://goo.gl/nJC9xv)
* [ORM con GraphQL (Prisma.io)](https://www.prisma.io/)
* [HOW TO GRAPHQL](https://www.howtographql.com/)














