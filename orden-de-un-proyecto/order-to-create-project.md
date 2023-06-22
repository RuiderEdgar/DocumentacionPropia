# Orden para crear un proyecto

## No se implementará para el proyecto

no implementar en services: queues, redis y los workers

Ocuparemos:

-   abstracciones de la BD para las consultas
-   definiciones de cada modulo (por lo menos 2): interfaces, modelos, rutas, schemas de validacion
-   helpers: errores, generadores, middlewares
-   decoradores: los validadores
-   interfaces de exposicion
-   configs: env, logs
-   bootstrap
-   cloudinary como plus, de pendendiendo de si usamos imagenes

## Tecnologías a usar

-   Node
-   Express

---

## Inicializando el proyecto

1.  Iniciamos creando la carpeta
2.  Hacemos un

        $npm init -y

    Podemos agregar la descripcion al package.json

Extra:

3. Elejir una arquitectura: Por capas (By Layers), Onion, Hexagonal. Recomendado: onion
   Para ello se debe de abordar la problematica como:
   a) Analisis de los requerimientos
   b) Definir las tecnologías o Stack
   c) Definicion de lineamientos, ej: implentacion, Definir una arquitectura, si es limpia como usar TS para POO

4. Crea la carpeta src

## Trabajando con Onion

### Primera capa

Creamos los lineamientos

---

Creamos los archivos

-   .editorconfig
-   .eslintrc.json
-   .eslintignore
-   .prettierrc (puede ser .prettierrc o .prettierrc.json)
-   nodemon.json
-   .gitignore

empezamos a agregar los modules

-   npm i typescript -D -E
-   npm i @types/express -D -E
-   npm i ts-node -D -E
-   tsc --init (para crear el archivo de tsconfig.json)
-   npm i nodemon -D -E
-   npm i eslint -D -E
-   npm i @typescript-eslint/eslint-plugin @typescript-eslint/parser -D -E
-   npm i prettier -D -E
-   npm i eslint-config-prettier -D -E
-   npm i express -S -E

Creamos el archivo raiz

dentro de src

-   app.ts (tambien main.ts o index.ts)

En package.json

-   cambiamos el main a "main": "app.ts"
-   los scripts
    -   dev: "nodemon src/app.ts"
    -   lint(o tambien lint:check):
    -   lint:fix:
    -   prettier:check:
    -   format(tambien format:fix o prettier:format prettier:fix):

Llenamos el nodemon
el editorconfig
el eslintrc
el tsconfig
el prettierrc

---

## Tools back-end package.json

sockets: permite habilitar la capacidad para manejar comportamientos en _tiempo real_
ej: mensajes, trackeo mapa, notificaciones, chat, seguir pedido

socket.io: configurar servidor con realtime

@socket.ioRedis-adapter: soporte para redis

Redis: configura un servidor con BD para el manejo de cache, entre otras, se necesita habilitar un server para redis

Compression: comprime el peso de la info que llega al servidor

Cokkie-session: maneja la autenticacion en base a datos del usuario

Cors: maneja la comunicacion entre dominios

Dotenv: maneja las referencias de mis variables de entorno.
quien resuelven en tiempo de ejecucion las variables de entorno? las resuelve a nivel de S.O

express-async-errors: maneja de forma facil los errores asincronos

http-status-code: permite referencial e inyectar el manejo de status code de una buena forma

mongoose: permite manejar las abstracciones y procesos referentes a BD no relacionales, para my-sql: type-orm, prisma, sequalize, micro-orm

tsconfig-paths: trabajar con alias para las importaciones, para crear rutas y sea mejor trabajar con ellas

typescript-transform-paths

@types/hpp

@types/compression

@types/cookie-session

@types/bunyan

## Trazabilidad de monitoreo de procesos

bunyan (recomendado) o winston: configura niveles de alertas en nuestr codigo para hacerles seguimiento, ej. para la BS si esta activa, si esta arriba, si el socket o redis, etc cosas importantes

