<h1 align='center'>
Vite.js
</h1>

## Instalación

    $npm create vite@latest

- Ingresamos el nombre de nuestro proyecto:
nombreApp

---
    $npm install
    $npm run dev

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


## Modificar la ruta en caso de que no genere la carpeta src

    export default {
        root: 'src',
        build: {
            outDir: '../dist'
        }
    }
---
    $npm i
