<h1 align='center'>
Webpack
</h1>

## Instalación

    $create-react-app nombre-del-proyecto

    $cd nombre-del-proyecto

    $npm i

una vez instalado podemos instalar webpack para poder meter sus nuevas caracteristicas para poder personalizar el build del proyecto con mis configuraciones y su ambiente de desalrrollo para personalizar el cli

    $npm i webpack -D
    $npm i webpack-cli -D

---

## Loaders

    $npm i ... -D
    $npm i babel-loader -D

* babel-loader
* file-loader
* image-webpack-loader
* style-loader
* css-loader
* sass-loader
* @svgr/webpack
* cson-loader

---

## webpack.config.js

    const path = require('path');
    const webpack = require('webpack');

    module.exports = {
        // mode: definir el entorno para el cual estamos configurando el build
        mode: "production",
        //entry: apuntas al archivo de entrada a la aplicacion
        entry: "./src/index.js",
        //output: defines donde alojarás los archivos estaticos generados uy puedes personalizar el nombre del archivo
        output: {
            path: path.join(__dirname, "public"),
            filename: "bundle.js",
        },
        //module rules: defines las configuraciones y reglas para la carga de las extensiones que tengan tus archivos
        module: {
            rules: [
                {
                    test: /\.(js|jsx)$/,
                    exclude: /node_modules/,
                    loader: "babel-loader",
                    options: {
                        presets: ['@babel/preset-env', '@babel/preset-react'],
                    },

                }
            ]
        },
        // devtool: es el inspector de recomendaciones y errrores en la generacion del build
        devtool: "source-map",
    }

---

## scripts

para build:

    "scripts": {
        "start": "react-scripts start",
        "build": "webpack --mode production",
        "test": "react-scripts test",
        "eject": "react-scripts eject"
    },

## Despues del build

se debe de agregar al html generado, la integracion del nuevo js que es el bundle.js de manera manual al body
