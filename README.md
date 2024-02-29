# Variables

Variables are the building blocks of any programming language that used to store reusabble values that can be any data types like string, number, boolean, array, object etc.

> **var, let,** and **const** keywords are used to declare variables.

### Variable Naming Rules

There are some common naming rules for variables in programming language:

- Names must begin with a letter.
- Names can contain letters, digits, underscores, and dollar signs.
- Names can also begin with dollar sign ($) and underscore (\_).
- Names are case sensitive (y and Y are different variables).
- By convention, JavaScript variable names are written in camelCase.
- Reserved words (like JavaScript keywords) cannot be used as names.

## Difference between var, let and const

**var, let,** and **const** are used to declare variables, but they have some key differences in terms of use like:

### Scope

- **var** has the function or global scope.
- **let** have the block scope.
- **const** variable has the block scope.

### Update & Re-declaration

- **var** can be updated and re-declared into the scope.
- **let** can be updated but cannot be re-declared into the scope.
- **const** cannot be updated or re-declared into the scope.

```javascript
var x = 10;
console.log(x); // Output: 10

// Update the value of x
x = 20;
console.log(x); // Output: 20

// Redeclare x in the same scope
var x = 30;
console.log(x); // Output: 30
```

```javascript
let x = 10;
console.log(x); // Output: 10

// Update the value of x
x = 20;
console.log(x); // Output: 20
```

```javascript
let y = 30;
console.log(y); // Output: 30

// This will throw an error (Identifier 'y' has already been declared.)
let y = 40;
```

```javascript
const a = 10;
console.log(a); // Output: 10

// This will throw an error because you cannot reassign a constant variable
a = 20;
```

```javascript
const b = 30;
console.log(b); // Output: 30

// This will throw an error because you cannot redeclare a constant variable in the same scope
const b = 40;
```

### Declar without Initialization

- **var** can be declared without initialization.
- **let** can be declared without initialization.
- **const** cannot be declared without initialization.

###

- **var** can be accessed without initialization as its default value is “undefined”.
- **let** cannot be accessed without initialization otherwise it will give ‘referenceError’.
- **const** cannot be accessed without initialization, as it cannot be declared without initialization.

###

- **var** are hoisted to the top of their function or global scope. This means you can use a var variable before it's declared in the code.
- **let, const** is not hoisted to the top of the block, and it cannot be used before it's declared.
