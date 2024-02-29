# Default Parameters

**Default parameters** allow you to assign default values to function parameters in case the values are not provided or are undefined. This feature was introduced in ECMAScript 6 (ES6).

### 1. To Define Default Parameters

Simply assign default value to the parameter in the function definition, if no arguments passed then its callled default values.

```javascript
function greet(name = "Guest", greeting = "Hello") {
  console.log(`${greeting}, ${name}!`);
}

greet(); // Outputs: Hello, Guest!
greet("John"); // Outputs: Hello, John!
greet("Dev", "Hi"); // Outputs: Hi, Dev!
```

```javascript
function sum(x = 3, y = 5) {
  return x + y;
}

console.log(sum(5, 15)); // Outputs: 20
console.log(sum(7)); // Outputs: 12
console.log(sum()); // Outputs: 8
```

```javascript
function multiply(a, b = 2 * a) {
  return a * b;
}

console.log(multiply(5)); // Outputs: 50
console.log(multiply(5, 3)); // Outputs: 15
```

```javascript
function sum(x = 1, y = x, z = x + y) {
  console.log(x + y + z);
}

sum(); // Outputs: 4
```

> When we passed arguments, default parameters values overrides.

### 2. Passing undefined Value

When you pass **undefined** to a default parameter function, the function takes the default value.

```javascript
function myFunc(x = 1) {
  console.log(x);
}

myFunc(10); // Outputs: 10
myFunc(undefined); // Outputs: 1
myFunc(null); // Outputs: null
myFunc(""); // Outputs:
```

> Both null and empty strings are considered valid values for the function.

### 3. Evaluating default parameters at call time

```javascript
function combine(value, array = []) {
  array.push(value);
  return array;
}
console.log(combine(1)); // Outputs: [1]
console.log(combine(2)); // Outputs: [2], not [1, 2]
```

The function called two times but it's give new updated value [2] and not [1,2].

### 4. Passing Function Value as Default Value

You can use a function in default value expression.

```javascript
const sum = () => 15;

const calculate = function (x, y = x * sum()) {
  return x + y;
};

console.log(calculate(10)); // Outputs: 160
```

> **Warning**
> If you reference the parameter that has not been initialized yet, you will get an error.

```javascript
function sum(x = y, y = 1) {
  console.log(x + y);
}

sum(10); // Outputs: 11
```

```javascript
function sum(y = 1, x = y) {
  console.log(x + y);
}

sum(); // Outputs: 2
```

```javascript
function sum(x = y, y = 1) {
  console.log(x + y);
}

sum(); // ReferenceError: Cannot access 'y' before initialization
```

## Arguments vs. Parameters

The **parameters** and **arguments** in a function are both different.

Function parameters are the values that are passed in the definition of the function, whereas function arguments are the real values that are passed in the function.
