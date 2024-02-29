# Scope

The term of **scope** refers to the accessibility of a particular variable within the program.

JavaScript variables have different scopes such as:

- Global Scope
- Function Scope
- Block Scope

### 1. Global Scope

Any variable declared at the top of a program or outside of a function is known as global scope variable.

```javascript
// global variable
var scope = "JavaScript";
console.log(scope);

function access() {
  console.log(scope);
}
access();
```

The value of a global variable can be changed inside a function.

```javascript
// global variable
let a = "Hello";

function greet() {
  a = 3;
}

// before the function call
console.log(a); // Output: Hello

// after the function call
greet();
console.log(a); // Output: 3
```

> It is a good practice to avoid using global variables because the value of a global variable can change in different areas in the program.

### 2. Function Scope

Any variable can be accessed within a function that are function scope variable.

```javascript
function myFunc() {
  var car = "BMW";
  console.log(car); // BMW
}

myFunc();

console.log(car); // Uncaught ReferenceError: car is not defined
```

> Since you can't access a function scope variable outside the function.

### 3. Block Scope

Variables declared with **let** and **const** are block scope, means they are limited to the block enclosed by **curly braces {}** where they are defined.

```javascript
function scopeFunction() {
  var functionVariable = 5; // Function scope
  console.log(functionVariable);

  if (true) {
    var blockScopeVar = 20; // Function-scoped in ES5
    let blockScopeLet = 30; // Block-scoped in ES6
    const blockScopeConst = 40; // Block-scoped in ES6
  }

  console.log(blockScopeVar); // Accessible because of function scope

  // console.log(blockScopeLet); // Uncaught ReferenceError: blockScopeLet is not defined
}

scopeFunction();
```

#### Variable without declaration

If a variable is used without declaring it, that variable automatically becomes a global variable.

```javascript
function greet() {
  a = "hello";
}

greet();

console.log(a); // hello
```

> It helps you manage the visibility and lifetime of variables and functions within your programs.

## Lexical Scope (Closure)

A function can access variables from its outer (enclosing) scope. This is known as lexical scope or closure.

```javascript
function outerFunction() {
  var outerVariable = "I'm outer!";

  function innerFunction() {
    console.log(outerVariable); // Accessing outerVariable from the outer scope
  }

  innerFunction();
}

outerFunction(); // Outputs: I'm outer!
```
