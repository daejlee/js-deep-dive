# Chapter 14: Global Variables and Their Issues

---

## 1. Variable Lifecycle

### 1.1 Local Variable Lifecycle

- Created when function is called
- Initialized to `undefined`
- Assigned a value when reached in code
- Destroyed when function execution ends

```javascript
function myFunc() {
  var localVar = 10; // localVar is created
  // localVar is destroyed when myFunc ends
}

myFunc(); // localVar is created and destroyed within myFunc
console.log(localVar); // ReferenceError: localVar is not defined
```

### 1.2 Global Variable Lifecycle

- Created when declared
- Automatically become properties of the global object (window in browsers)
- Exist for the entire runtime of the program

---

## 2. Problems with Global Variables

### 2.1 Implicit Coupling

- Can be accessed and modified from anywhere in the code
- Leads to unintended side effects and harder debugging

### 2.2 Long Lifecycle

- Consume memory for the entire program runtime
- Increased risk of accidental modification

### 2.3 Namespace Pollution

- Risk of naming conflicts, especially in large projects
- Different scripts can overwrite each other's global variables

---

## 3. Minimizing Global Variable Usage

### 3.1 Use Immediately Invoked Function Expressions (IIFE)

```javascript
(function() {
  var localVar = 10;
  // Code here
})();
```

### 3.2 Namespace Pattern

```javascript
var MYAPP = MYAPP || {}; // This will be the global namespace object
MYAPP.module1 = {
  data: [],
  func: function() {}
};
```

### 3.3 Module Pattern

```javascript
var module = (function() {
  var privateVar = 0;
  return {
    increment: function() {
      privateVar++;
      return privateVar;
    },
    decrement: function() {
      privateVar--;
      return privateVar;
    }
  };
})();

console.log(module.privateVar); // undefined
console.log(module.increment()); // 1
console.log(module.decrement()); // 0
```

### 3.4 ES6 Modules

By using ES6 modules, you can avoid global variables altogether.