### Librerias para ciber-seguridad

para añadir una capa de seguridad a nuestra app o servidor desde node

hpp: permite proteger mi server de ataques de hackers a mis parametros de rutas xss
(croos-site-scripting)

helmet: proteger el servidor cuando la info navega en la web

### para rendimiento

(no necesario)

snyk, sonarqube, kibana, locust, kubernetes

---

En src

-   creamos la carpeta bootsrap
-   dentro de boostrap: setupServer.bootstrap.ts y setupDatabase.bootstrap.ts
-   creamos la carpeta features y shared (capa media)
-   creamos interface y dentro http (capa de exposicion)

Se crea en la raiz el archivo .env para dejar las definiciones, DB, env, etc

se crea el archivo config.ts en src y se crea la clase de Config para las env

el .env.example se sube sin los valores para que los demas sepas cuales son las env

empezamos a trabajar en el setupDatabase.bootstrap

trabajamos con app.ts

en congif.ts podemos quitar || '' para empezarlas a monitorear

empezamos a trabajar con setupServer

instanciamos el server en la app.ts

agregar el bunyan al script de dev para darle color al texto de la terminal

creamos en src el directorio configs y movemos configs.ts a esa carpeta y lo llamamos configEnvs.ts, tambien creamos el archivo configLogs.ts

podemos definir los decoradores el tsconfig.json

dentro de shared creamos globals y dentro helpers y dentro el archivo error-handler.ts

trabajamos con error-handler.ts

si tsc-alias no funcina al hacer el build y no quita los decoradores, instalamos ttypescript y en el build: "ttsc -p ."

creamos todos los errors, empezando por las interfaces para definir las fachadas y la clase padre, la I es porque se refiere a Interface

podemos crear todas las carpetas dentro de shared

---

definiciones de carpetas:

-   Cloudinary: almacenamiento de imagenes
-   errors: para hacer los tipos de errores
-   generators: para indentificadores, manejar cadenas
-   decorators: abstracciones de logica mediante decoradores
-   services: abstracciones de servicios para manipular la logica final y quitar responsabilidad a la arquitectura limpia
-   workers: observadores a nivel de app, para derivar tareas, administrar tareas y administrar el flujo de datos en el servidor

---

en app metemos los import despues de htpp_status y el de los errores, creamos el globalErrorHandler y los de socket

en starServe, inyectamos los sockets para levantar el de server

Para trabajar con imagenes, instalamos cloudinary como -SE, y metemos sus env

Creamos los generators

### Segunda capa

_features_

Arquitectura cebolla tenemos unas Normativas, como el auth, user
ejemplos: medicos

-   Crear un modulo de auth, user

-   dentro de auth creamos carpetas:
    -   models(modelos de representacion de BD),
    -   controllers (logica de negocio),
    -   interfaces (estructuras de datos),
    -   routes (definiciones de rutas para este modulo),
    -   schemes (esquemas de validacion)

dentro de user: interfaces, models

al final cada modulo puede contener mas o menos de estos, de penderá de lo que necesite

creamos en decorators el joi-validation.decorators.ts, e instalamos joi -SE

dentro de auth empezamos a crear los schemas para las validaciones de campos

empezamos a trabajar con los models, que son los modelos para la BD, para esto primero:

-   creamos user.interface en User/interfaces
-   creamos dentro de models el user.schema.ts

los schemas son las colecciones que se van a guardar en la BD, y las interfaces es el tipo de datos para ese schema

Despues empezamos a trabajr con las interfaces de auth

**workers**: sirven para deslindar responsabilidades al servidor, son vigilantes que van recibiendo y enviando las tareas por separadas, es un multitask, y sirve en temas de performace en el server.
Librerias para los workers: RabbitMQ(microservicios), Kafka, BullMQ, Bull(light), sns (amazon)

librerias para hashear:

