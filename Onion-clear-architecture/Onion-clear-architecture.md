# Arquitectura por capas

Para nuevas funcionales en el camino, para un alcance más grande,

## Front-end

### Capa de exposición

Para el front-end la primera capa (capa de exposicion) podria ser la UI o Delivery, aplicacion
Todo react, Componentes de react

### Segunda capa

Orquestar implementaciones - de acuerdo a la logica de negocio
Funciones auxiliares para reutilizar, funciones o clases que encapsulen las peticiones HTTP

---

## Back-end

### Capa de exposición

Tenemos el Api Rest con HTTP
Se expone mediante rutas HTTP, que es el api rest

### Segunda capa

Tenemos los Modules/Features que son como: los modules usuarios, medico, paciente, etc. todo se encapsula en features
Que puedo hacer con un usuario, denotar un usuario, que implementaciones lo rodean, Como lo declaro, si hay funciones o clases auxiolares que metan capacidades

### Centro

App description: entidades, arranque.
ej: Config, Setup, Bootstrap, contexto de la aplicacion, todo para que la app arranque.
Inicializar el server, conexion a BD, definir config de heeramientas, inicializaciones de websockets, redis, env, descripcion de un usuario.

### Resumen

-   Capa inicial: definicion de la aplicacion
-   Capa de implementaciones: se desgloza a partir de inicializaciones o procesos basico, iniciales
-   Capa de exposicion: Se expone de alguna forma
