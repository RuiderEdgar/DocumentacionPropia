<h1 align='center'>
Instalacion de Eslint y Prettier
</h1>

<h2 align='center'>
Instalación
</h2>

*Como dependencias de desarrollo*

    $npm install eslint prettier @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react -D

<h2 align='center'>Configuracion</h2>

### En el file .eslintrc.cjs

    module.exports = {
      extends: [
        // By extending from a plugin config, we can get recommended rules without having to add them manually.
        'eslint:recommended',
        'plugin:react/recommended',
        'plugin:import/recommended',
        'plugin:jsx-a11y/recommended',
        'plugin:@typescript-eslint/recommended',
        // This disables the formatting rules in ESLint that Prettier is going to be responsible for handling.
        // Make sure it's always the last config, so it gets the chance to override other configs.
        'eslint-config-prettier',
      ],
      settings: {
        react: {
          // Tells eslint-plugin-react to automatically detect the version of React to use.
          version: 'detect',
        },
        // Tells eslint how to resolve imports
        'import/resolver': {
          node: {
            paths: ['src'],
            extensions: ['.js', '.jsx', '.ts', '.tsx'],
          },
        },
      },
      rules: {
        // Add your own rules here to override ones from the extended configs.
      },
    };

### En el file .eslintignore

    node_modules/
    dist/
    .prettierrc.js
    .eslintrc.cjs
    env.d.ts
    vite.config.js
    postcss.config.cjs
    tailwind.config.cjs

### Añadimos el script

Se añade en el package.json

    "scripts": {
      ...
      "lint": "eslint . --ext .jsx"
    },

### En el file .prettierrc.js

    module.exports = {
      "trailingComma": "all",
      "tabWidth": 2,
      "semi": true,
      "singleQuote": true,
      "printWidth": 120,
      "bracketSpacing": true
    }

### En el file .prettierignore

    node_modules/
    dist/
    .prettierrc.js
