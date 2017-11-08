# angular5-closure-extern-bug

Reproduction of needing to require unnecessary extern from platform-browser.js

To reproduce:

1. clone the repository
2. install the ngr cli with `npm i -g angular-rollup`
3. `npm install` all dependencies
4. run the build `ngr build prod --verbose`
5. see error in terminal

```
WARN node_modules/@angular/platform-browser/esm2015/platform-browser.js:1542: 
Originally at:
node_modules/packages/platform-browser/src/dom/util.js:38: ERROR - variable COMPILED is undeclared

1 error(s), 0 warning(s)
```

6. open `closure.externs.js` and add the line `var COMPILED = function(){};` save the file
7. run the build `ngr build prod --verbose`
8. build finishes without errors

This project assumes the Java JDK already installed.
