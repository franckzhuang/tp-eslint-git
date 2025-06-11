## 2. Test d’ESLint sur un fichier JavaScript

2. Lorsque qu'on lance la commande `npx eslint app.js` directement, ESLint ne retourne rien.   
Lancé sur index.js, j'obtiens : 
```bash
   2:1   error  Expected indentation of 2 spaces but found 0    indent
   2:15  error  Missing semicolon                               semi
   3:1   error  Expected indentation of 2 spaces but found 0    indent
   3:38  error  Missing semicolon                               semi
   4:1   error  Expected indentation of 2 spaces but found 0    indent
   4:14  error  Missing semicolon                               semi
   7:7   error  'unusedVar' is assigned a value but never used  no-unused-vars
  11:17  error  Strings must use singlequote                    quotes
  11:39  error  Missing semicolon                               semi
  12:11  error  Missing semicolon                               semi
  14:15  error  Missing semicolon                               semi
  19:7   error  'message' is assigned a value but never used    no-unused-vars
  19:35  error  Missing semicolon                               semi
  21:5   error  Unexpected constant condition                   no-constant-condition
  22:15  error  Strings must use singlequote                    quotes
  22:47  error  Missing semicolon                               semi
  25:7   error  'tableau' is assigned a value but never used    no-unused-vars
  26:1   error  Expected indentation of 2 spaces but found 0    indent
  28:1   error  Expected indentation of 2 spaces but found 0    indent
  29:2   error  Missing semicolon                               semi
  31:20  error  Missing semicolon                               semi
  33:34  error  Missing semicolon                               semi
  36:10  error  'toutFaire' is defined but never used           no-unused-vars
  37:23  error  Missing semicolon                               semi
  38:14  error  Missing semicolon                               semi
  39:14  error  Missing semicolon                               semi
  40:14  error  Missing semicolon                               semi
  41:14  error  Missing semicolon                               semi
  42:14  error  Missing semicolon                               semi
  43:14  error  Missing semicolon                               semi
  44:14  error  Missing semicolon                               semi
  45:14  error  Missing semicolon                               semi
  46:14  error  Missing semicolon                               semi
  47:15  error  Missing semicolon                               semi
  48:35  error  Missing semicolon                               semi
  49:21  error  Missing semicolon                               semi
  53:25  error  Missing semicolon                               semi
  54:3   error  Missing semicolon                               semi
  56:7   error  'd' is assigned a value but never used          no-unused-vars
  56:21  error  Missing semicolon                               semi
  58:10  error  'fetchData' is defined but never used           no-unused-vars
  60:39  error  Missing semicolon                               semi
  63:7   error  'nombres' is assigned a value but never used    no-unused-vars
  64:15  error  Missing semicolon                               semi
  65:3   error  Missing semicolon                               semi
  67:1   error  Unexpected 'debugger' statement                 no-debugger
  67:9   error  Missing semicolon                               semi
  72:2   error  Missing semicolon                               semi

✖ 48 problems (48 errors, 0 warnings)
```

3. Après avoir lancé le fix, je n'ai plus que 9 erreurs : 
```bash
   7:7   error  'unusedVar' is assigned a value but never used  no-unused-vars
  19:7   error  'message' is assigned a value but never used    no-unused-vars
  21:5   error  Unexpected constant condition                   no-constant-condition
  25:7   error  'tableau' is assigned a value but never used    no-unused-vars
  36:10  error  'toutFaire' is defined but never used           no-unused-vars
  56:7   error  'd' is assigned a value but never used          no-unused-vars
  58:10  error  'fetchData' is defined but never used           no-unused-vars
  63:7   error  'nombres' is assigned a value but never used    no-unused-vars
  67:1   error  Unexpected 'debugger' statement                 no-debugger

✖ 9 problems (9 errors, 0 warnings)
```
---
## 3. Intégration avec Git Hooks (Husky)

1. Pendant l'installation, j'obtiens le warning suivant : 
```bash
husky - install command is DEPRECATED
```

2. Même chose que la question 1, j'obtiens le warning : 
```bash
husky - add command is DEPRECATED
```

