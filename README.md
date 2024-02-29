# Async/Await

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

> **Await** can only be used within an async function otherwise give an error.

### 1. Multiple Asynchronous Operation (Parallel Execution)

We use multile asynchronous operation using **await** keyword. await wait for each promise to be complate.

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Promise 1");
  }, 10000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Promise 2");
  }, 1000);
});

async function handleMultiplePromise() {
  const result1 = await promise1;
  const result2 = await promise2;

  //wait for each promise to be complate
  console.log(result1); // Promise 2
  console.log(result2); // Promise 1
}

handleMultiplePromise();
```

### 2. Fetching API Data

```javascript
async function fetchApi() {
  const result = await fetch("https://jsonplaceholder.typicode.com/users");
  const res = result.json();
  console.log(res);
}

fetchApi(); // // (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```

### 3. Error Handling

To handle errors in asynchronous functions, you can use **try** and **catch** blocks, similar to synchronous code.

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Promise resolved");
  }, 4000);
});

async function asynFunc() {
  try {
    // wait until the promise resolves
    const result = await myPromise;

    console.log(result);
  } catch (error) {
    console.log(error);
  }
}

asynFunc(); // Promise resolved
```

> If any promise inside the **async** function is rejected, the control will jump to the **catch** block.

**async/await** is widely used especially in dealing with asynchronous operations such as

- Making API calls,
- Reading/Writing files,
- Interacting with databases.
