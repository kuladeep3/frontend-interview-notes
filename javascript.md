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