3. Lorsque je test le hook en faisant un commit, tout se passe bien je n'ai pas d'erreurs ce qui est bizarre.
Il semblerait que cela soit dû à une mauvaise configuration, j'utilise donc `git config core.hooksPath .husky
` (car le path était `husky/_hooks` au lieu de `.husky`) et cela fonctionne.
J'obtiens le message d'erreur suivant :
```bash
git commit -m "Test du hook ESLint 2"

   1:16  error  Strings must use singlequote  quotes
   2:21  error  Strings must use singlequote  quotes
   3:30  error  Strings must use singlequote  quotes
   7:13  error  Strings must use singlequote  quotes
   9:15  error  Strings must use singlequote  quotes
  11:14  error  Strings must use singlequote  quotes
  11:23  error  Strings must use singlequote  quotes
  12:16  error  Strings must use singlequote  quotes
  13:16  error  Strings must use singlequote  quotes
  13:25  error  Strings must use singlequote  quotes
  14:7   error  Strings must use singlequote  quotes
  14:26  error  Strings must use singlequote  quotes
  17:13  error  Strings must use singlequote  quotes
  17:56  error  Strings must use singlequote  quotes
  18:13  error  Strings must use singlequote  quotes

   7:7   error  'unusedVar' is assigned a value but never used  no-unused-vars
  19:7   error  'message' is assigned a value but never used    no-unused-vars
  21:5   error  Unexpected constant condition                   no-constant-condition
  25:7   error  'tableau' is assigned a value but never used    no-unused-vars
  36:10  error  'toutFaire' is defined but never used           no-unused-vars
  56:7   error  'd' is assigned a value but never used          no-unused-vars
  58:10  error  'fetchData' is defined but never used           no-unused-vars
  63:7   error  'nombres' is assigned a value but never used    no-unused-vars
  67:1   error  Unexpected 'debugger' statement                 no-debugger

✖ 24 problems (24 errors, 0 warnings)
  15 errors and 0 warnings potentially fixable with the `--fix` option.

```
---

## 4. Configuration avancée d’ESLint

1. J'utilise un fichier `eslint.config.mjs` et non un `.eslintrc.json` : 
```mjs
export default defineConfig([
  {
    files: ["**/*.{js,mjs,cjs}"],
    plugins: { js },
    extends: ["airbnb-base"],
    rules: {
      "no-console": "warn",
      indent: ["error", 2],
      quotes: ["error", "single"],
    },
    languageOptions: {
      globals: globals.browser,
      env: {
        browser: true,
        node: true,
      },
    },
  },
  { files: ["**/*.js"], languageOptions: { sourceType: "commonjs" } },
]);
```

2. Le package.json à jour avec le lint :
```json
{
  "name": "tp-eslint-git",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "prepare": "husky install",
    "lint": "eslint ."
  },
  "private": true,
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "devDependencies": {
    "@eslint/js": "^9.28.0",
    "eslint": "^9.28.0",
    "globals": "^16.2.0",
    "husky": "^9.1.7"
  }
}
```

3. Cela ne fonctionne pas, j'ai les erreurs suivants : 
```bash
Oops! Something went wrong! :(

ESLint: 9.28.0

TypeError: Plugin "" not found.
    at findPluginConfig (/Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:251:9)
    at /Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:415:25
    at Array.map (<anonymous>)
    at processExtends (/Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:413:36)
    at /Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:485:38
    at Array.flatMap (<anonymous>)
    at processConfigList (/Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:485:20)
    at defineConfig (/Users/franck/WebstormProjects/tp-eslint-git/node_modules/@eslint/config-helpers/dist/cjs/index.cjs:520:9)
    at file:///Users/franck/WebstormProjects/tp-eslint-git/eslint.config.mjs?mtime=1749654260284:5:16
    at ModuleJob.run (node:internal/modules/esm/module_job:234:25)
```
J'ai donc remis cette config : 
```mjs
export default defineConfig([
  {
    files: ["**/*.{js,mjs,cjs}"],
    plugins: { js },
    extends: ["js/recommended"],
    rules: {
      semi: ["error", "always"],
      indent: ["error", 2],
      quotes: ["error", "single"],
      "no-unused-vars": ["error"]
    }
  },
  { files: ["**/*.js"], languageOptions: { sourceType: "commonjs" } },
  { files: ["**/*.{js,mjs,cjs}"], languageOptions: { globals: globals.browser } },
]);
```

## 6.Simulation d’un travail d’équipe
1. Création de la branche feature/ajout-fonction :
```bash
tp-eslint-git % git branch
* feature/ajout-fonction
  main
```

2. Erreur quand j'essaye de commit ce fichier `utils.js`:
```javascript
console . log(123)
```
```bash
git commit -m "Code non conforme"

/Users/franck/WebstormProjects/tp-eslint-git/.github/utils.js
  1:19  error  Missing semicolon  semi

✖ 1 problem (1 error, 0 warnings)
  1 error and 0 warnings potentially fixable with the `--fix` option.
```