# My JavaScript Notes

Everything in JS happens inside an **Execution Context**.

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/621bcb18-0d5d-41a5-930b-195000d05fce" />
One more fundamental concept is that JS is a synchronous single-threaded language. Single-threaded means it can execute one code at a time, and "Synchronous single-threaded" means it executes one code at a time and also in a specific order.

### What happens when a JS code is run?
When a JS code is run, an Execution Context is created.
This happens in 2 phases. Such as <br>
1. Memory Creation:
   <img width="790" height="420" alt="image" src="https://github.com/user-attachments/assets/808b625b-432e-4558-b2b4-b2c6cdb7cbfc" />

   In the first phase, first, all the variables are stored with a value 'undefined' initially. Such as - n, square 2, square 4.  If it is a function, the entire code inside the function will be saved along with the function - such as the square function in this case.

3. Code Execution Phase:
   

## Var, Let, Const:
- The var keyword was used in all JavaScript code from 1995 to 2015 (it is not used now).
- The let and const keywords were added to JavaScript in 2015.
- Remember: The var keyword should only be used in code written for older browsers.

```Javascript
var lang = "Bangla";

function learn(topic) {
  lang = topic;
  console.log(`I am learning ${topic}`};
}
learn{"JavaScript"}

console.log(`I know ${lang}`};
```
Here, since the var lang is global, it will change the lang inside the function, but eventually it will be replaced by the new text "JavaScript". So the 
