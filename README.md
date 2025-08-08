<img width="997" height="406" alt="image" src="https://github.com/user-attachments/assets/3e3d7159-2f97-45d5-a91e-c652d30871bb" /># My JavaScript Notes

Everything in JS happens inside an **Execution Context**.

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/621bcb18-0d5d-41a5-930b-195000d05fce" />

One more fundamental concept is that JS is a synchronous, single-threaded language. Single-threaded means it can execute one code at a time, and "Synchronous single-threaded" means executing one code at a time and in a specific order.

## What happens when a JS code is run?
When a JS code is run, an Execution Context is created.
This happens in 2 phases. Such as <br>
1. Memory Creation:
   <img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/808b625b-432e-4558-b2b4-b2c6cdb7cbfc" />

   In the first phase, all the variables are stored with a value 'undefined' initially, such as n, square2, and square4. If it is a function, the function body will be saved along with the function, such as the square function in this case.

2. Code Execution Phase:
   Now, in the second phase, the undefined values stored within the values will be replaced by the actual values in this phase. Besides, the function will remain untouched in this phase for now.
   At the same time, for square 2 & square 3, which means for function invocation, for instance, a function call in a variable is known as variable invocation.
   
   ```JavaScript
   var square2 = square(n);
   var square4 = square(4);
   ```

> [!NOTE]
> In this case, 'n' inside the square function is called an argument, and 'num' inside the square(num) is called a parameter.
   
   For variable invocation like this, another **Execution Context** will be created inside the first one.
   
  <img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/c1f2fce3-91df-4eb9-b35e-b0d144e71793" />

This time, it will only be concerned with the body code inside the function; in this case, the function is "square()". The same process will be repeated from phase 1.

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/fca5475d-09cd-44f9-af6f-383b3aea2203" />

Just like before, the variable inside the function, called 'ans' and 'num', is stored in the memory section with a value of 'undefined' initially.

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/10cd8f88-b640-4d9b-8d8c-e278039b1d83" />

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/a2f80550-1de6-47d4-a938-18ee04b42e68" />

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/ec23b419-8736-4bc4-b6d5-69f4ddbd52f6" />
<br />

> [!IMPORTANT]
> ***The return in a function means that it returns the value to the position where the function was invoked.***

   ```JavaScript
   var square2 = square(n);
   ```
As soon as the main value receives the return value from the function, the nested Execution Context will be deleted.

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/cb6a74bc-ac2b-44d2-9edc-f217d0edd2a9" />

Finally, the same thing will happen for a square; the only difference is that there is a value given as an argument.

### Call Stack in JavaScript:
It helps to manage all the **Execution Context**.

Every time a Call Stack is run, it populates the stack with a ***Global Execution Context (GEC)***. Now, the entire Execution context is pushed inside the stack as GEC, and after the execution, it leaves control to GEC. 

<img width="1068" height="547" alt="image" src="https://github.com/user-attachments/assets/810cadf2-faa7-4f35-ba90-eca178c02b3c" />

For this case,

- First E1, which means the first execution context  for square2=square(n) will enter the stack, and after it is done executing, it will simply pop out of the stack.
  <img width="1068" height="547" alt="image" src="https://github.com/user-attachments/assets/26742149-8f12-429b-9aa0-836dcaebf60c" />
  
- The same thing will happen for E2, which is Execution context 2, for square4=square(4).

<img width="1068" height="547" alt="image" src="https://github.com/user-attachments/assets/bbd9c088-1d21-4f3f-bfe4-d336d20075f5" />

**Other Fancy names for Call stack:**
<img width="1068" height="547" alt="image" src="https://github.com/user-attachments/assets/916203e3-f93d-4117-ad57-5e83adab6cc3" />

> [!NOTE]
> ***Call Stack maintains the order of execution of execution contexts***

## Hoisting
To directly dive into Hoisting, let's see some examples to get a better understanding of the situation here.  

### Visualizing the situation:

__First Case Code:__

```JavaScript
var x = 7;

function getName() {
   console.log("JavaScript");
}

getName();
console.log(x);
```

__Output on console:__

```bash
> JavaScript
> 7
```

__Second Case Code:__

```JavaScript
getName();
console.log(x);

var x = 7;

function getName() {
   console.log("JavaScript");
}

```

__Output on console:__

```bash
> JavaScript
> undefined
```

This might look initially, but that's how JavaScript works, and the reason behind it is well connected with the previous topic, **Execution Context**.

> [!NOTE]
> ```
> console.log(getName) without any invocation will only print the whole function
> ```

### Visualizing more scenarios:
```JavaScript
getName();
console.log(x);
console.log(getName);

var x = 7;

function getName() {
   console.log("JavaScript");
}

```
__Output on console:__

```bash
> JavaScript
> undefined
```

```JavaScript
getName();
console.log(x);
console.log(getName);

var x = 7;

var getName = () => {
   console.log("JavaScript");
}

```

