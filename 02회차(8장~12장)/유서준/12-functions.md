# Chapter 12: Functions

---

## 1. What is a Function?

- Functions are a core concept in JavaScript
- They are related to other important concepts like scope, execution context, closures, object creation, methods, this, prototypes, and modularity
- Functions in programming are similar to mathematical functions:
  - Take input
  - Perform operations
  - Produce output

---

## 2. Why Use Functions?

- Enable code reuse
- Improve maintainability
- Enhance readability
- Reduce errors through centralized logic

---

## 3. Function Literals

- Functions are object-type values in JavaScript
- Can be created using function literals
- Components: `function` keyword, name (optional, if omitted it's an anonymous function), parameter list, and function body

```javascript
// function: function keyword
// add: function name
// x, y: parameters
// { return x + y; }: function body
var f = function add(x, y) {
  return x + y;
};
```

---

## 4. Function Definition Methods

1. Function Declaration
2. Function Expression
3. Function Constructor
4. Arrow Function (ES6)

### 4.1 Declaration

```javascript
function add(x, y) {
  return x + y;
}

console.log(add(2, 3)); // 5
```

- Hoisted to the top of their scope
- Can be named or anonymous
  - Named: `function add() {}`
  - Anonymous: `function() {}` but it should be assigned to a variable

### 4.2 Function Expression

```javascript
var add = function(x, y) {
  return x + y;
};

console.log(add(2, 3)); // 5
```

```javascript
var add = function sum(x, y) {
  return x + y;
};

console.log(add(2, 3)); // 5
console.log(sum(2, 3)); // ReferenceError: sum is not defined
```

- Not hoisted
- Can be anonymous or named

### 4.3 Function Creation Timing and Hoisting

- Function declarations are processed before code execution
- Function expressions are processed during code execution
- Recommended to use function expressions for better code organization

```javascript
// Function declaration
function foo() {
  console.log('foo');
}();

// Function expression: recommended
var bar = function() {
  console.log('bar');
}();
```

### 4.4 Function Constructor

```javascript
var add = new Function('x', 'y', 'return x + y');
```

- Not recommended for general use
- Doesn't create closures to their creation contexts

### 4.5 Arrow Function

```javascript
const add = (x, y) => x + y;
```

- Introduced in ES6
- More concise syntax
- Different behavior for `this` binding

---

## 5. Function Invocation

- Called using the function name and parentheses
- Arguments are passed inside the parentheses

### 5.1 Parameters and Arguments

- Parameters are variables listed in function definition
- Arguments are values passed to the function when called
- JavaScript doesn't check the number of arguments passed

### 5.2 Argument Checking

- JavaScript doesn't enforce type checking for arguments
- When a function is called with fewer arguments than defined, the missing parameters are set to `undefined`
- When a function is called with more arguments than defined, the extra arguments are ignored
- It's good practice to check argument types and provide default values

```javascript
function add(x, y) {
  if (typeof x !== 'number' || typeof y !== 'number') {
    throw new TypeError('x and y must be numbers');
  }

  return x + y;
}

console.log(add(2, 3)); // 5
console.log(add('2', 3)); // TypeError: x and y must be numbers
```

### 5.3 Maximum Number of Parameters

- No strict limit, but it's recommended to keep the number of parameters low (ideally 3 or fewer)
- Use an object for multiple parameters if needed\

### 5.4 Return Statement

- Used to specify the value returned by the function
- Can also be used to exit the function early
- If no return statement is present, the function returns `undefined`

---

## 6. Call-by-Value vs Call-by-Reference

- Primitives are passed by value
- Objects are passed by reference
- Modifying objects inside functions can have side effects

---

## 7. Various Function Forms

### 7.1 Immediately Invoked Function Expression (IIFE)

```javascript
(function() {
  // code
})();
```

### 7.2 Recursive Functions

- Functions that call themselves
- Useful for tasks that can be broken down into similar subtasks
- Warning: can lead to stack overflow if not properly implemented
- Best practice
  - Have a base case to stop the recursion
  - Ensure the base case is reached
  - Use loops for simpler tasks

```javascript
function factorial(n) {
  if (n <= 1) {
    return 1;
  }

  return n * factorial(n - 1); // recursive call
}

console.log(factorial(5)); // 120
```

### 7.3 Nested Functions

- Functions defined inside other functions
- Have access to outer function's variables
- Why use nested functions?
  - Encapsulation
  - Code organization
  - Information hiding
  - Closures (covered later)

```javascript
function outer() {
  var x = 10;

  function inner() {
    console.log(x);
  }

  inner();
}

outer(); // 10
```

### 7.4 Callback Functions

- Functions passed as arguments to other functions
- Used in asynchronous operations, event handling, and functional programming

```javascript
function add(x, y) {
  return x + y;
}

function subtract(x, y) {
  return x - y;
}

function calculate(x, y, operation) {
  return operation(x, y);
}

console.log(calculate(2, 3, add)); // 5
console.log(calculate(2, 3, subtract)); // -1
```

### 7.5 Pure Functions and Impure Functions

- Pure functions always return the same output for given inputs and have no side effects
- Impure functions may depend on or modify external state

```javascript
// Pure function
function add(x, y) {
  return x + y;
}

// Impure function
var sum = 0;

function add(x) {
  sum += x; // modifies external state
  return sum;
}
```
