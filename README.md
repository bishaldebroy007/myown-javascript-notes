# My JavaScript Notes

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

**Temporal Dead Zone:** It is the time since when the 'let' variable was hoisted and till it was initialized with some value. The time in between is called the Temporal Dead Zone.




## Acknowledgement

[@Akshay Saini](https://www.youtube.com/@akshaymarch7)
