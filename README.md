# Strict Mode

The **"Strict Mode"** makes easier to write good and secure JavaScript codes.

To enable strict mode in JavaScript, you simply add the **"use strict"** directive.

> Strict Mode used in global scope for the entire script or it can be applied to individual functions.

### 1. Undeclared variable is not allowed.

Variables must be declared with **var, let,** or **const**. Undeclared variables result in an error.

```javascript
"use strict";

x = 3.14; // will throw an error
```

### 2. Undeclared objects are not allowed.

```javascript
"use strict";

person = { name: "Carla", age: 25 }; // throws an error
```

### 3. Deleting an object is not allowed.

```javascript
"use strict";

let person = { name: "Carla" };

delete person; // throws an error
```

### 4. Duplicating a function parameter not allowed.

```javascript
"use strict";

function hello(p1, p1) {
  console.log("hello");
} // throws an error

hello();
```

### 5. this Keyword show undefined in function

```javascript
function hello() {
  "use strict";
  console.log(this); // undefined
}

hello();
```
