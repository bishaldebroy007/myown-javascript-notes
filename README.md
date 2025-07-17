# My JavaScript Notes

Everything in JS happens inside an **Execution Context**.

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/621bcb18-0d5d-41a5-930b-195000d05fce" />

One more fundamental concept is that JS is a synchronous single-threaded language. Single-threaded means it can execute one code at a time, and "Synchronous single-threaded" means it executes one code at a time and also in a specific order.

## What happens when a JS code is run?
When a JS code is run, an Execution Context is created.
This happens in 2 phases. Such as <br>
1. Memory Creation:
   <img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/808b625b-432e-4558-b2b4-b2c6cdb7cbfc" />

   In the first phase, first, all the variables are stored with a value 'undefined' initially. Such as - n, square 2, square 4.  If it is a function, the entire code inside the function will be saved along with the function - such as the square function in this case.

2. Code Execution Phase:
   Now, in the second phase, the undefined values stored within the values will be replaced by the actual values in this phase. Besides, the function will remain untouched in this phase for now.
   At the same time, for square 2 & square 3, which means for function invocation, for instance, a function call in a variable is known as variable invocation.
   
   ```JavaScript
   var square2 = square(n);
   var square4 = square(4);
   ```
***Note: In this case, 'n' inside the square function is called an argument, and 'num' inside the square(num) is called a parameter.***
   
   For variable invocation like this, another **Execution Context** will be created inside the first one.
   
  <img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/c1f2fce3-91df-4eb9-b35e-b0d144e71793" />

This time, it will only be concerned with the code inside the function; in this case, the function is "square()". The same process will be repeated from phase 1.

<img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/fca5475d-09cd-44f9-af6f-383b3aea2203" />

Just like before, the variable inside the function, called 'ans' and 'num' is stored in the memory section with a value of 'undefined' initially.

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

Every time a Call Stack is run, it populates the stack with a Global Execution Context (aka GEC). Now, the entire Execution context is pushed inside the stack as GEC, and after the execution is done, it leaves control to GEC.

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
 
