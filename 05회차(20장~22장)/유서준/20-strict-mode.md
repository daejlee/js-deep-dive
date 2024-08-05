# Chapter 20: Strict Mode

---

## 1. Introduction to Strict Mode

- Introduced in ES5 to catch common coding errors and "unsafe" actions
- Helps create more robust code by enforcing stricter parsing and error handling
- But, let's use Other tools like ESLint 🤓

---

## 2. Enabling Strict Mode

### 2.1 Global Scope

```javascript
'use strict';
// Code here runs in strict mode
```

### 2.2 Function Scope

```javascript
function strictFunction() {
  'use strict';
  // This function runs in strict mode
}
```

  ---

## 3. Best Practices for Applying Strict Mode

- Apply strict mode to individual scripts or functions
- Some libraries may not work with strict mode. Therefore, if you want to use strict mode as global, wrap your code in an IIFE(Immediately Invoked Function Expression)
- Avoid using strict mode in function scope. It can lead to unexpected behavior

```javascript
(function() {
  'use strict';
  // Your entire script here
})();
```

---

## 4. Common Strict Mode Errors

### 4.1 Implicit Globals

```javascript
'use strict';
x = 10; // ReferenceError: x is not defined
```

### 4.2 Deleting Variables, Functions, or Parameters

```javascript
'use strict';
var x = 1;
delete x; // SyntaxError
```

> Q: Why is `delete` not allowed in strict mode?
> A: Because it's a bad practice to delete variables, functions, or parameters. It can lead to unexpected behavior. Instead, set the value to `null` or `undefined`. (from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Delete_in_strict_mode))

### 4.3 Duplicate Parameter Names

```javascript
'use strict';
function dupeParams(a, a) {} // SyntaxError
```

### 4.4 With Statement

```javascript
'use strict';
with (Math) { // SyntaxError
  x = cos(2);
}
```

## 5. Strict Mode Behavior Changes

### 5.1 `this` in Functions

- `this` is `undefined` in non-method functions (instead of global object)

### 5.2 `arguments` Object

- Doesn't reflect changes to function parameters

```javascript
function f(a) {
  'use strict';
  a = 2;
  console.log(arguments[0]); // Still 1, not 2
}
f(1);
```

## Summary

- Strict mode helps catch common coding errors and "unsafe" actions
- Apply strict mode to individual scripts
- Use ESLint 😉
