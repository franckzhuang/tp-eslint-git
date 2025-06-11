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
