# Hoisting

**Hoisting** is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase.

```javascript
// Using test variable before declaring
console.log(test); // Output: undefined
var test;
```

> The above program behaves like as variable **test** moved to the top.

```javascript
var test;
console.log(test); // Output: undefined
```

### 1. Hoisting with Variables

In terms of variable, **var** keyword is hoisted and **let** and **const** does not allow hoisting.

```javascript
a = 5;
console.log(a);
var a;
```

Variable **a** is used before declaring it & program works.

```javascript
// program to display value
var a;
a = 5;
console.log(a); // 5
```

```javascript
var a = 4;

function greet() {
  b = "hello";
  console.log(b);
  var b;
}

greet(); // Outputs: hello
```

### 2. Hoisting with Functions

A function can be called before declaring it.

```javascript
greet(); // Outputs: Hi, there...

function greet() {
  console.log("Hi, there...");
}
```

### 3. Hoisting and Function Expressions

With function expressions (assigning a function to a variable), only the variable declaration is hoisted, not the function implementation.

when you try to invoke the function before its declaration, it results in a **TypeError**.

```javascript
greet(); // TypeError: greet is not a function

var greet = function () {
  console.log("Hi, there...");
};
```

> Function expressions & arrow functions cannot be hoisted.

### 4. Block Scope Variables (let and const)

Variables declared with **let** and **const** are hoisted to the top of their block but they are not initialized until the actual declaration statement is encountered. You will get the **ReferenceError**.

```javascript
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
console.log(y); // 10
```
