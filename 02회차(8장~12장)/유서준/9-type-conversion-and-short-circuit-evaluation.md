# Chapter 9: Type Conversion and Short-Circuit Evaluation

---

## 1. Type Conversion

- Definition: Changing a value from one data type to another.
- Two types: Explicit (intentional) and Implicit (automatic/coerced)

### 1.1 Explicit Type Conversion

- Intentionally changing a value's type using built-in functions or methods.
- Methods:
  - String(): Converts to string
  - Number(): Converts to number
  - Boolean(): Converts to boolean

### 1.2 Implicit Type Conversion (Coercion)

- Automatic type conversion by JavaScript during operations.
- Occurs in operations involving different data types.

---

## 2. Converting to String

- String(value)
- value.toString()
- value + "" (concatenation with empty string)

```JavaScript
// String()
var num = 123;
var str = String(num);

// toString()
var bool = true;
var str = bool.toString();

// Concatenation
var num = 123;
var str = num + "";
```

---

## 3. Converting to Number

- Number(value)
- parseInt(string) / parseFloat(string)
- +value (unary plus operator)
- value * 1

```JavaScript
// Number()
let str = "42";
console.log(Number(str)); // 42

// parseInt() / parseFloat()
console.log(parseInt("42.5", 10)); // 42
console.log(parseFloat("42.5")); // 42.5

// Unary plus operator
let strNum = "42";
console.log(+strNum); // 42

// Multiply by 1
let boolTrue = true;
console.log(boolTrue * 1); // 1
```

---

## 4. Converting to Boolean

- Boolean(value)
- !!value (double negation)

```JavaScript
// Boolean()
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false

// Double negation
console.log(!!42); // true
console.log(!!""); // false
```

---

## 5. Truthy and Falsy Values

- Falsy values: false, 0, "", null, undefined, NaN
- Truthy values: Everything else

```JavaScript
// Falsy values
console.log(Boolean(false)); // false
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN)); // false

// Truthy values - Everything else
console.log(Boolean(true)); // true
console.log(Boolean(42)); // true
console.log(Boolean("hello")); // true
console.log(Boolean([])); // true
console.log(Boolean({})); // true
```

---

## 6. Short-Circuit Evaluation

- Definition: Stopping the evaluation of an expression as soon as the result is determined.

### 6.1 Logical AND (`&&`)

- Returns the first falsy value or the last value if all are truthy.
- `expr1` && `expr2` && `expr3`

```JavaScript
// Logical AND (&&)
console.log(true && 'Hello'); // 'Hello'
console.log(false && 'Hello'); // false
```

### 6.2 Logical OR (`||`)

- Returns the first truthy value or the last value if all are falsy.
- `expr1` || `expr2` || `expr3`

```JavaScript
// Logical OR (||)
console.log(null || 'Default'); // 'Default'
console.log('Hello' || 'Default'); // 'Hello'
```

---

## 7. Nullish Coalescing Operator (`??`)

- Returns the right-hand operand when the left is null or undefined.
- Introduced in ES2020
- value ?? defaultValue

```JavaScript
let name = null;
console.log(name ?? 'Anonymous'); // 'Anonymous'

let count = 0;
console.log(count ?? 42); // 0
```

---

## 8. Optional Chaining Operator (`?.`)

- Safely accesses nested object properties.
- Returns undefined if the property doesn't exist(`null` or `undefined`) instead of throwing an error.
- object?.property?.nestedProperty

```JavaScript
let user = {
  address: {
    street: 'Main St'
  }
};

console.log(user?.address?.street); // 'Main St'
console.log(user?.contact?.email); // undefined
```

---

## 9. My opinion about Type Conversion in JavaScript

- Let's use the explicit type conversion methods to avoid confusion.
- Let's use limited type conversion methods to prevent unexpected results and increase readability.
  - Use `parseInt(string, 10)` for integer conversion (always specify the radix)
  - Use `parseFloat(string)` for floating-point numbers
  - Prefer `===` (strict equality) over `==` to avoid implicit type conversion in comparisons
- Use type checking before type conversion to prevent errors. (`typeof`, `instanceof`)
- Let's Use TypeScript 😂🤦‍♂️
