# Chapter 28: Number

---

## 1. Number Constructor Function

- `Number` is a standard built-in object that serves as a wrapper for numeric values
- Can be used as a constructor function with `new` keyword
- Without arguments, it creates a wrapper object with value 0
- With a numeric argument, it creates a wrapper object with that value
- With a non-numeric argument, it attempts to convert it to a number

```javascript
const numObj = new Number(10);
console.log(numObj); // Number {[[PrimitiveValue]]: 10}
```

---

## 2. Number Properties

### 2.1 Number.EPSILON

- Represents the difference between 1 and the smallest floating point number greater than 1
- Used to handle rounding errors in floating point arithmetic

```javascript
console.log(0.1 + 0.2 === 0.3); // false
console.log(Math.abs(0.1 + 0.2 - 0.3) < Number.EPSILON); // true
```

### 2.2 Number.MAX_VALUE

- Largest representable positive number in JavaScript

### 2.3 Number.MIN_VALUE

- Smallest representable positive number in JavaScript

### 2.4 Number.MAX_SAFE_INTEGER

- Largest integer that can be safely represented in JavaScript

### 2.5 Number.MIN_SAFE_INTEGER

- Smallest integer that can be safely represented in JavaScript

### 2.6 Number.POSITIVE_INFINITY

- Represents positive infinity

### 2.7 Number.NEGATIVE_INFINITY

- Represents negative infinity

### 2.8 Number.NaN

- Represents "Not-a-Number"

---

## 3. Number Methods

### 3.1 Number.isFinite()

- Checks if a value is a finite number

### 3.2 Number.isInteger()

- Checks if a value is an integer

### 3.3 Number.isNaN()

- Checks if a value is NaN

### 3.4 Number.isSafeInteger()

- Checks if a value is a safe integer

### 3.5 Number.prototype.toExponential()

- Returns a string representing the number in exponential notation

### 3.6 Number.prototype.toFixed()

- Returns a string representing the number with a specified number of decimals

### 3.7 Number.prototype.toPrecision()

- Returns a string representing the number with a specified precision

### 3.8 Number.prototype.toString()

- Converts the number to a string, optionally in a specified base (radix)

```javascript
(16).toString(2);  // "10000" (binary)
(16).toString(16); // "10" (hexadecimal)
```