__Output on console:__

```bash
> undefined
> undefined
```
> [!TIP]
> 1. In the second case, the function acts as a variable. <br />
> 2. The value of the array function is stored as 'undefined'.

```JavaScript
var getName2 = function () {
   console.log("Console")
}
```
> [!NOTE]
> This type of function is also stored as a variable in EC.

## Functions

```JavaScript
var x = 1;

a();
b();
console.log(x); //Just to see what is printed

function a() {
   var x = 10;
   console.log(x);
}

function b() {
   var x = 100;
   console.log(x);
}

```
__Output:__ <br />
<img width="474" height="141" alt="image" src="https://github.com/user-attachments/assets/bad07a28-a121-4a69-ab97-2a3079209658" />

## How Execution Context will work here

Let's first place in the Memory Component, <br />
<img width="712" height="390" alt="image" src="https://github.com/user-attachments/assets/3d48d9fe-ebe6-4de4-b215-bd0315dc30ec" />

> [!NOTE]
> The first phase, Memory Component, is also called the 'Variable Environment'.

Now, the value of x will be replaced by 1, and secondly, since the function is invoked, a new stack will be added to the call stack, and also a new independent EC will be created inside the Global EC.

<img width="941" height="382" alt="image" src="https://github.com/user-attachments/assets/fce39164-9c3a-4b2a-adac-6078d35e32b8" />

> [!NOTE]
> Always, before using a variable, it will look for the value of the variable inside the scope of that specific function first!

Since the execution of the a() function is complete, it will be removed from the call stack and at the same time it will also be removed from the main Execution Context (EC). 

<img width="943" height="481" alt="image" src="https://github.com/user-attachments/assets/b2e4bcdd-4dfa-4519-a967-24abdb06c2b0" />
Again, since the execution of over for the second function as well, it will pop out of the call stack and the main EC. Lastly, the control will move forward to line number 4 from 3 to console.log(x).

<img width="943" height="481" alt="image" src="https://github.com/user-attachments/assets/ad09d4dc-f456-4be0-b65c-5ef5773845c3" />

__Output__ <br />

```bash
> 10
> 100
> 1
```
After all the executions are done, the entire thing will be removed.

## Window & this-keyword

The shortest program in JavaScript is a blank JavaScript file.

**What is a window?** <br />
Ans: A window is like a global object, and it is created along with the global execution context. This means each time a JavaScript program is run, a global object is created, an execution context is created, and 'this' is created.

Even if a JavaScript file is empty, the global object will be created automatically.
So, at  the global level,

```JavaScript
this === window
> true
```

**What is global space?**<br />
Ans: 

```JavaScript
var a = 10; //Global space

function b() {   // Global space

}

function c() {
   var x = 10; // x is not in the global space
}


```

Now we know that anything in the global space will automatically get into the global object/window. For instance,

```JavaScript
var a = 30;
function c() {
   var x = 10;
}

console.log(window.a);
//or,
console.log(this.a);
//or,
console.log(a);
```
## Undefined vs Not Defined
So, "Undefined" and "Not Defined" might sound the same, but it is not. <br />
**Undefined:** Consider it like a special placeholder that holds a certain space in the memory for the time being until any other value is assigned.

```JavaScript
var a = 2;
console.log(a);
```
```bash
> a: 2
```
```JavaScript
console.log(a);
var a = 2;

```
```bash
> a: Undefined
```
On the other hand, "Not Defined" means a variable that is not declared yet but is used.
```JavaScript
console.log(x);
```
```bash
> Not Defined.
```
> [!NOTE]
> JavaScript is known as a loosely-typed or weakly-typed language, since its data type can be dynamically changed, unlike C or C++

## The Scope Chain, Scope & Lexical Environment
Let's discuss some cases, <br />
Case 1
```JavaScript
function a() {
   console.log(b);
}
var b = 10;
a(); //invoking the function
```
***Output:***
```bash
> 10
```
Case 2
```JavaScript
function a() {
   c(); //invoking the function c.
   function c() {
      console.log(b);
   }
}
var b = 10;
a(); //invoking the function a.
```
***Output:***
```bash
> 10
```
Case 3
```JavaScript
function a() {
   var b = 10;

   c(); //invoking the function c.
   function c() {
      console.log(b);
   }
}
a(); //invoking the function a.
```
***Output:***
```bash
> 10
```
So, we can see, it can still access the value.
But,
Case 3
```JavaScript
function a() {
   var b = 10;
}
a(); //invoking the function a.
console.log(b);
```
***Output:***
```bash
> ReferenceError: b is not defined.
```

**Easiest Definition of Scope:** Where a particular variable can be found is called the scope of that variable. For example, where is the scope of a variable called 'b'? Answer: It is inside the 'a()' scope.

