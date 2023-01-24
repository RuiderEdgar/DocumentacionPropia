<h1 align="center"> Introducción a React</h1>

---

## Creando el proyecto con webpack

### Instalacion

        $npx create-react-app nombreProyecto
---

### Intrucciones

- Borrar todo src y volve a crearlo
- Tener siempre un index.js
- Siempre importar React en los modulos ('Import react')
- Podemos poner extension .js o .jsx especificando la extension en el import

---

### Eventos

- onHandlers: onClick, onChange, onSubmit (podemos quitar el de recarga con

        ((e) => e.preventDefault())

---

### Hooks

- useState
- useEffect
- etc

#### useState

        import React, { useState } from "react";
        const [state, setState] = useState(initialState);


const [inicializacion, funcion para ajustar el valor] = useState()

Para declarar la variable, se declara en useState()

        const [inicializacion, funcion] = useState(0)

        onClick={() => setVariable(modificar el valor)}

#### useEffect

Se ejecuta cada vez que hay un cambio o hace un render

        useEffect(() => {
                console.log('render')
        })

Si nosotros agregamos un arreglo vacio, se ejecutará solo una vez

        useEffect(() => {
                console.log('render')
        }, [])

El arreglo indica que depende de una variable, por lo tanto, se puede ejecutar una funcion cada vez que la variable de la que depende cambie, osea lo esta vigilando, a su cambio, hace algo

        useEffect(() => {
                console.log('render')
        }, [nameVariable])

Podemos tener mas de una variable "vigilada"

        useEffect(() => {
                console.log('render')
        }, [nameVariable, nameVariable2])

- Sirve mas para traer datos del backend y guardalos en una variable o a un estado de react
- Para que cuando cambie una interfaz y en otra parte de la interfaz tambien cambie
