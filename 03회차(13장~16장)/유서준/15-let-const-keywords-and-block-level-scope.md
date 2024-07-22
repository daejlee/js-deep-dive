# Chapter 15: `let`, `const`, and Block-Level Scope

---

## 1. Problems with `var`

- Allows variable redeclaration
- Function-level scope only
- Hoisting can lead to unexpected behavior

---

## 2. `let` Keyword

### 2.1 No Redeclaration

```javascript
let x = 1;
let x = 2; // SyntaxError: Identifier 'x' has already been declared
```

### 2.2 Block-Level Scope

```javascript
if (true) {
  let x = 10;
  console.log(x); // 10
}
console.log(x); // ReferenceError: x is not defined
```

### 2.3 Temporal Dead Zone (TDZ)

- Cannot access variable before declaration
- Hoisting still occurs, but differently from `var`
- Declaration stage(ReferenceError) -> Initialization stage(undefined) -> Assignment stage

```javascript
console.log(x); // ReferenceError: Cannot access 'x' before initialization
let x = 1;
```

### 2.4 Not Added to Global Object

```javascript
let x = 1;
console.log(window.x); // undefined
```

---

## 3. `const` Keyword

### 3.1 Must Be Initialized

```javascript
const x = 1; // Correct
const y; // SyntaxError: Missing initializer in const declaration
```

### 3.2 No Reassignment

```javascript
const x = 1;
x = 2; // TypeError: Assignment to a constant variable
```

### 3.3 Use for Constants

```javascript
const PI = 3.14159;
const TAX_RATE = 0.1;
```

### 3.4 Objects with `const`

- The reference is constant, not the content

```javascript
const obj = { x: 1 };
obj.x = 2; // Allowed
obj = {}; // TypeError: Assignment to a constant variable
```

---

## 4. Best Practices

1. Avoid using `var`
2. Use `let` for variables that need reassignment
3. Use `const` by default
4. Use `const` for all primitive values and objects that don't need reassignment
5. Consider using all-caps for true constants (e.g., `PI`, `MAX_SIZE`)
