# callbacks-and-promises

Got it — I’ll explain this in a **very simple, interview-friendly way** with clear examples 👇

---

# 1) Callbacks (basic idea)

👉 A **callback** is just a function passed into another function to run later.

### Simple example:

```js
function greet(name, callback) {
    console.log("Hi " + name);
    callback();
}

function sayBye() {
    console.log("Bye!");
}

greet("Ruheena", sayBye);
```

👉 Output:

```
Hi Ruheena
Bye!
```

✔ Here `sayBye` is the callback

---

### Real-world async example:

```js
setTimeout(() => {
    console.log("Data fetched");
}, 2000);
```

👉 Runs after 2 seconds
✔ `setTimeout` uses a callback

---

### ❌ Problem: Callback Hell

```js
setTimeout(() => {
    console.log("Step 1");
    setTimeout(() => {
        console.log("Step 2");
        setTimeout(() => {
            console.log("Step 3");
        }, 1000);
    }, 1000);
}, 1000);
```

👉 Hard to read 😵 → this is **callback hell**

---

# 2) Promises (solution to callback hell)

👉 A **Promise** represents a future result
States:

* pending
* resolved (success)
* rejected (error)

---

### Example:

```js
const myPromise = new Promise((resolve, reject) => {
    let success = true;

    if (success) {
        resolve("Data received");
    } else {
        reject("Error occurred");
    }
});
```

---

### Using `.then()` and `.catch()`:

```js
myPromise
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log(error);
    });
```

---

### Async example:

```js
function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data fetched");
        }, 2000);
    });
}

fetchData().then((data) => console.log(data));
```

---

# 3) Async/Await (cleanest way)

👉 Built on top of promises
👉 Makes async code look like normal synchronous code

---

### Same example using async/await:

```js
function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data fetched");
        }, 2000);
    });
}

async function getData() {
    const data = await fetchData();
    console.log(data);
}

getData();
```

---

### Handling errors:

```js
async function getData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
```

---

# 🔥 Simple analogy (VERY IMPORTANT)

Think of ordering food 🍕

### Callbacks:

👉 “Call me when food is ready”

### Promises:

👉 “I give you a receipt (promise) → food will come later”

### Async/Await:

👉 “I’ll wait here until food comes” (clean & simple)

---

# ⚡ Final comparison

| Concept     | Syntax style      | Problem               |
| ----------- | ----------------- | --------------------- |
| Callbacks   | nested functions  | messy (callback hell) |
| Promises    | `.then()`         | better but chaining   |
| Async/Await | looks synchronous | cleanest ✅            |

---

# 💡 Interview one-liner answers

* Callback → function passed to run later
* Promise → handles async operations with success/failure
* Async/Await → cleaner way to write promises


