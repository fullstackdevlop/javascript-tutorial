# Callback Function

A **callback** is a function passed as an argument to another function. Its fundamental concept in JavaScript, especially when dealing with asynchronous code or events.

> The benefit of using a callback function is that you can wait for the result of a previous function call and then execute another function call.

### 1. Example

```javascript
let members = ["John", "Sam", "Allie "];

function addNewMember(newMember, callback) {
  setTimeout(() => {
    members.push(newMember);
    callback(newMember);
  }, 3000);
}

function getAllmembers(name) {
  console.log(members);
  console.log("New member is " + name);
}

addNewMember("Ajay", getAllmembers);
```

### 2. Example

```javascript
function doSomething(callback) {
  setTimeout(() => {
    console.log("Async operation completed!");
    callback();
  }, 2000);
}

function onComplete() {
  console.log("Callback executed!");
}

doSomething(onComplete);
```

### 3. Callbacks in Asynchronous JavaScript

```javascript
function getData(onSuccess, onError) {
  setTimeout(function () {
    const data = { name: "User" };

    const error = Math.random() > 0.6;

    console.log(error); // check conditions

    if (error) {
      onSuccess(data);
    } else {
      onError("Error fetching data");
    }
  }, 2000);
}

function handleSuccess(data) {
  console.log("Data:", data);
}

function handleError(error) {
  console.log("Error:", error);
}

getData(handleSuccess, handleError);
```

### 4. Callbacks in Fetching Data

```javascript
function fetchData(url, onSuccess, onError) {
  fetch(url)
    .then((res) => {
      return res.json();
    })
    .then((data) => {
      onSuccess(data);
    })
    .catch((error) => {
      onError(error.message);
    });
}

function handleSuccess(data) {
  console.log("Data:", data);
}

function handleError(error) {
  console.log("Error:", error);
}

fetchData(
  "https://jsonplaceholder.typicode.com/users",
  handleSuccess,
  handleError
);
```

## Callback Hell

**Callback hell** occurs when you have multiple nested callback functions, Its making the code difficult to read, understand, and maintain. Error handling also may be hard to manage.

```javascript
/**

* 1. Register
* 2. Send welcome mail
* 3. Login
* 4. Get user data
* 5. Display user data
*/

function register(callback) {
  setTimeout(() => {
    console.log("1-Register end");
    callback();
  }, 3000);
}

function sendEmail(callback) {
  setTimeout(() => {
    console.log("2-Send Email");
    callback();
  }, 4000);
}

function login(callback) {
  setTimeout(() => {
    console.log("3-Login ");
    callback();
  }, 2000);
}

function getUserData(callback) {
  setTimeout(() => {
    console.log("4-Get User Data");
    callback();
  }, 5000);
}

function displayUserData() {
  console.log("5-Display user data");
}

// Callback Hell
register(function () {
  sendEmail(function () {
    login(function () {
      getUserData(function () {
        displayUserData();
      });
    });
  });
});

console.log("Other application works!");
```
