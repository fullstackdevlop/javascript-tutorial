# Template Literals (Template Strings)

Template literals provide an easy way to create strings, especially when you need to include dynamic content or multiline text. The method is called string interpolation.

- Template literals are enclosed in backticks (``) character.
- It was introduced in ES6.

> There are some uses of template literals such as:

### 1. Template Literals for Strings

With **template literals**, you can use both single ('') and double quote ("") inside a string.

```javascript
const text = `I am learning "JavaScript"`;

console.log(text);
```

### 2. Multiline Strings

**Template literals** also make it easy to write multiline strings.

```javascript
// using es5 with the + operator
const message1 =
  "This is a long message\n" +
  "that spans across multiple lines\n" +
  "in the code.";
console.log(message1);

// using es6 with template literals
const message1 = `This is a long message
that spans across multiple lines
in the code.`;

console.log(message1);
```

### 3. Expression Interpolation

With template literals, it's a bit easier to include variables and expressions inside a string. For this we use the **${...}** syntax.

Before ES6, we use the + operator to concatenate variables and expressions in a string.

```javascript
// using es5 with the + operator
const name = "Jack";
console.log("Hello " + name); // Hello Jack

// using es5 with the + operator
const name = "Jack";
console.log(`Hello ${name}`);

const num = 9;
console.log(`${num < 10 ? "Too Low" : "Very high"}`); // Too Low
```

### 4. Tagged Templates

Tagged template literals allow us to parse template literals with a function. The first argument of the tag function contains an array having string values, and the remaining arguments are related to the expression.

```javascript
const x = 10;
const y = 20;

function customTag(strings, ...values) {
  // Process the strings and values as needed

  console.log(strings); // ['This is ', ' and ', '',]

  console.log(values); //  [10, 20]

  // Return the final string
  return "Processed string!";
}

const taggedResult = customTag`This is ${x} and ${y}`;

console.log(taggedResult);
```

> Template literals are widely used in modern JavaScript for cleaner and more readable string formatting.
