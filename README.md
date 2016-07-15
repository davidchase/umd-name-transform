# umd-name-transform
Transform stream for UMD bundle names

## Why

Lets say you have a scoped npm package with some esnext code and you want to say use [rollup](rollupjs.org) to bundle it for the browser with UMD.

```sh
rollup -c --name '@somescope/somepackagename' -o dist/somepackagename.js
```

the result will be 

```js
factory((global.@somescope/somepackagename = {})
```


This module attempts to fix that so that results looks like 

```js
factory((global['@somescope/somepackagename']= {})
```

## Install

```sh
npm install umd-name-transform --save-dev
```
