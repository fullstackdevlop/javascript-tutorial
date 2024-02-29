# Rest Parameters

The **rest parameters** is an improved way to handle function parameters.

The **rest parameters** allows us to represent an indefinite number of arguments as an array. By using the rest parameters, a function can be called with any number of arguments.

- The rest parameter is prefixed with **three dots (...)** followed by the parameter name.
- It has to be the **last argument** because it is used to collect all of the remaining elements into an array.
- Before ES6, the **arguments object** of the function was used.

### 1. Using Rest Parameters

Function can accept any number of arguments using the rest parameter **...args**

```javascript
function myFunc(a, b, ...rest) {
  console.log(a); // Outputs: 1
  console.log(b); // Outputs: 2

  // remaining arguments values as an array
  console.log(rest); // Outputs: [3, 4, 5, 6, 7, 8, 9, 10]
}

myFunc(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```

```javascript
function sum(...numbers) {
  console.log(numbers); // Outputs: [1, 2, 3, 4, 5]

  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

> **Note:**
> The **rest parameter** has to be the last argument, as its job is to collect all the remaining arguments into an array, and a function can only have one rest parameter.

```javascript
function logInfo(name, age, ...hobbies) {
  console.log(`${name} is ${age} years old and like ${hobbies.join(", ")}`);
}

logInfo("John", 30, "reading", "traveling", "coding"); // Outputs: John is 30 years old and like reading, traveling, coding
```

```javascript
function fun(...input) {
  let sum = 0;
  for (let i of input) {
    sum += i;
  }
  return sum;
}
console.log(fun(1, 2)); // Outputs: 3
console.log(fun(1, 2, 3)); // Outputs:6
console.log(fun(1, 2, 3, 4, 5)); // Outputs: 15
```

## Difference between Rest Parameter and arguments object

The rest parameter and arguments object are different from each other.

- The arguments object is an array-like (but not array), while the rest parameters are array instances.

- The arguments object does not include methods such as sort, map, forEach, or pop, but these methods can be directly used in rest parameters.

## Rest Parameters vs. Spread Operator

Although the syntax of the **rest parameter** is similar to the **spread operator**, but rest parameter is entirely opposite from the spread operator.

- The **rest parameter** is used in function declarations to gather arguments into an array, while the **spread operator** is used in array or object literals to spread (unpack) elements or properties.

- Despite the similar syntax, they have different use cases and functionalities.
