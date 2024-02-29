# this Keyword

The **"this"** keyword in JavaScript is used to refers to the current object.

> There are sevral uses of the **this** keyword in JavaScript.

### 1. Inside Global Context

When **this** is used alone, **this** refers to the global(window) object.

```javascript
console.log(this); // window {}

this.name = "JavaScript";
console.log(window.name); // JavaScript
```

### 2. Inside Function Context

When **this** is used in a function, **this** refer to the global(window) object or undefined in strict mode.

```javascript
function showThis() {
  console.log(this);
}

showThis(); // In a browser, points to window (or undefined in strict mode)
```

### 3. Inside Object Method

When **this** is used inside an object's method, **this** refers to the object that the method is called on.

```javascript
const obj = {
  name: "My Object",
  showName: function () {
    console.log(this); // refer to the current object

    console.log(this.name);
  },
};

obj.showName(); // point to the obj object
```

### 4. Inside Constructor Function

When a function is used as a constructor with the **new** keyword, **this** refers to the newly created instance.

```javascript
function Person(name) {
  this.name = name;
}

const person = new Person("John");

console.log(person.name); // point to the newly created instance
```

> When **this** is used with ES6 Classes, it refers to the current instance of the class similar to constructor function

### 5. Inside Inner Function

When you access **this** inside an inner function with method, **this** refers to the global object.

```javascript
const person = {
  name: "Jack",
  age: 25,
  greet: function () {
    console.log(this); // {name: "Jack", age ...}
    console.log(this.age); // 25

    // inner function
    function innerFunc() {
      // this refers to the global object

      console.log(this); // Window { ... }
      console.log(this.age); // undefined
    }

    innerFunc();
  },
};

person.greet();
```

### 6. Inside Arrow Function

Arrow functions do not have their own **this**. When you use **this** inside an arrow function, **this** refers to its parent scope object.

```javascript
const obj = {
  value: 42,
  getValue: function () {
    console.log(this.value); // point this current object with regular function
  },
};

obj.getValue();
```

```javascript
const obj = {
  value: 42,
  getValue: () => {
    console.log(this.value); // undefined
  },
};

obj.getValue(); // It refers to the outer(parent) scope
```

```javascript
const obj = {
  value: 42,
  getValue: function () {
    return () => {
      console.log(this.value); // 42
    };
  },
};

const fun = obj.getValue();

fun(); // point to obj because of arrow function
```

```javascript
const person = {
  name: "Jack",
  age: 25,
  greet: function () {
    console.log(this);
    console.log(this.age); // this refers to the object itself

    // here this refers to the parent scope
    const innerFunc = () => {
      console.log(this);
      console.log(this.name);
    };

    innerFunc();
  },
};

person.greet();
```

### 7. Inside Event Handler

In event handlers, **this** often refers to the element that triggered the event.

```javascript
const button = document.getElementById("myButton");

button.addEventListener("click", function () {
  console.log(this); // points to the button element
  this.classList.add("new-class"); // css class added on button element
});
```

### 8. Inside Function with Strict Mode

When **this** is used in a function with strict mode, **this** is undefined.

```javascript
this.name = "JavaScript";

function greet() {
  "use strict";
  console.log(this); //this refers to undefined
}

greet(); // undefined
```

> When using **this** inside a function with strict mode, you can use **JavaScript Function Call()**.

```javascript
this.name = "JavaScript";

function greet() {
  "use strict";
  console.log(this); // refers global object with call() function
  console.log(this.name); // JavaScript
}

greet.call(this);
```

> When you pass **this** with the **call()** function, **greet()** is treated as the method of the this object (global/window object).

### 9. Inside Call and Apply Methods

The **call()** and **apply()** methods allow you to set the value of **this** explicitly, when invoking a function.

```javascript
const person = {
  name: "John",
};

function greet() {
  console.log(`Hello, ${this.name}!`);
}

greet.call(person); // Outputs 'Hello, John!'
```

> When you pass person object with **call** function, **this** will refers the person object inside **greet()**.
