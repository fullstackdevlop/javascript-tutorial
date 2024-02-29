# Spread Operator

The **spread operator (...)** is used to expand or spread elements of an iterable like array, object, string and function.

It is a very simple and powerful feature that helps us to write nicer & shorter code, which is denoted by three dots(...).

There are different uses of spread operator with array, object, string and functions:

## Spread Operator with Arrays

### 1. Copying Arrays

By using the **spread operator** we make sure that the original array is not affected whenever we alter the new array.

```javascript
❌❌❌
// Copying without the spread operator
const arr = ["a", "b", "c"];
const arr2 = arr;

arr2.push("d");

console.log(arr2); // Outputs: ['a', 'b', 'c', 'd']
console.log(arr); // Outputs: ['a', 'b', 'c', 'd']
```

```javascript
✅✅✅
// Copying with the spread operator (...)
const arr = ["a", "b", "c"];
const arr2 = [...arr];

arr2.push("d");

console.log(arr2); // Outputs: ['a', 'b', 'c', 'd']
console.log(arr); // Outputs: ['a', 'b', 'c']
```

### 2. Concatenating (combining) or Merging Arrays

We can merge two arrays with **spread operator**, not need to use **concat** method.

```javascript
let array1 = [1, 2, 3];
let array2 = [4, 5, 6];

array1 = array1.concat(array2);
console.log(array1); // Outputs: [1, 2, 3, 4, 5, 6]
```

```javascript
let array1 = [1, 2, 3];
let array2 = [4, 5, 6];

let mergedArray = [...array1, ...array2];
console.log(mergedArray); // Outputs: [1, 2, 3, 4, 5, 6]
```

### 3. Adding New Element to an Array (or expand an array)

Whenever we want to expand or add new element an array into another array we use **spread operator**.

```javascript
const originalArray = [1, 2, 3];
const newArray = [0, ...originalArray, 4];

console.log(newArray); // Outputs: [0, 1, 2, 3, 4]
```

### 4. Converting NodeList to Array

To convert DOM list into an array we use spread operator (...) inside new array.

```javascript
const nodeList = document.querySelectorAll("p");
console.log(nodeList); // Outputs: NodeList(5) [p, p, p, p, p]

const arrayOfParagraph = [...nodeList];
console.log(arrayOfParagraph); // Outputs: [p, p, p, p, p]
```

### 5. Creating a Shallow Copy of an Object with Array Property:

```javascript
const originalObject = { name: "John", hobbies: ["reading", "coding"] };

// copyObject is a shallow copy of originalObject with array property
const copyObject = { ...originalObject };
```

### 6. Eliminate Duplicates from an Array

You can use the **spread operator** along with the **Set** data structure to eliminate duplicates from an array.

```javascript
const arrayWithDuplicates = [1, 2, 3, 4, 2, 4, 5, 1, 3];

const arrayWithoutDuplicates = [...new Set(arrayWithDuplicates)];

console.log(arrayWithoutDuplicates); // Outputs: [1, 2, 3, 4, 5]
```

### 7. Array Destructuring

Array destructuring used with spread operator for collect remaining elements into a seprate array.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Using spread operator in array destructuring
const [first, second, ...rest] = numbers;

console.log(first); // 1
console.log(second); // 2
console.log(rest); // [3, 4, 5]
```

### 8. Mathematical Operations

The **spread operator (...)** can be used with the **Math object** to apply various mathematical operations to an array of values.

```javascript
const numbers = [1, 2, 3, 4, 5];

const maxNumber = Math.max(...numbers);
const minNumber = Math.min(...numbers);

console.log(maxNumber); // Outputs: 5
console.log(minNumber); // Outputs: 1
```

## Spread Operator with Objects

### 1. Copying Objects

By using the **spread operator** we make sure that the original object is not affected whenever we alter the new object.

```javascript
❌❌❌
// Copying without the spread operator
const originalObject = {
  name: "John",
  age: 25,
};

const copiedObject = originalObject;

copiedObject.phone = 12345678;

