# Arrow Function

Arrow function allows us to create functions in a cleaner way compared to regular functions. It was introduced in the ES6 version.

- Thay have a shorter syntax and do not have their own this, arguments, super or new.target.
- They make our code more structured and readable.
- They are also called Lambda Functions.

```javascript
// Regular function expression
function add(a, b) {
  return a + b;
}

// Arrow function
const addArrow = (a, b) => a + b;
```

> There are a lot of features of arrow function such as:

### 1. Shorter Syntax

Arrow function has more shorter syntax, especially when the function body consists of a single expression. In such cases, you can omit the curly braces **{}** and the **return** keyword.

```javascript
// Arrow function with a single expression
const square = (x) => x * x;
```

### 2. No Binding of this keyword

Arrow function does not have its own **this**. Whenever you call this, it refers to its parent scope. So arrow function do not bind their own **this**.

#### Inside a regular function

```javascript
const person = {
  name: "Jack",
  age: 25,
  sayName: function () {
    // this is accessible
    console.log(this.age); // 25

    // this refers to the global object
    function innerFunc() {
      console.log(this); // window {...}
      console.log(this.age); // undefined
    }

    innerFunc();
  },
};

person.sayName();
```

#### Inside an arrow function

```javascript
const person = {
  name: "Jack",
  age: 25,
  sayName: function () {
    // this is accessible
    console.log(this.age); // 25

    // this refers to the parent scope
    const innerFunc = () => {
      console.log(this); // person {...}
      console.log(this.age); // 25
    };

    innerFunc();
  },
};

person.sayName();
```

### 3. Arrow Function with No Argument

If a function doesn't take any argument, then you should use empty parentheses.

```javascript
const greet = () => console.log("Hello");
greet(); // Hello
```

### 4. Arrow Function with One Argument

If a function has only one argument, you can omit the parentheses.

```javascript
const greet = x => console.log(x);
greet("Hello"); // Hello
```

### 5. Arrow Function as an Expression

You can also dynamically create a function and use it as an expression.

```javascript
const age = 5;

const welcome =
  age < 18 ? () => console.log("Baby") : () => console.log("Adult");

welcome(); // Baby
```

### 6. Multiline Arrow Functions

If a function body has multiple statements, you need to put them inside curly brackets **{}**

```javascript
const sum = (a, b) => {
  let result = a + b;
  return result;
};

console.log(sum(5, 7)); // 12
```

### 7. No Arguments Binding

Regular functions have arguments binding but Arrow functions do not have their own arguments object. So you can use rest parameters.

```javascript
function regularFunction() {
  console.log(arguments); // [1, 2, 3]
}

const arrowFunction = (...args) => {
  console.log(args); // [1, 2, 3]
};

regularFunction(1, 2, 3);
arrowFunction(1, 2, 3);
```

### 8. Arrow Function with Promises and Callbacks

Arrow functions provide better syntax to write promises and callbacks.

```javascript
// with regular function (ES5)
asyncFunction()
  .then(function () {
    return asyncFunction1();
  })
  .then(function () {
    return asyncFunction2();
  })
  .then(function () {
    finish;
  });

// with arrow function (ES6)
asyncFunction()
  .then(() => asyncFunction1())
  .then(() => asyncFunction2())
  .then(() => finish);
```

## When You Should Not Use Arrow Functions

### 1. You should not use arrow functions to create methods inside objects.

```javascript
const person = {
  name: "Jack",
  age: 25,
  sayName: () => {
    // this refers to the global .....
    console.log(this.age);
  },
};

person.sayName(); // undefined
```

### 2. You cannot use an arrow function as a constructor function.

```javascript
const Foo = () => {};
const foo = new Foo(); // TypeError: Foo is not a constructor
```

### 3. You should not use with event handler because its has no binding of this keyword

```javascript
const button = document.getElementById("myButton");

button.addEventListener("click", () => {
  console.log(this); // undefined
});
```

<!-- ### Arrow functions do not have the prototype property. -->


