# Object Literals

The **object literals** is one of the short form for creating an object in JavaScript.

- Define an object in the **curly braces {}** with key:value pairs separated by a comma.
- The key would be the name of the property and the value will be a literal value or a function (method).
- Properties can be accessed using dot notation or bracket notation.

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

**object literal** more powerful by extending the syntax in some ways like.

### 1. Object Property Shorthand

You can use shorthand property names when the variable name matches the property name.

```javascript
const name = "Alice";
const age = 25;

// Old way to assign value
const obj = {
  name: name,
  age: age,
};

// Object property shorthand
const obj = {
  name,
  age,
};

console.log(obj); // Outputs: {name: 'Alice', age: 25}
```

```javascript
// Old way when function return object
function createMachine(name, status) {
  return {
    name: name,
    status: status,
  };
}

// New way when function return object
function createMachine(name, status) {
  return {
    name,
    status,
  };
}
```

### 2. Short Method Syntax

Before ES6 we use colon(:) and the function keyword with method in object.

But now object literal provide shorter syntax for creating method. This shorthand syntax is also known as the concise method syntax.

```javascript
// Old way for creating method in object
const server = {
  name: "Server",
  restart: function () {
    console.log(`The ${this.name} is restarting...`);
  },
};

server.restart();
// Or
server["restart"]();
```

```javascript
// New way for creating method in object
const server = {
  name: "Server",
  restart() {
    console.log(`The ${this.name} is restarting...`);
  },
  "starting up"() {
    console.log("The " + this.name + " is starting up!");
  },
};

server.restart(); // Or server["restart"]();

server["starting up"]();
```

> It’s valid to have spaces in the property name. The method 'starting up' has spaces in its name. To call the method, you use the following syntax:

```javascript
object_name["property name"]();
```

```javascript
const name = "Alice";
const age = 25;

const user = {
  name,
  age,
  greet() {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old.`
    );
  },
};

user.greet(); // Outputs: Hello, my name is Alice and I'm 25 years old.
```

### 3. Use Variable as a Property Name

The **square brackets ([])** allow you to use the string literals and variables as the property names.

```javascript
const n = "name";

const obj = {
  [n]: "Dev",
  course: "Btech",
};

console.log(obj); // Outputs: {name: 'Dev', course: 'Btech'}
console.log(obj.name); // Outputs: Dev
```

### 4. Computed Property Names (ES6+)

You can also use computed property names

```javascript
const dynamicKey = "color";

const n = "company";

const car = {
  brand: "Toyota",
  [dynamicKey]: "blue",
  [n + "name"]: "TATA",
  ["number of wheels"]: 4,
};

console.log(car.color); // Outputs: blue
console.log(car.companyname); // Outputs: TATA
console.log(car["number of wheels"]); // Outputs: 4
```

### 5. Object Destructuring (ES6+)

Object destructuring allows you to extract properties from objects and assign them to variables.

```javascript
const person = {
  course: "JavaScript",
  technplogy: "Web Development",
};

const { course, technplogy } = person;

console.log(course, technplogy); // Outputs: JavaScript Web Development
```
