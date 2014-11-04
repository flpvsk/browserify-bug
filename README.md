# Browserify transformations bug

### Steps to reproduce

```sh
npm i
./node_modules/browserify/bin/cmd.js -t reactify index.js
```

### Expected result

Transformations run on `module-1` files. Result should look like this:

```js
// ... not relevant code ...
/** @jsx React.DOM */

module.exports = React.createElement("div", null);

// ... not relevant code ...
```


### Actual result

Transformations do not run on `module-1` files:

```js
// ... not relevant code ...
/** @jsx React.DOM */

module.exports = <div></div>;

// ... not relevant code ...
```


### Fix :)

Use global-transform

```js
./node_modules/browserify/bin/cmd.js -g reactify index.js
```
