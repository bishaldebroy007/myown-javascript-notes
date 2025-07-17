# My JavaScript Notes

Everything in JS happens inside an **Execution Context**.

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/621bcb18-0d5d-41a5-930b-195000d05fce" />
One more fundamental concept is that, JS is a 

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