### Lexical Environment
Whenever a Global Execution is created, a Lexical Environment is also created along with it. It is the local memory along with the lexical environment of its parent.
Now, the question is, **what is Lexical?** <br />
Answer to the question, 'Lexical' means hierarchy. For instance, the c() is lexically sitting inside the a(), and the a() is lexically sitting inside the global scope.
```JavaScript
function a() {
   var b = 10;

   c(); //invoking the function c.
   function c() {
      
   }
}
a(); //invoking the function a.
console.log(b);
```
<br />
<img width="754" height="663" alt="image" src="https://github.com/user-attachments/assets/3a9bee77-b4f2-4c14-97dd-a888d33e61c9" />

## Let & Const | Temporal Dead Zone
let & const declarations are hoisted in JavaScript. <br />
But, yes, they are managed differently in 'var' compared to let & const. <br />
Here,
```JavaScript
console.log(b);
var b = 100;
```
Output:
```bash
> 100
```
```JavaScript
console.log(a);
let a = 10;
```
Output:
```bash
> Uncaught ReferenceError: Cannot access 'a' before initialization.
```
But, if I try to
```JavaScript
let a = 10;
console.log(a);
```
It will work just fine. Why is that? <br />
This happens because 'let' & 'const' are assigned memory just like 'var', which is called hoisting. But in the case of 'var', the memory is allocated in the global, and in the  case of 'let' & 'const', the memory is allocated somewhere else where it cannot be excess before declaration or putting some value in them.

**Temporal Dead Zone:** It is the time since when the 'let' variable was hoisted till it was initialized with some value. The time in between is called the Temporal Dead Zone.

## Block Scope & Shadowing
**Block in JS:** <br />
```JavaScript
{
   //Compound Statement
}
```
This is a perfectly valid code or block in JavaScript, which does nothing. It is also called "Compound Statement". It is used to put multiple JS statements into one group. For instance, <br />
```JavaScript
{
   //Compound Statement
   var a = 10;
   console.log(a);
}
```
Why do we need to put them in such a group? So that wherever JS expects only one statement, we can send it as a single statement within a group. <br />
For example,
```JavaScript
if (true) {
   //Compound Statement
   var a = 10;
   console.log(a);
}
```

**Block Scope in JS:** <br />
It means, whatever variables & functions are inside a block, we can access.
```JavaScript
var a = 10;  // inside Global Scope
let b = 11; // Inside a seperate memory
const c = 12; // Inside a seperate memory
```
<img width="566" height="494" alt="image" src="https://github.com/user-attachments/assets/895fa6ff-30db-459b-a717-6851fd28911a" />

This is why it is said that 'let' & 'const' are block-scoped. <br />
>[!Note]
> let & const are never accessible outside of the block. Although the 'var' is accessible outside the block scope since it is in the global scope.

**Shadowing in JS:** <br />
<img width="927" height="462" alt="image" src="https://github.com/user-attachments/assets/fca7c5d0-8f3a-4309-a97f-da0b079b6f57" />
Here, we can see the output of a is 10, not 100. This implies that the 'var a = 10' inside the block scope shadows the 'var a = 100' outside the block and keeps the second value of a, which is 10. <br />

Even if we place another console.log(a) outside of the block, we will see that the value will still be 10. Because the 'var a = 10' inside the block is replacing or shadowing the value outside, because they both are pointing towards the same memory location.
<img width="907" height="403" alt="image" src="https://github.com/user-attachments/assets/03f3f47b-4a0b-4bc3-ad4c-8ef7e096c6d0" />

Although unlike 'ver', 'Let' works in a slightly different way,
<img width="915" height="341" alt="image" src="https://github.com/user-attachments/assets/806c14c5-492c-4c2f-9beb-f508de8ba45d" />
The value of b is 100, this time because the value inside the block is limited to its block scope, and the one outside is only getting access to the value that is outside, 100. <br />
Let's see how it works in functions,
<img width="924" height="358" alt="image" src="https://github.com/user-attachments/assets/d9b53231-2d0a-4490-83d4-150b15682672" />

**Illegal Shadowing:**
<img width="924" height="358" alt="image" src="https://github.com/user-attachments/assets/91cf8a99-a66b-4ff5-9f71-fedd2a506518" />

But this second case is perfectly valid,
<img width="924" height="358" alt="image" src="https://github.com/user-attachments/assets/73379da9-01d4-4e57-80a0-b5fdba9c7ab4" />

Remember these cases too,
<img width="965" height="376" alt="image" src="https://github.com/user-attachments/assets/c71ee05e-75f3-47de-8559-af20304dace2" />
<img width="965" height="376" alt="image" src="https://github.com/user-attachments/assets/430719b7-d7a9-4fd4-bf37-c236cfc2e5db" />

## JavaScript Closures – Simplified

### What is a Closure?
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

### Why Are Closures Useful?
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

### How to Explain Closures?

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

## Acknowledgement

[@Akshay Saini](https://www.youtube.com/@akshaymarch7)
