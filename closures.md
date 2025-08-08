# Closures

## What is a Closure?
A **closure** is a feature in JavaScript where an **inner function** has access to:

1. Its **own scope** (variables defined inside it)
2. The **outer function’s variables**
3. The **global scope**

_This means a function “remembers” the variables from where it was created, even if it’s used outside that scope._ <br />
In other words, it can also be answered as, _Closure means a function that is bundled with its lexical scope._ <br />

<img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/c3003375-73dd-4dea-97ec-e76741e78652" />


### Basic Syntax Example
```JavaScript
function outerFunction() {
  let count = 0; // local variable

  function innerFunction() {
    count++; // accessing outer function's variable
    console.log(count);
  }

  return innerFunction;
}

const counter = outerFunction();
counter(); // 1
counter(); // 2
counter(); // 3
```
**Why this works?** <br />
Because `innerFunction()` closes over the variable `count`. It keeps a reference to it even after `outerFunction()` has finished running. <br />

## Why Are Closures Useful?
- Data Privacy / Encapsulation
   - Create "private" variables
- Callback Functions
   - Especially in event handling and asynchronous code
- Functional Programming
   - Closures are key in concepts like currying, partial application
- Factory Functions
   - Functions that generate other functions

### Real-Life Example: Private Counter
```JavaScript
function createCounter() {
  let count = 0;

  return {
    increment: function () {
      count++;
      return count;
    },
    decrement: function () {
      count--;
      return count;
    },
    getCount: function () {
      return count;
    }
  };
}

const counter = createCounter();
console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
console.log(counter.getCount());  // 2
```
`count` is private – it can only be accessed through the methods returned. <br />

## How to Explain Closures?

> "A closure is created when a function remembers the variables from its outer scope, even after that outer function has returned. It’s like a backpack where the inner function carries its environment along with it."

### More information about functions in JS (Why functions are also known as the heart of JS)
- A function can be kept inside a variable,
- Also, it can be passed into another function as a parameter.
- A function can also be returned.

### Quick Recap
- A closure = function + its surrounding lexical environment
- It allows persistent access to outer variables
- Useful for data hiding, callbacks, and functional patterns

### Practice Questions
1. What is a closure in your own words?
2. Can a closure exist after its parent function finishes?
3. How can closures be used to create private variables?



<img width="985" height="288" alt="image" src="https://github.com/user-attachments/assets/37c4d466-c220-4565-8206-30c18fdcd80c" />

## SetTimeout + Clousers
<img width="1000" height="312" alt="image" src="https://github.com/user-attachments/assets/df19aefa-901e-4e70-a19b-0e5baa93203c" />

It will not wait for 3000ms or 3s to pass by and print the `console.log("...")`. Instead, it will print the `console.log("...")` first, and then after 3000ms or 3s, it will print `console.log(i)`. <br />

**Now let's discuss how the entire thing works:** <br />
- The inner function creates a closure and remembers the variable i. So, wherever the inner function goes, it takes the variable along with its reference with it. <br />

**This does not work as everyone thinks:**
<img width="997" height="406" alt="image" src="https://github.com/user-attachments/assets/b6c4d0cd-6e60-440d-9d9a-18557ebd59c6" />

Here,
- Instead of printing 1,2,3... sequentially and after 1s of gap it is printing 6 every time after 1s of gap.
- When the function inside is called, it stores the internal function (which is inside the `setTimeout`) in a different part of the memory along with the memory reference.
- And as the loop was continuously running, by the time the setTimeout finishes running, the entire loop finishes running and sets to the value afterwards, which is 6 in this case.
- To fix the issue, instead of `var`, `let` could be used. What it will do is it will create a new copy each time the function runs as `let` is block-scoped, the output will be what we expect.
- Previously, it was not working with `var` because it was referring to the same memory location each time.
- But to fix the issue with `var` only we can only do that using a closure. With a `var`, we need to wrap the setTimeout function with another function, call it, and pass 'i' (in this case). For example:

<img width="348" height="278" alt="image" src="https://github.com/user-attachments/assets/d5fce77a-cb49-4431-8bdd-a73157a17bdd" />


>[!Note]
>In JavaScript, variables declared with var are function-scoped, not global-scoped by default. However,
>if a `var` variable is declared outside any function, it becomes globally scoped (attached to the window object in browsers).

### Good Examples of closures


<br />
<br />

- [Read More from W3School](https://www.w3schools.com/js/js_function_closures.asp)
- [Read More from MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures)

<br />