-   bcrypt(no ocupar): corre por debajo python y se debe tener instalado
-   bcrypt.js: corre con js

instalamos bcryptjs -SE y sus tipos:
npm i --save-dev @types/bcryptjs -E

creamos el schema de auth en models

Creamos la carpeta middlewares en helpers y dentro auth-middleware.ts

instalamos jsonwebtoken -SE
npm i --save-dev @types/jsonwebtoken

en services creamos directorios: db, queues, redis

instalamos bullmq y lodash y @bull-board/express -SE

creamos en helpers el clodinary, configuramos en configEnvs para las keys y lo injectamos en la app

trabajamos en services/redis y creamos:
base.cache.ts, redis.connection.ts, user.cache.ts

metemos redis a setupDatabase.bootstrap y la conexion

hacemos el script dev para ver si corre bien

empezamos a trabajar los workers, creamos: auth.worker.ts y user.worker.ts
trabajamos con user.worker despues auth.worker

trabajamos en queues: base.queue.ts
despues en auth.queues.ts

Despues en services/db creamos auth.service.ts y user.service.ts y trabajamos con auth

creamo el user.queue.ts

y despues llenamos el user.service.ts

y añadinmos ese servicio de user.service a user.worker

Despues de todo esto, nos pasamos a features/auth/controllers/ creamos signup.ts

npm i --save-dev @types/lodash

podemos abstraelos y creamos en controllers utilities

Para los endpoints (que es la documentacion)
trabajamos con la extension REST Client

en endpoints creamos el archivo de la ruta, observamos que al hacer el send, nos regresa not found

Para ello creamos las rutas de exposicion, vamos a interfaces/http/routes.ts

creamos la ruta de featrues/auth/routes/authRoutes.ts

una vez creada las rutas, la integramos al server de boostrap

---

## Creando otro modulo para la logica de negocio

**Singin**

Empezamos a crando en auth/controllers/singin.ts
(podemos ayadir el signout, currentUser tambien)

empezamos a trabajr en singin

creamos la documentacion en auth.http

creamos la ruta en auth/routes/authRoutes

para el singout hacemos lo mismo:
Trabajamos en signout, lo inyectamos a authRoutes, pero como es un comportamiento diferente, sera un GET, lo manejamos un poco diferente y al final tambien lo inyectamos en interfaces/http/routes.ts
y probamos haciendo la peticion

creamos la ruta currentUser, creamos la ruta en las rutas padres, despues creamos su ruta hija, puede ser en authRoutes o crear currentRoutes ->

De controllers/utilities/currentUser, trabajamos en ella

Ahora empezaremos a crear el servicio de mensajeria
Creamos el archivo de emails en services, para ello trabajaremos con **Nodemailer (desarrollo/test) y SendGrid (production)**

npm i nodemailer @sendgrid/mail -SE
npm i --save-dev @types/nodemailer

creamos mail.transport.ts
y directorio templates

usar motores de plantillas solo para los emails, para la UI no usarlo

trabajamos con mail.transport.ts

despues creamos su queue para optimizarlo en colas
creamos su worker de email.queue, email.worker.ts

instalamos ejs para las plantillas de los correos

npm i ejs -SE
npm i --save-dev @types/ejs -E

dentro de templates/forgot-password/forgot-password-template.ejs
dentro de templates/reset-password/reset-password-template.ejs

creamos su ts para cada uno

despues vamos a comprobar que se esten propagando bien

en signin.ts de auth/controllers podemos crearlo para ver si los correos funcionan, de prueba no mas

creamos las veriones de prueba

npm i ip -SE
npm i moment -SE
npm i --save-dev @types/ip -E

agregamos el passowordResetToken y Expires de user.schema a auth.schema y al authDocument.interface

borramos user.interface
sacamos de userDocument lo de password token y expires

el auth/controllers creamos el password

trabajamos con el password pero antes se creo el query en auth.service.ts de la base de datos el query para el resetToken