console.log(copiedObject); // Outputs: {name: 'John', age: 25, phone: 12345678}
console.log(originalObject); // Outputs: {name: 'John', age: 25, phone: 12345678}
```

```javascript
✅✅✅
// Copying with the spread operator
const originalObject = {
  name: "John",
  age: 25,
};

const copiedObject = { ...originalObject };

copiedObject.phone = 12345678;

console.log(copiedObject); // Outputs: {name: 'John', age: 25, phone: 12345678}
console.log(originalObject); // Outputs: {name: 'John', age: 25}
```

### 2. Concatenating (combining) or Merging Objects

We can merge two Objects with **spread operator**, Its just a shorthand for the **Object.assign()**.

```javascript
// Combine Object with Object.assign() method
const object1 = { food: "pizza", car: "ford" };
const object2 = { animal: "dog" };

const combinedObject = Object.assign({}, object1, object2);

console.log(combinedObject); // Ouputs: {food: 'pizza', car: 'ford', animal: 'dog'}
```

```javascript
// Combine Object with spread operator
const object1 = { food: "pizza", car: "ford" };
const object2 = { animal: "dog" };

const combinedObject = { ...object1, ...object2 };

console.log(combinedObject); // Ouputs: {food: 'pizza', car: 'ford', animal: 'dog'}
```

> Existing property name will be overrides.

### 2. Adding Object Properties

You can add new properties to an existing object by spread operator.

```javascript
// Without spread operator
const person = {
  name: "John",
  lastName: "Doe",
};

person.age = 25;
person["eyecolor"] = "blue";

// Outputs: {name: 'John', lastName: 'Doe', age: 25, eyecolor: 'blue'}
console.log(person);
```

```javascript
✅✅✅
// With spread operator
const person = {
  name: "John",
  lastName: "Doe",
};

const newPerson = { ...person, age: 25, eyecolor: "blue" };

// Outputs: {name: 'John', lastName: 'Doe', age: 25, eyecolor: 'blue'}
console.log(newPerson);
```

### 3. Overriding Object Properties

You can modify existing object property value with spread operator, not need to use outdated **Object.defineProperty()** or the **Object.assign()**.

```javascript
const animal = {
  name: "Horse",
  age: 10,
  color: "black",
};

// Outputs: {name: 'Horse', age: 10, color: 'black'}
console.log(animal);

// Outputs: {name: 'Horse', age: 10, color: 'red'}
console.log(Object.defineProperty(animal, "color", { value: "red" }));

// Outputs: {name: 'Horse', age: 10, color: 'white'}
console.log(Object.assign({}, animal, { color: "white" }));

✅✅✅
// Outputs: {name: 'Horse', age: 10, color: 'gray'}
console.log({ ...animal, color: "gray" });
```

### 4. Destructuring Object

Object destructuring used with spread operator for collect remaining elements into a seprate object.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  city: "New York",
};

// Selective destructuring using spread operator
const { firstName, lastName, ...restInfo } = person;

console.log(firstName); // Outputs: 'John'
console.log(lastName); // Outputs: 'Doe'
console.log(restInfo); // Outputs: { age: 30, city: 'New York' }
```

## Spread Operator with Function Arguments

### 1. Passing an Array as Arguments

Spread operator can be used with function arguments as array elements.

```javascript
function sum(...numbers) {
  console.log(numbers); // Outputs: [1, 2, 3, 4, 5]

  return numbers.reduce((total, num) => total + num, 0);
}

const numbers = [1, 2, 3, 4, 5];
console.log(sum(...numbers)); // Outputs: 15
```

## Spread Operator with Strings

### 1. Split the String into an Array

Spread operator is used to convert the string into array.

```javascript
const str = "Hello";
const charArray = [...str];

console.log(charArray); // Outputs: ['H', 'e', 'l', 'l', 'o']
```

### 2. Concatenating Strings

Spread operator is used to spread the characters of str1 and str2 into an array, and then join('') is used to concatenate them back into a single string

```javascript
const str1 = "Hello";
const str2 = "World";
const combinedString = [...str1, " ", ...str2].join("");

console.log(combinedString); // Outputs: 'Hello World'
```
