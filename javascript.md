# JavaScript Interview Questions and Answers

### What is hoisting?

**Hoisting** is a JavaScript mechanism where variable and function declarations are moved to the top of their containing scope during the compilation phase.  
This means you can use variables and functions before declaring them in your code. However, only declarations are hoisted, not initializations.

For example:

```javascript
console.log(a); // undefined
var a = 5;

// Function hoisting
hoistedFunction(); // 'This function is hoisted'

function hoistedFunction() {
  console.log("This function is hoisted");
}
```

In the example above, the variable `a` is hoisted (declared at the top) but not its assignment, so it is `undefined` until initialized. Function declarations are fully hoisted, allowing them to be called before they appear in the code.

---

### What is Implicit Type Coercion?

**Implicit Type Coercion** is a feature in JavaScript where the language automatically converts values from one type to another when performing operations. This can lead to unexpected results if not properly understood.

For example:

```javascript
console.log(5 + "5"); // "55"
console.log(5 - "2"); // 3
console.log(true + 1); // 2
```

In the first case, the number `5` is coerced into a string, resulting in string concatenation. In the second case, the string `"2"` is coerced into a number, allowing for subtraction. In the third case, the boolean `true` is coerced into the number `1`.

While implicit type coercion can make code more concise, it can also introduce bugs if developers are not aware of how JavaScript handles type conversion.

---

### What are closures in JavaScript?

A **closure** in JavaScript is a function that retains access to its lexical scope, even when the function is executed outside that scope. This means that a closure can "remember" the environment in which it was created.
For example:

```javascript
function outerFunction(outerVariable) {
  return function innerFunction(innerVariable) {
    console.log("Outer Variable: " + outerVariable);
    console.log("Inner Variable: " + innerVariable);
  };
}
const newFunction = outerFunction("outside");
newFunction("inside");
```

In this example, `innerFunction` is a closure that has access to `outerVariable` from its parent scope, even after `outerFunction` has finished executing. When `newFunction` is called, it can still access `outerVariable` and log its value.

---

### What is currying in JavaScript?

**Currying** is a functional programming technique in JavaScript where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument. This allows for partial application of functions, enabling you to create specialized functions by fixing some arguments.
For example:

```javascript
function add(a) {
  return function (b) {
    return a + b;
  };
}
const addFive = add(5);
console.log(addFive(3)); // 8
```

In this example, the `add` function takes one argument `a` and returns another function that takes the second argument `b`. The returned function can then access `a` and add it to `b`. By calling `add(5)`, we create a new function `addFive` that adds `5` to its argument.

---

### What is the difference between `event.preventDefault()` and `event.stopPropagation()`?

- `event.preventDefault()` is used to stop the browser's default action for an event. For example, clicking a link normally navigates to a new page; calling preventDefault() on the click event handler prevents that navigation. This is useful for actions like stopping form submissions, preventing link navigation, or halting other default browser behaviors, but it does not affect event propagation to parent elements.

- `event.stopPropagation()` stops the event from bubbling up to parent elements in the DOM hierarchy. This means the event handler for the current element runs, but any event handlers on parent elements that would have responded to the same event won't be triggered. However, it does not prevent the default browser action (such as navigation or form submission).

```javascript
document.getElementById("myButton").addEventListener("click", function (event) {
  event.preventDefault(); // Prevent default action
  event.stopPropagation(); // Stop event from bubbling
});
```

In this example, clicking the button will not submit a form (if it's inside one) and will not trigger any click event listeners on parent elements.

---

### What is a promise in JavaScript?

A **promise** in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a way to handle asynchronous operations more gracefully than traditional callback functions, allowing for better readability and error handling.
A promise can be in one of three states:

1. **Pending**: The initial state, neither fulfilled nor rejected.
2. **Fulfilled**: The operation completed successfully, and the promise has a resulting value.
3. **Rejected**: The operation failed, and the promise has a reason for the failure.
   Here's an example of creating and using a promise:

```javascript
const myPromise = new Promise((resolve, reject) => {
  const success = true; // Simulate an asynchronous operation
  setTimeout(() => {
    if (success) {
      resolve("Operation completed successfully!");
    } else {
      reject("Operation failed.");
    }
  }, 1000);
});
```

```javascript
myPromise
  .then((message) => {
    console.log(message); // "Operation completed successfully!"
  })
  .catch((error) => {
    console.error(error); // "Operation failed."
  });
```

In this example, we create a promise that simulates an asynchronous operation using `setTimeout`. If the operation is successful, we call `resolve`, otherwise we call `reject`. We then handle the fulfilled and rejected states using `.then()` and `.catch()`.

---

### Promise methods

- `Promise.all()`
- `Promise.allSettled`
- `Promise.any()`
- `Promise.race()`

```