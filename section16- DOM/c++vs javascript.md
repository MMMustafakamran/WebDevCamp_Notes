# **C++ vs JavaScript**

------

#### 1. Variable Declarations

**JavaScript (dynamically typed):**

```javascript
// Using let (block-scoped) and const (block-scoped, immutable binding)
let x = 10;
const PI = 3.14159;

// Variables can change type dynamically
let value = "Hello";
value = 42; // Now a number
```

**C++ (statically typed):**

```cpp
// You must declare the variable type, and types cannot change once set.
int x = 10;
const double PI = 3.14159;

// Type is fixed at declaration:
std::string value = "Hello";
// value = 42; // This would be an error because value is a string.
```

------

### 2. Function Declarations

**JavaScript:**

```javascript
// Function declaration with no type annotations
function add(a, b) {
  return a + b;
}

// Arrow function syntax (ES6)
const multiply = (a, b) => a * b;
```

**C++:**

```cpp
// Function declaration with return type and parameter types
int add(int a, int b) {
  return a + b;
}

// C++ does not have an equivalent to JavaScript's arrow functions for defining anonymous functions (C++ lambdas are similar but with a different syntax):
auto multiply = [](int a, int b) -> int { return a * b; };
```

------

### 3. Object and Data Structures

**JavaScript:**

```javascript
// Objects are created on the fly without a class (prototypal inheritance)
let person = {
  name: "Alice",
  age: 30
};

// Arrays are dynamic and can hold any type
let items = [1, "two", true];
```

**C++:**

```cpp
// Use structs or classes to define data structures
struct Person {
  std::string name;
  int age;
};

Person person = {"Alice", 30};

// Arrays require a fixed size or use STL containers like std::vector
#include <vector>
std::vector<int> items = {1, 2, 3};
```

------

### 4. String Handling

**JavaScript:**

```javascript
let greeting = "Hello";
let name = "Alice";

// Concatenation using + or template literals
console.log(greeting + ", " + name + "!");
console.log(`${greeting}, ${name}!`);
```

**C++:**

```cpp
#include <iostream>
#include <string>

std::string greeting = "Hello";
std::string name = "Alice";

// Concatenation using the + operator
std::cout << greeting + ", " + name + "!" << std::endl;

// C++ does not have a built-in template literal equivalent
```

------

### 5. Control Structures and Loops

**JavaScript:**

```javascript
// If-else statement (similar in structure to C++)
let score = 85;
if (score > 80) {
  console.log("Great match!");
} else {
  console.log("Needs improvement.");
}

// For loop
for (let i = 0; i < 5; i++) {
  console.log("Iteration " + i);
}

// While loop
let count = 0;
while (count < 5) {
  console.log("Count: " + count);
  count++;
}
```

**C++:**

```cpp
#include <iostream>

int score = 85;
if (score > 80) {
  std::cout << "Great match!" << std::endl;
} else {
  std::cout << "Needs improvement." << std::endl;
}

// For loop
for (int i = 0; i < 5; i++) {
  std::cout << "Iteration " << i << std::endl;
}

// While loop
int count = 0;
while (count < 5) {
  std::cout << "Count: " << count << std::endl;
  count++;
}
```

------

### 6. Memory Management

**JavaScript:**

- Memory is automatically managed with garbage collection.
- No explicit syntax for manual memory allocation.

**C++:**

```cpp
// Manual memory management (using new and delete)
int* ptr = new int(10); // allocate memory
std::cout << *ptr << std::endl;
delete ptr;            // free allocated memory
```

------

### 7. Asynchronous Code

**JavaScript:**

```javascript
// Asynchronous code using callbacks, promises, or async/await.
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);

// Async/Await (ES2017)
async function fetchData() {
  let response = await fetch("https://api.example.com/data");
  let data = await response.json();
  console.log(data);
}
```

**C++:**

- C++ supports asynchronous programming via libraries and features like threads, futures, and async functions, but the syntax is more complex and lower-level.

```cpp
#include <future>
#include <iostream>

int compute() {
    return 42;
}

int main() {
    // Run compute() asynchronously
    std::future<int> fut = std::async(std::launch::async, compute);
    std::cout << "Result: " << fut.get() << std::endl;
    return 0;
}
```

------

### Summary

- **Dynamic vs. Static Typing:** JavaScript allows variables to change types at runtime, while C++ requires explicit type declarations.
- **Memory Management:** JavaScript handles memory automatically; C++ requires explicit memory management.
- **Function Syntax:** JavaScript functions do not require type annotations and support flexible declaration styles (e.g., arrow functions), whereas C++ functions require types.
- **Asynchronous Programming:** JavaScript has built-in support for asynchronous operations using promises and async/await, while C++ manages asynchronous tasks using threads and related libraries.

These syntax differences illustrate how each language is tailored to its typical use cases and runtime environments.