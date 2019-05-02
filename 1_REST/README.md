# REST API


## Conceptos Básicos

* **TCP/IP:** Transfer control protocol/Internet Protocol
* **REST:** Representational State Transfer
* **API:** Application Programming Interface
* **HTTP:**  Se encarga de la comunicación entre un servidor web y un navegador web. HTTP se utiliza para enviar las peticiones de un cliente web (navegador) a un servidor web, volviendo contenido web (páginas web) desde el servidor al cliente.
* **HTTPS:** Lo mismo pero más seguro. La información viaja de manera segura y encriptada mediante un certificado SSL/TLS

## ¿Qué es?

Es una arquitectura para envio de información a travez  de estados representados en rutas en el servidor. Todos los servicios rest cuentan con las siguinetes caracteristicas.

* Esta asociados a información.
* Permiten listar, crear, leer, actualizar y borrar información.
* Para las operaciones anteriores necesitan una URL y un método HTTP para accederlas.
* Usualmente regresan la información en formato JSON.
* Retornan códigos de respuesta HTTP, por ejemplo 200, 201, 404, etc.
  
## Modelo HTTP

![Modelo HTTP](https://drive.google.com/uc?export=download&id=14R3j2oQME6zMwHX-GsG84JLt7bm3cL2S)

## Otros Protocolos

* **FTP:** File transfer protocol, como su nombre lo indica es un protocolo para transferencia de archivos.
*  **SMTP:** Simple Mail Transfer Protocol
* **IMAP:** Internet Message Access Protocol
* **POP:** Post Office Protocol
* **SSL:** Secure Sockets Layer
* **TLS:** Transport Layer Security

## Verbos HTTP

* **GET:** Verbo exclusivo para obtener recursos del servidor.
*  **POST:** Verbo exclusivo para crear nuevos recursos en el servidor.
*  **PUT:** Verbo reemplaza un recurso por completo en el servidor.
*  **PATCH:** Verbo que modifica parcialmente el el recurso.
*  **DELETE:** Verbo que elimina física o lógicamente el recurso.

## REST - Reglas

### Independiente del Formato

Todas las rutas de REST no deben terminar en ningun tipo de formato ya se HTLM,JS,JSON, etc.

#### Ejemplos

**Formato incorrecto**

```
/contacto/tarea.json
```

**Formato Correcto**

```
/contacto/tarea
```

### Mantienen Jerarquia Lógica

Todas las rutas de rest tienen que tener una jerarquia lógica la cual debe ir de lo general a lo particular.

#### Ejemplos

**Formato incorrecto**

```
/tarea/4/contactos/2
```

**Formato Correcto**

```
/contactos/2/tareas/4
```

### Filtrado,Paginación y otras operaciónes

Una REST API tiene que tener opciones de poder filtrar datos o tener paginación en dado caso de que los registros en la  base de datos sean demasiados, además estos elememtos se tiene que agregar a la ruta como **Query Parameters** y no como parte de la ruta.

#### Ejemplos

**Formato incorrecto**

```
/tareas/fecha-desde/2007/pagina/3
```

**Formato Correcto**

```
/tareas?fecha-desde=2007&pagina=3
```

## REST - CRUD

Todas las operaciones de una API REST depende del recurso que se quiere ocupar en este caso el recurso es escrito en la ruta y del verbo HTTP correspondiente.

### Ejemplo

![Ejemplo CRUD](https://img.colabug.com/2018/11/050c7aadecbecb20edcd68d3d1196862.png)



## REST - Status Codes

Toda peticion hacia una REST API debe contener un código de HTTP corespondiente al resultado de la operación.

* **Nivel 2xx** : Las operaciones realizadas fueron exitosas.
* **Nivel 3xx**: Son operaciones de redirección o cache.
*  **Nivel 4xx**: Las operaciones que realizo el clientes son incorrectas o hay un problema con el cliente.
*  **Nivel 5xx**: Las operaciones en el servidor resultarón mal o hubo un problema con el servidor.

### Ejemplos

![Códigos Comunes](https://codeteddycom.files.wordpress.com/2017/06/statuscode.png?w=1109)

Para mas códigos visita [HTTP Cat 😺](https://http.cat)

## REST - Mejores Practicas

* REST siempre debe enviar y aceptar  **JSON**  como  **Content-Type**
* Usa sustantivos en la rutas en vez de verbos
  * Ejemplos
    * Si  **/employees/2323423**
    * No **/getOneEmployee**
* Usa sustantivos en **plural** en vez de **singular**.
  * Ejemplos
    * Si **/cars**
    * No **/car**

* Utiliza sub-resources para relaciones
  * Ejemplo:
    * **/employees/711/addresses**  #Obtinen todas las direcciones del empleado 711
    * **/employees/711/addresses/2** #Obtinen la dirección 2 del empleado 711
* Siempre utiliza el Header Content-Type  para especificar  el tipo de contenido del request y response.
* Usa **HATEOAS**   Conocidas como Hypermedia as the Engine of Application State, hace mas facil la navegación de la api.
  *  Ejemplo:
  *  ![Ejemplo HATEOAS](https://drive.google.com/uc?export=download&id=1y4m8X4THkPRK9vPRCtUY2yW7P_Hd2z9d)

* Provee Filtrado,Sorting, Field Selection y Pagination para las colecciones.
* Versiona tu API.
* Usa Status Codes de HTTP para capturar errores.
* Usa mensajes de error descriptivos.















