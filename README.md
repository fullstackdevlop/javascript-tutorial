# ES6

ECMAScript 6, often referred to as ES6 or ECMAScript 2015, is a major update to the JavaScript programming. It was officially released in june 2015 by the ECMAScript standards committee.

ES6 intoduces several new features and enhancements to JavaScript, making the language more expressive, readable and powerful.

There are some key features of ES6 like:

- [Let and Const Declarations]()

- [Template Literals]()

- [Arrow Functions]()

- [Array Destructuring]()

- [Object Destructuring]()

- [Default Parameter]()

- [Rest Parameter]()

- [Spread Operator]()

- [Object Literal]()

- [Modules]()

- [Promises]()

- [Async/Await]()

- [Try...catch (Error Handling)]()

- [For...of]()

- [For...in]()

- [Classes]()

- [Map, Set, WeakMap, WeakSet]()

- [Octal and binary literals]()

- [Symbols]()

- [Generators]()

- [Iterators]()

- [Proxy]()

- [Reflect]()

- [Array Extensions: Array.of(), Array.from(), Array.find(), Array.findIndex(), Array.includes()]()

- [String Extensions: startsWith(), endsWith(), includes()]()

- [Math Methods: Math.sign, Math.trunc, Math.hypot]()

- [Object Extensions: Object.assign(), Object.is()]()

### [Let and Const Declarations]()

ES6 introduced two new way to declare variables `let` and `const`. These provide block-scoping, which helps avoid issues related to variable hoisting.

### [Template Literals]()

Template Literals provide a cleaner and more readable way to work with strings, especially when dealing with dynamic content and multiline text. They are enclosed by backticks(``) rather than single or double quotes.

### Arrow Functions

Arrow functions is a concise way to write function expression. It provide a more compact syntax compared to traditional function expression. Thay have a shorter syntax and do not have their own this, arguments, super or new.target. It also cannot be used as constructors.

### Array Destructuring

Array destructuring is a powerful feature that allow you to extract values from array and assign them to variables in a concise and expressive way.

> Destructuring is a feature in programming languages that allows you to extract values from arrays, objects, or other data structures in a more concise and convenient way.

### Object Destructuring

Object destructuring is a convenient way to extract multiple properties from an object and assign them to variables.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  country: "USA",
};

// Extracting properties using object destructuring
const { firstName, lastName, age } = person;

console.log(firstName); // Output: John
console.log(lastName); // Output: Doe
console.log(age); // Output: 30
```

> It's particularly useful when you're working with objects that have a lot of properties, as it allows you to quickly and cleanly extract just the values you need.

### Default Parameter

Default parameters allow you to assign default values to function parameters in case the values are not provided or are undefined. This feature was introduced in ECMAScript 6 (ES6).

```javascript
function greet(name = "World") {
  console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, World!
greet("Alice"); // Output: Hello, Alice!
```

### Rest Parameter

The **Rest Parameters** is an improved way to handle function parameters. It allows us to represent an indefinite number of arguments as an array. By using the rest parameters, a function can be called with any number of arguments.

- The Rest Parameter is prefixed with three dots `(...)` followed by the parameter name.
- It has to be the **last argument** because it is used to collect all of the remaining elements into an array.
- Before ES6, the **arguments object** of the function was used.

```javascript
function myFunc(a, b, ...rest) {
  console.log(a); // Outputs: 1
  console.log(b); // Outputs: 2

  // remaining arguments values as an array
  console.log(rest); // Outputs: [3, 4, 5, 6, 7, 8, 9, 10]
}

myFunc(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```

### Spread Operator

The **Spread Operator** `(...)` is used to expand or spread elements of an iterable like array, object, string and function.

It is a very simple and powerful feature that helps us to write nicer & shorter code, which is denoted by three dots `(...)`.

### Object Literal

The **Object Literals** is one of the short form for creating an object in JavaScript.

- Define an object in the **curly braces {}** with ``key:value` pairs separated by a comma.
- The key would be the name of the property and the value will be a literal value or a function (method).
- Properties can be accessed using **dot** notation or **bracket** notation.

```javascript
// Creating Object with literal
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  isStudent: false,
  greet: function () {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}.`);
  },
};

// Accessing properties
console.log(person.firstName); // Outputs: John
console.log(person["lastName"]); // Outputs: Doe

// Calling a method
person.greet(); // Outputs: Hello, my name is John Doe.
```

### [Modules]()

Modules are a way to organize and structure code in modern JavaScript applications. It is piece or chunk of a JavaScript code written in a file.

#### Advantage of Modules

- Modules allow us to partitioning the entire code into separate files.
- Modules easy to maintain the code, debug the code, and reuse the piece of code.
- Module can be variable, function, class, array or object.

### Promises

A Promise is a special JavaScript object and used to manage when dealing with multiple asynchronous operations. It provides a cleaner and more flexible way to handle asynchronous operations.

> Benefit of Promises:

- Improves code readability
- Better handling of asynchronous operations
- Provides easy error handling

#### A promise has three states:

1. Pending - The initial state; the promise is neither fulfilled nor rejected.

2. Fulfilled: The operation completed successfully, and the promise has a resulting value.

3. Rejected: The operation failed, and the promise has a reason for the failure.

### Async/Await

JavaScript **"async/await"** simplifies the handling of asynchronous code.

It helps make the code more readable and maintainable compared to using callbacks or chaining .then() calls.

- **Async** keyword is used to declare a function as asynchronous. The async function return a promise.

```javascript
async function greet() {
  return "Hello JavaScript";
}

const msg = greet();

console.log(msg); // Promise {<fulfilled>: 'Hello JavaScript'}
```

- **Await** keyword is used inside an async function to wait for a promise to resolve before proceeding to the next line of code.

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true;

    if (success) {
      resolve("Promise called!");
    } else {
      reject("Rejected");
    }
  }, 2000);
});

// using the chaining method then()
myPromise.then((result) => {
  console.log(result);
});

// consuming promise with async/await
async function myFunc() {
  const data = await myPromise;
  console.log(data);
}

myFunc();
```

### Try...catch (Error Handling)

**try...catch** statement is used to handle errors that occur within a block of code.

- The **try** block contains the code that might throw an error. If any error occurs within this block, it's immediately caught.

- If an exception is thrown in the **try** block, the execution immediately stops and jumps to the **catch** block.

```javascript
try {
  // Code that might throw an error
  // For example:
  // console.log(nonExistentVariable); // This will throw a ReferenceError
} catch (error) {
  // Code to handle the error
  console.error("An error occurred:", error);
}
```

### For...of
