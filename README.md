# Modules

**Modules** are a way to organize and structure code in modern JavaScript applications. It is piece or chunk of a JavaScript code written in a file.

### Advantage of Modules

- Modules allow us to partitioning the entire code into separate files.
- Modules easy to maintain the code, debug the code, and reuse the piece of code.
- Module can be variable, function, class, array or object.

There are two main types of JavaScript modules:

### 1. CommonJS Modules

CommonJS is a module system used in **server-side** JavaScript environments, like Node.js.

- It uses **require()** to import modules and **module.exports** to export them.

```javascript
// in math.js
function add(a, b) {
  return a + b;
}

module.exports = { add };

// another file
const { add } = require("./math");
console.log(add(2, 8));

// OR
const math = require("./math");
console.log(math.add(2, 8));
```

```javascript
// in math.js
function add(a, b) {
  return a + b;
}

module.exports = add; // Like export default

// another file
const math = require("./math");
console.log(math(5, 8));
```

### 2. ES6 Modules

ES6 providing a more standardized and feature-rich module system.

- It uses **import** to bring in modules and **export** to export them.
- There are two kind of exports like **Named Exports** & **Default Exports**.

#### Named Exports:

Named exports are useful to export several values.

```javascript
// in math.js
export function add(a, b) {
  return a + b;
}

export function multiply(a, b) {
  return a * b;
}

// another file
import { add, multiply } from "./math";

console.log(add(5, 8));
console.log(multiply(5, 8));
```

#### Default Exports:

Export Default is used to export only one value from a file which can be a variable, function, class or object. The default export can be imported with any name.

```javascript
// in math.js
export default function add(a, b) {
  return a + b;
}

// another file
import anyName from "./math";
console.log(anyName(5, 8));
```

> You can rename the module with "as" keyword when you got conflict with two same name module.

```javascript
import { add as added } from "./math";

console.log(added(5, 8));
```
