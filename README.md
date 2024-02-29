# Promise

A **Promise** is a special JavaScript object and used to manage when dealing with multiple asynchronous operations. It provides a cleaner and more flexible way to handle asynchronous operations.

> Benefit of Promises:

- Improves code readability
- Better handling of asynchronous operations
- Provides easy error handling

#### A promise has three states:

1. Pending - The initial state; the promise is neither fulfilled nor rejected.

2. Fulfilled: The operation completed successfully, and the promise has a resulting value.

3. Rejected: The operation failed, and the promise has a reason for the failure.

### Creating Promise

To creare a promise object, we use the **Promise** constructor.

```javascript
const myPromise = new Promise((resolve, reject) => {
  // simulating an asynchronous operation
  setTimeout(() => {
    const success = true;

    if (success) {
      resolve("Operation succeeded!");
    } else {
      reject("Operation failed!");
    }
  }, 1000);
});
```

The **Promise()** constructor takes a function as an arguments. The function also accepts two functions **resolve** and **reject**.

If the promise returns successfully, the **resolve()** function is called. And if an error occurs, the **reject()** function is called.

### Consuming Promise

Promise can be consumed by registering using **then()** and **catch()** methods.

```javascript
myPromise
  .then((result) => {
    console.log("Success:", result);
  })
  .catch((error) => console.log("Error:", error));
```

- then() method used to handle the success case
- catch() method used to handle errors

> Asynchronous operations (tasks) can be such as fetching data from server, reading a file, writing to a file, reading/writing to a database.

## Promise Chaining

Promises are useful when you have to handle more than one asynchronous task, one after another.
This helps improve code readability and avoid the callback hell problem.

```javascript
// Register should call first
function register() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("1 User Register");
      resolve("Register successfully");
    }, 3000);
  });
}

// Send email should call second
function sendEmail() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("2 Send Email");
      resolve("Mail sent successfully");
    }, 1000);
  });
}

// Login user should call third
function login() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("3 Login User");
      resolve("User login successfully");
    }, 2000);
  });
}

// Chaining Promises

register() // consuming with then()...
  .then((result) => {
    console.log("register data----", result);
    return sendEmail();
  })
  .then((result) => {
    console.log("send email data----", result);
    return login();
  })
  .then((result) => {
    console.log("Login data----", result);
  }) // handling error by catch
  .catch((error) => {
    console.error("Error:", error);
  });
```

We can chain promise together using the **then()** method. The **then()** method takes a callback function that will be executed when the Promise is resolved.

We can use the **catch()** method at the end of promise chain to catch any errors that occur in any of the promises in the chain.

## Promise.all()

**Promise.all()** is a method that takes an array of promises as input and return a single promise.
It will wait for all promises in the array to either fulfill or reject.

```javascript
function promise1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise One");
    }, 3000);
  });
}

function promise2() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise Two");
    }, 2000);
  });
}

function promise3() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise Three");
    }, 1000);
  });
}

Promise.all([promise1(), promise2(), promise3()])
  .then((results) => {
    console.log("All promises fulfilled:", results);
  })
  .catch((error) => {
    console.log("One of the promises was rejected:", error);
  });
```

- If all promises are resolved successfully, the **then()** callback is executed with an array with fulfilled values
- If any promise rejects, the **catch()** callback is executed without waiting for the remaining pending promises to resolve.

> Orders of results in the array matches the order of promises.

## Promise.allSettled()

**Promise.allSettled()** is a method that allows you to handle multiple promises concurrently, just like **Promise.all()**, but it waits for all the promises to settle means either resolve or reject before proceeding.

```javascript
function promise1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise One");
    }, 1000);
  });
}

function promise2() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject("Promise Two");
    }, 3000);
  });
}

function promise3() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise Three");
    }, 2000);
  });
}

Promise.allSettled([promise1(), promise2(), promise3()]).then((results) => {
  console.log("All promises settled:", results);
});
```

