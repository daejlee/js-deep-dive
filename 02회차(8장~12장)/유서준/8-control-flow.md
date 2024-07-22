# Chapter 8: Control Flow in JavaScript

---

## 1. What is Control Flow

- Control flow is the order in which individual statements, instructions, or function calls are executed in a program.

---

## 2. Block Statements

- A block statement is used to group statements.
- Defined by a pair of curly brackets `{}`.
- Used with control flow statements like if, for, while.

---

## 3. Conditional Statements

### 3.1 if...else Statement

- Executes a block of code if a specified condition is true.
- Can include an optional else clause for when the condition is false.
- Multiple conditions can be chained using else if.

Basic Syntax:

```javascript
if (condition) {
    // code to be executed if condition is true
} else if (anotherCondition) {
    // code to be executed if anotherCondition is true
} else {
    // code to be executed if no condition is true
}
```

Advanced Syntax 1 - Omitting the curly brackets:

```JavaScript
// If there is only a single statement in the code block, we can omit the curly brackets
var weight = 80;
var status;

if (weight < 60) status = "Skinny"
else if (weight < 90) status = "Fit"
else status = "Do some cardio"

```

Advanced Syntax 2 - Using Ternary Operator instead of if...else statement.

```JavaScript
// Most of the if...else statements can be replaced with using ternary operators. 
var age = 21;
var isAdult;

if (age > 19) isAdult = true;
else isAdult = false;

//  We can use Ternary Operator instead 
var isAdult = age > 19 ? true : false;
```

### 3.2 switch Statement

- Evaluates an expression and executes code blocks based on matching cases.
- Uses the `break` keyword to prevent fall-through between cases.
- Can include a `default` case for when no match is found.

Syntax:

```javascript
switch (expression) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}
```

---

## 4. Loops

### 4.1 for Loop

- Repeats a block of code a specified number of times.
- Consists of initialization, condition, and increment/decrement parts.

Syntax:

```javascript
for (initialization; condition; increment/decrement) {
    // code to be repeated
}

// example
for (var i = 0; i < 3; i++) {
    console.log(i) // prints 0, 1, 2
}
```

### 4.2 while Loop

- Executes a block of code as long as a specified condition is true.
- The condition is checked before each iteration.

Syntax:

```javascript
while (condition) {
    // code to be repeated
}
```

### 4.3 do...while Loop

- Similar to while loop, but the condition is checked after the code block is executed.
- Ensures that the code block is executed at least once.

Syntax:

```javascript
do {
    // code to be repeated
} while (condition);
```

---

## 5. Break and Continue Statements

### 5.1 break Statement

- Used to exit a loop or switch statement prematurely.
- Can be used with labeled statements to break out of nested loops.

### 5.2 continue Statement

- Skips the rest of the current iteration in a loop and continues with the next iteration.
