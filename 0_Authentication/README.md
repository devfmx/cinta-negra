# Autenticación

## Basic Authentication

* Sistema simple de autenticación para el protocolo HTTP.
  
* El Cliente  envía una petición HTTP con la cabecera **“Authorization”** y esta contiene la palabra **“Basic”** seguida por un espacio  y  en un string  “username:password” en formato de **base64**.
   
* Por Ejemplo, Para autorizar al usuario **“demo”** se usaria **demo:p@55w0rd** a travez de **base64**.  El resultado seria la siguiente cabecera: Authorization: Basic ZGVtbzpwQDU1dzByZA==.
  
* base64 es fácil de decodificar, Por lo tanto _Basic authentication_ debería usarse junto con otros protocolos de seguridad como HTTPS/SSL. 

![Basic Auth](https://chathurangat.files.wordpress.com/2017/08/blog-post-spring-security-basic-authentication-1.png?w=1108)

## OAUTH2

* Es un framework de autorización que le permite a las aplicaciones obtener acceso limitado a cuentas de usuario en un servicio HTTP (Facebook,Google,Github,etc)

* Delega la autenticación del usuario al servicio y autoriza a aplicaciones de terceros el acceso a dicha cuenta de usuario.

* Cuenta con 4 Roles:
  * **Propietario del recurso**: Es el "usuario" que da la autorización a una aplicación, para acceder a su cuenta. 
  
  * **Cliente**: Es la aplicación que desea acceder a la cuenta del usuario.
  
  * **Servidor de recursos**: Servidor que autentifica al cliente y regresa token de acceso .
  
  * **Servidor de autorización**: Servidor  que regresa los recursos solicitados al cliente.

**Oauth2 Generico** 

![Oauth2 generico](https://assets.digitalocean.com/articles/translateddiagrams32918/Abstract-Protocol-Flow-Spanish@2x.png)

**Ejemplo: Dropbox Auth**

![Oauth2 dropbox](https://www.dropbox.com/static/images/developers/oauth2-web-diagram.png)

## JWT (Json Web Tokens)

* Estándar abierto (RFC-7519) basado en JSON para crear un token que sirva para enviar datos entre aplicaciones o servicios y garantizar que sean válidos y seguros.
  
* JWT es muy usado  para manejar la autenticación en aplicaciones móviles o web.

* Se compone  de tres partes  **header, payload y signature** los cuales son **objetos json** que se convierten en string a travez de hash de **base64**. Estos hashes se concatenan con un punto  teneindo la siguiente estructura:  

> header.payload.signature

* Ejemplo de JWT
  
  ```
  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjEiLCJ1c2VybmFtZSI6InNlcmdpb2R4YSJ9.Qu7rv5wqk6zGjiMU8ZixwvKQGBNW9hhj55DbSP50b1g

**Header**: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9

**Payload**: eyJpZCI6IjEiLCJ1c2VybmFtZSI6InNlcmdpb2R4YSJ9

**Signature**: Qu7rv5wqk6zGjiMU8ZixwvKQGBNW9hhj55DbSP50b1g


![JWT Example](https://artsy.github.io/images/2016-10-26-jwt-artsy-journey/jwt-example.png)

### JWT - Header


Json con Metadata del JWT  el cual especifica el tipo de token y algoritmo de encriptación.

* Tipo de token (typ) - Identifica el tipo de token. (siempre debe ser JWT).

* Algoritmo de firmado (alg) - Indica que tipo de algoritmo fue usado para firmar el token.

### JWT - Payload


Json  que puede llevar cualquier tipo de dato, por lo regular se ocupa para mandar datos de la sesión como: email,id,username. Además aquí se agregan otras reglas como la expiración del token.
Algunas reglas son :

* Creador (iss) - Identifica a quien creo el JWT

* Razón (sub) - Identifica la razón del JWT, se puede usar para limitar su uso a ciertos casos.

* Tiempo de expiración (exp) - Una fecha que sirva para verificar si el JWT está vencido y obligar al usuario a volver a autenticarse.

* No antes (nbf) - Indica desde qué momento se va a empezar a aceptar un JWT.

* Creado (iat) - Indica cuando fue creado el JWT.

### JWT - Signature


La firma del JWT se genera usando el header y el payload en base64,este nuevo string es encriptado con una llave secreta unica guardada en el backend. El Siganture es el que da validez al token en el backend.


### JWT - Request

![JWT Request Example](http://sivatechlab.com/wp-content/uploads/2017/09/jwt-get-customer.png)

El token debe ser intercambiado enel backend por un usuario y una contraseña a travez de una petición **POST**.

Para hacer uso del token el cliente debe enviar este en la **cabecera _Authorization_** del request que vaya a realizar al servidor.

El contenido de esta cabecera debe tener un prefijo que típicamente es **Bearer** o **JWT** seguida de un espacio en blanco entre el prefijo y el token. 


## Otras Formas de Autenticación


**API Keys**: 
Se generan dos diferentes keys o llaves una privada y una pública, ambas son dependientes (No se puede utilizar una sin la otra), Por seguridad la llave pública debe ser usada  en el frontend y la llave privada en el backend, además estas llaves son asociadas a un solo usuario de manera permanente.

![API KEYS](https://ssd.eff.org/files/2018/05/14/16_0.png)

**API Token**:
Se genera un token de caracteres aleatorios y es asociado de manera permanente a un usuario. Este  token no caduca y sirve para identificar el usuario que hace uso de la API.



**HMAC**:
Conocido como “hash-based message authentication code”   se envía una versión en hash del password y otros elementos de autenticación al servidor,este recibe varias partes y recompone el password y así dar acceso al usuario.

![HMAC](https://fiverr-res.cloudinary.com/images/t_main1,q_auto,f_auto/gigs/111936087/original/0db8df30be67c18b629bdfb02ab8c683c477893f/implement-hmac-authentication-in-your-web-api-2.jpg)


## Fuentes

[Oauth2 Digital Ocean](https://www.digitalocean.com/community/tutorials/una-introduccion-a-oauth-2-es)

[Oauth2 Simplified](https://aaronparecki.com/oauth-2-simplified/)

[JWT Introduction](https://jwt.io/introduction/)

[Common Methos Auth](https://nordicapis.com/3-common-methods-api-authentication-explained/)















