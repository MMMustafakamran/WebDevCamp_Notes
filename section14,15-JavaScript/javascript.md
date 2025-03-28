# JavaScript Fundamentals: A Concise Reference

## Table of Contents

- [Introduction](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#introduction)
- [Basic Syntax](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#basic-syntax)
- [Data Types and Variables](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#data-types-and-variables)
- [Strings](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#strings)
- [Functions](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#functions)
- [Conditional Logic](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#conditional-logic)
- [Arrays](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#arrays)
- [Loops](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#loops)
- [Common Coding Challenges](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#common-coding-challenges)

## Introduction

JavaScript is a high-level, interpreted language primarily used for web development. It runs both client-side (browser) and server-side (Node.js).

```html
<script>
  console.log("Hello, world!"); // Output to the console
</script>
```

## Basic Syntax

### Alerts

Display popup messages to users:

```javascript
alert("Welcome to JavaScript!");
```

## Data Types and Variables

### Main Data Types

- **Number**: `let age = 30;`
- **String**: `let name = "Alice";`
- **Boolean**: `let isStudent = false;`
- **null**: `let job = null;`
- **undefined**: `let salary;`
- **Object**: `let person = { firstName: "Alice", lastName: "Smith" };`

### Variable Declaration

```javascript
// For variables that can change
let counter = 10;
counter = 15;

// For constants
const PI = 3.14159;
```

### Naming Conventions

- Use letters, digits, underscores (_), dollar signs ($)
- Cannot start with a digit
- JavaScript is case-sensitive
- Typically use camelCase

```javascript
let firstName = "Alice";
let _privateVar = "hidden";
let $element = document.getElementById("myId");
```

## Strings

### Concatenation

```javascript
// Using + operator
let greeting = "Hello, ";
let name = "Alice";
let message = greeting + name + "!"; // "Hello, Alice!"

// Using template literals
let message2 = `${greeting}${name}!`; // "Hello, Alice!"
```

### String Properties and Methods

```javascript
let text = "JavaScript";

// Length
console.log(text.length); // 10

// Slicing
let sliced = text.slice(4, 10); // "Script"

// Case conversion
console.log(text.toUpperCase()); // "JAVASCRIPT"
console.log(text.toLowerCase()); // "javascript"
```

## Functions

### Basic Function

```javascript
function greet() {
  console.log("Hello, world!");
}

greet(); // Call the function
```

### Functions with Parameters

```javascript
function add(a, b) {
  return a + b;
}

let sum = add(5, 3); // 8
```

### Return Values

```javascript
function square(x) {
  return x * x;
}

let result = square(4); // 16
```

## Conditional Logic

### Random Number Generation

```javascript
// Generate number between 0-100
let randomNum = Math.floor(Math.random() * 101);
```

### if-else Statements

```javascript
let score = 75;

if (score > 80) {
  console.log("Great job!");
} else if (score >= 50) {
  console.log("Good effort.");
} else {
  console.log("Keep practicing.");
}
```

### Comparators

```javascript
// Equality
let a = 5;
let b = "5";
console.log(a == b);   // true (value comparison)
console.log(a === b);  // false (value AND type comparison)

// Other comparators: !=, !==, <, >, <=, >=
```

### Logical Operators

```javascript
let age = 25;
let hasLicense = true;

// AND operator
if (age >= 18 && hasLicense) {
  console.log("You can drive.");
}

// OR operator
if (age < 18 || !hasLicense) {
  console.log("You cannot drive.");
}
```

## Arrays

### Creating Arrays

```javascript
let fruits = ["apple", "banana", "cherry"];
```

### Accessing Elements

```javascript
console.log(fruits[0]); // "apple"
console.log(fruits.length); // 3
```

### Array Methods

```javascript
// Add to end
fruits.push("date");

// Remove from beginning
let first = fruits.shift();

// Transform array
let numbers = [1, 2, 3];
let squares = numbers.map(num => num * num); // [1, 4, 9]
```

## Loops

### While Loop

```javascript
let count = 0;
while (count < 5) {
  console.log(count);
  count++;
}
```

### For Loop

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

## Common Coding Challenges

### BMI Calculator

```javascript
function calculateBMI(weight, height) {
  let bmi = weight / (height * height);
  
  if (bmi < 18.5) {
    return [bmi, "Underweight"];
  } else if (bmi < 25) {
    return [bmi, "Normal weight"];
  } else if (bmi < 30) {
    return [bmi, "Overweight"];
  } else {
    return [bmi, "Obese"];
  }
}

// Example usage
let [bmi, category] = calculateBMI(70, 1.75);
console.log(`BMI: ${bmi.toFixed(2)}, Category: ${category}`);
```

### Life in Weeks

```javascript
function lifeInWeeks(age) {
  const maxAge = 90;
  const weeksPerYear = 52;
  let remainingYears = maxAge - age;
  return remainingYears * weeksPerYear;
}

console.log(`You have ${lifeInWeeks(25)} weeks left.`);
```

### Who's Buying Lunch

```javascript
function whosPaying(names) {
  let randomIndex = Math.floor(Math.random() * names.length);
  return `${names[randomIndex]} is buying lunch today!`;
}

let result = whosPaying(["Alice", "Bob", "Charlie", "David"]);
console.log(result);
```

### Fibonacci Sequence

```javascript
function generateFibonacci(n) {
  if (n <= 0) return [];
  if (n === 1) return [0];
  
  let fib = [0, 1];
  for (let i = 2; i < n; i++) {
    fib.push(fib[i-1] + fib[i-2]);
  }
  
  return fib;
}

console.log(generateFibonacci(10)); // [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```