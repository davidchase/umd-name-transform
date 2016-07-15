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

Also will convert dashes to camelcase `my-module-with-dashes` to `myModuleWithDashes`

## Install

```sh
npm install umd-name-transform --save-dev
```

## Usage

```sh
rollup -c --name '@somecope/somepackagename' | umd-name-transform -o dist/somepackagename.js
```

This will transform the output from rollup and write to `dist/somepackagename.js`

**Note** this module assumes that you have created the given directories in the above case its `dist`
