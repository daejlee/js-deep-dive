# Chapter 13: Scope

---

## 1. What is Scope?

- Scope determines the accessibility of variables and functions in code
- It's the region where a variable or function can be referenced
- Scope helps prevent naming conflicts and provides security by limiting access to variables

---

## 2. Types of Scope

### 2.1 Global Scope

- Variables declared outside any function or block
- Accessible from anywhere in the code

### 2.2 Local Scope

- Variables declared inside a function or block
- Only accessible within that function or block

---

## 3. Scope Chain

- Hierarchical structure of nested scopes
- When a variable is referenced, JS engine searches up the scope chain
- Starts from the innermost scope and moves outward until it finds the variable

```javascript
var globalVar = "I'm global";

function outerFunc() {
  var outerVar = "I'm from outer";
  
  function innerFunc() {
    var innerVar = "I'm from inner";
    console.log(innerVar);  // Accessible
    console.log(outerVar);  // Accessible
    console.log(globalVar); // Accessible
  }
  
  innerFunc();
  console.log(innerVar);  // Not accessible
}

outerFunc();
console.log(outerVar);  // Not accessible
```

---

## 4. Function-Level Scope

- JavaScript has function-level scope for variables declared with `var`
- Variables declared inside a function are only accessible within that function
- Block statements (if, for, while) do not create a new scope for `var`

```javascript
if (true) {
  var x = 10;
}
console.log(x); // 10 (x is accessible)

function test() {
  var y = 20;
}
console.log(y); // ReferenceError: y is not defined
```

- However, we will use let, const keywords for block-level scope in modern JS

---

## 5. Lexical Scope

- Also known as static scope
- A function's scope is determined by its location in the source code
- Inner functions have access to variables in their outer scope

```javascript
var x = 10;

function outer() {
  var y = 20;
  
  function inner() {
    var z = 30;
    console.log(x + y + z);
  }
  
  inner();
}

outer(); // Outputs: 60
```

---

## 6. Best Practices

- Minimize use of global variables
- Use local scope when possible to avoid naming conflicts
- Be aware of hoisting behavior with `var` declarations
- Utilize lexical scope for creating closures and maintaining privacy
- Just don't use `var` anymore, use `let` and `const` instead 😉 (more in chapter 15)
