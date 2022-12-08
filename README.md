## Proyecto de Rutas Protegidas

Usamos una API Segura para  nuestros usuarios, encriptando contraseñas y manejando sesiones con rutas protegidas

Usamos la siguientes librerías y/o dependencias:

1. bcrypt
2. passport
3. jsonwebtoken
4. passport-jwt


En la carpeta src se tiene una carpeta auth con los siguientes 3 archivos:
   - auth.controller.js:
    Agrega una funcion que verifica las credenciales del usuario, recibiendo solo el email y la contraseña, retornar el usuario en caso de ser exitoso, o null en caso de que no

   - auth.services.js:
    Maneja el servicio del login y ejecutar el controlador. En caso de ser exitoso  crea un token que almacena el id, el email y el rol del usuario

   - auth.router.js: 
   Manejar la peticion de tipo post a /login con el servicio

Creamos un middleware para proteger rutas usando una archivo auth.middleware.js creado en: src/middleware/auth.middleware.js
 - Crea la configuracion de passport con la estrategia de JWT verificando si pertenece a un usuario correcto 

[Documentación de passport](https://www.passportjs.org/packages/passport-jwt/)


En el archivo crypto.js (utils) se encriptará la contraseña pasada por el usuario y se realizará la comprobación del mismo: src/utils/crypto.js

 - hashPassword
 - comparePassword

Crea un controlador en src/users/users.controllers.js para obtener usuario por email y poder hacer el respectivo login en la ruta:
/api/v1/auth/login

Protege las rutas de patch y delete de users.router.js