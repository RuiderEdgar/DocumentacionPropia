<h1 align='center'>
Vite.js
</h1>

## Instalación

    $npm create vite@latest

-   Ingresamos el nombre de nuestro proyecto:
    nombreApp

---

    $npm install
    $npm run dev

## Configurar el archivo vite.config.js

---

export default defineConfig({
plugins: [react(),],
server: {
port: 3030,
},
preview: {
port: 4060,
},
build: {
//acelera el proceso de compilacion de los archivos cuando generas el build
incremebtal: true,
//habilitar un trabajo en conjunto con Babel, para el manejo ccorecto del versionado del js moderno a la version que necesite el navegador
babel: {
presets: ['@babel/preset-env', '@babel/preset-react'],
},
//habilitar la aceleracion de compilacion de TS a JS
typescript: {
tsconfig: "./tsconfig.json"
},
// Habilitar cache para optimizar el compilado de los recursos que caen en dist
cache: true,

     //habilitar la opcion de compresion optimizada para minimizar el tamañó de los archivos generados
     minify: true,

}
})

## Tailwind en vite

    $npm install -D tailwindcss postcss autoprefixer
    $npx tailwindcss init -p

### En el file tailwind.config.cjs

    /** @type {import('tailwindcss').Config} */
    module.exports = {
      content: [
        "./index.html",
        "./src/**/*.{js,ts,jsx,tsx}",
      ],
      theme: {
        extend: {},
      },
      plugins: [],
    }

### Añadir tailwind al css

@tailwind base;
@tailwind components;
@tailwind utilities;

    run dev

### Añadir tailwind al css

    $npm i sass

## Modificar la ruta en caso de que no genere la carpeta src

    export default {
        root: 'src',
        build: {
            outDir: '../dist'
        }
    }

---

    $npm i