- Promise.allSettled() always returns array of objects with **status** key which denotes fulfilled or rejected.
- If a promise is fulfilled then you can get response with **value** key and if the promise is rejected then you can find the reason in **reason** key.

```javascript
// Response Output
[
  {
    status: "fulfilled",
    value: "Promise One",
  },
  {
    status: "rejected",
    reason: "Promise Two",
  },
  {
    status: "fulfilled",
    value: "Promise Three",
  },
];
```

## Promise.race()

As the name suggests, **race()** returns first promise with shortest delay whether it is **resolved** or **rejected**.

```javascript
function promise1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 1 resolved");
    }, 5000);
  });
}

function promise2() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 2 resolved");
    }, 3000);
  });
}

function promise3() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 3 resolved");
    }, 2000);
  });
}

Promise.race([promise1(), promise2(), promise3()])
  .then((results) => {
    console.log("First promises resolved:", results);
  })
  .catch((error) => {
    console.log("At least one promise rejected:", error);
  });
```

> This can be useful when you're interested in the result of the first promise to complete, regardless of whether it's a success or failure.

## Promise.any()

**Promise.any()** is somewhat similar to **race()** method but with few minor differences like:

- It will return with first resolved promise.
- If all promises are rejected, it will give you an aggregated error.

```javascript
function promise1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 1 resolved");
    }, 5000);
  });
}

function promise2() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 2 resolved");
    }, 2000);
  });
}

function promise3() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 3 resolved");
    }, 3000);
  });
}

Promise.any([promise1(), promise2(), promise3()])
  .then((results) => {
    console.log("First promises resolved:", results);
  })
  .catch((error) => {
    console.log("At least one promise rejected:", error);
  });
```

```javascript
// Output
First promises resolved: Promise 2 resolved
```

> If you run below code with the promise in shortest delay **Promise 2** of 2000ms is rejected and **promise 3** which has next shortest delay 3000ms then:

- any() will return promise 3 with resolved (because return with first resolved promise).
- race() will return promise 2 with rejected (because return first resolved or rejected promise).

```javascript
function promise1() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 1 resolved");
    }, 5000);
  });
}

function promise2() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject("Promise 2 rejected");
    }, 2000);
  });
}

function promise3() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Promise 3 resolved");
    }, 3000);
  });
}

Promise.any([promise1(), promise2(), promise3()])
  .then((results) => {
    console.log("First promises resolved:", results);
  })
  .catch((error) => {
    console.log("At least one promise rejected:", error);
  });
```

## Promise finally()

This method is always executed whether the promise is resolved or rejected.

```javascript
function myPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = false;

      if (success) {
        resolve("Operation succeeded!");
      } else {
        reject(new Error("Operation failed!"));
      }
    }, 1000);
  });
}

myPromise()
  .then((result) => {
    console.log("Resolved:", result);
  })
  .catch((error) => {
    console.log("Rejected:", error.message);
  })
  .finally(() => {
    console.log("Finally block executed.");
  });
```

> You can use **finally** method after resolved or rejected, like want to stop loader after api call or other scenario.

## APIs Calling with Promise

The Fetch API is a modern and native JavaScript API for making network requests, and it returns promises.

```javascript
function fetchData() {
  return fetch("https://jsonplaceholder.typicode.com/users");
}

fetchData()
  .then((res) => res.json())
  .then((result) => console.log(result))
  .catch((error) => {
    console.error("Error:", error);
  });
```

## Promise vs Callback

Both promises and callbacks are used to handle asynchronous operation in JavaScript, but they differ in their syntax, structure and how they manage asynchronous code.

**Callbacks** are functions that are passed as arguments to another function and are executed after the completion of an asynchronous operation. They hava been a traditional way of handling asynchronous code in JavaScript.

**Promises** provides a cleaner and more structured way to handle asynchronous operations compared to callbacks. A promise represents a value that might be available now, or in the future, or never. It has three states: pending, fulfilled or rejected.
