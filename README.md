 


# minimal-script-loader

![](https://img.shields.io/badge/minimal--script--loader-v1.0.0-green.svg) ![](https://img.shields.io/badge/no-tests%20yet-red.svg) 


Minimal browser library to import JS and CSS and to use XHR easily.

## Installation

### Install `npm` package:

~$ `npm install --save minimal-script-loader`

### Import the package:

#### a. Via `script` tag:

```html
<script src="node_modules/minimal-script-loader/dist/script-loader.min.js"></script>
```

If so, the library will be available at `ScriptLoader` global variable.

#### b. Via `browserify`:

```js
const ScriptLoader = require("minimal-script-loader");
```

----

Once done this, `ScriptLoader` is available in the scope.

## Examples

A demo of each type of call (`js`, `css` and `xhr`) is shown below.

### Load a external JS file:

```js
ScriptLoader.js("https://cdnjs.cloudflare.com/ajax/libs/qunit/2.8.0/qunit.js")
 .then(function() {
   console.log("QUnit was loaded successfully!");
 })
 .catch(function() {
   console.log("QUnit could not be loaded!");
 });
```

### Load a external CSS file:

```js
ScriptLoader.css("https://cdnjs.cloudflare.com/ajax/libs/qunit/2.8.0/qunit.css")
 .then(function() {
   console.log("QUnit (stylesheet) was loaded successfully!");
 })
 .catch(function() {
   console.log("QUnit (stylesheet) could not be loaded!");
 });
```

### Load a external XHR file:

```js
ScriptLoader.xhr({
   url: "/",
   method: "GET",
   headers: {"Custom-Headers":"Yes, we can too"},
   json: false,
   timeout: 5000
 })
 .then(function() {
   console.log("Self-call made successfully!");
 })
 .catch(function() {
   console.log("Self-call could not be made!");
 });
```




 


## API Reference

### class `ScriptLoader`


**Type:** class

**Extends:** `Object`

**Description:** The whole API is this class.




 


### static method `ScriptLoader.js(url)`


**Type:** static class method

**Parameter:** `{String} url`. URL to fetch the script from.

**Returns:** `{Promise} promise`. A `Promise` that will be `resolved`/`rejected` once the script is `loaded`/`failed`.

**Description:** This method creates a `script` tag, sets the `src` field and injects it into the DOM (`document.body`). It sets the `onload` and `onerror` into the request using the values provided to the `Promise`.




 


### static method `ScriptLoader.css(url)`


**Type:** static class method

**Parameter:** `{String} url`. URL to fetch the css stylesheet from.

**Returns:** `{Promise} promise`. A `Promise` that will be `resolved`/`rejected` once the stylesheet is `loaded`/`failed`.

**Description:** This method creates a `link` tag, sets the `rel`, `type` and `href` and injects it into the DOM (`document.head`). The callback called is always `success`, and immediately. But this is maintained in order to standarize the API (maybe some day stylesheet callbacks are a valid strategy).




 


### static method `ScriptLoader.xhr(options)`


**Type:** static class method

**Parameter:** `{Object} options`.

**Returns:** `{Promise} promise`. A `Promise` that will be `resolved`/`rejected` once the stylesheet is `loaded`/`failed`.

**Description:** This method is exactly [this function](https://github.com/naugtur/xhr#example). Refer to it for more information.




 


# Commands

The available commands of the project are displayed as `npm run ~` commands, so you can check them in `package.json#scripts`.

# Conclusion

It is important to have a handy way to easily import data externally in your web pages, scripts, apps, etc...

You will have to do it somehow.




