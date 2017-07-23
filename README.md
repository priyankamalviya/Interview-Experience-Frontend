# Interview-Experience-Frontend
A collection of front end interview questions I faced, and their answers. Answers are based on my understanding and/ or taken from the internet. 


## **_JavaScript_**


Q1. Define dependency injection. How is it achieved in JavaScript?
* Dependency injection is a software design pattern that allows someone to remove hard-coded dependencies and makes it possible to change  them. 
* Dependency injection means giving an object its own instance variables. 
* Dependencies can be injected to the object via the constructor or via defined method or a setter property.

Q2. What is multiple inheritance in JavaScript?
The following MDN link has amazing explanation about this topic: 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model

Summary of explanation: 
> There is no real multiple inheritance in JavaScript. Inheritance of property values occurs at run time by JavaScript searching the 
> prototype chain of an object to find a value. Because an object has a single associated prototype, JavaScript cannot dynamically inherit  from more than one prototype chain.
> In JavaScript, you can have a constructor function call more than one other constructor function within it. This gives the illusion of 
> multiple inheritance. 

Q3.  == Vs ===
* The simplest way of saying that, == will not check types and === will check whether both sides are of same type. So, == is tolerant. But under the hood it converts to its convenient type to have both in same type and then do the comparison.
* === compares the types and values. Hence, if both sides are not same type, answer is always false. For example, if you are comparing two strings, they must have identical character sets. For other primitives (number, boolean) must share the same value.
* Rule for implicit coercion: Comparison by using == does implicit type conversion under the hood. And rules for implicit coercion are as follows-
- If both operands are same type use ===
undefined == null
- If one operands is string another is number, convert string to number
- If one is boolean and another is non-boolean, convert boolean to number and then perform comparison
- While comparing a string or number to an object, try to convert the object to a primitive type and then try to compare
- Be careful while comparing objects, identifiers must reference the same objects or same array.
```
var a = {a: 1};
var b = {a: 1};
a == b //false
a === b //false

var c = a;
a == c//true
a === c //true
```
Q4. What are the most unique features of JavaScript?
* Prototypal inheritance (read OLOO)
* Functional programming 
* https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3

Q4. Can array be multi dimensional in JavaScript?
* NO, however, like most C languages it can have an array of arrays
* Example:
    ```
    var matrix = [
      [0,1,2],
      [55,21,9],
      [3, 7, 10]
    ];
    
    console.log(matrix [1, 2]); // 9 
   ```
 
Q5. Lets say there is an object arr. How will you confirm it is an array?

```
let arr = [9, 1, 8, 7, 3, 4, 12];
Object.prototype.toString.apply(arr);
```
* If the above returns "[object Array]", it is an array.

Q6. Mention different ways in which JavaScript objects can be created.
-------
1. Using the Object() constructor:
  ```
  let obj = new Object();   //now discouraged
  ```
2. Using Object.create() method
```
let obj = Object.create(null);
```
3. Using the brackets syntactic sugar
```
let obj = {};
```
4. Using a function constructor
```
var Obj = function(name){
    this.name = name;
}
let temp = new Obj("Heya!!!");
```
5. Using constructor + prototype
```
function myObj(){};
myObj.prototype.name = "Hello";
let temp = new myObj();
```
6. Using ES6 class syntax:
```
class myClass{
    constructor(name){
        this.name = name;
    }
}
var temp = new myClass("Hello");
```
7. Singleton pattern
```
let temp = new function(){
    this.name = "hello"
}
```
Q7. What is so great about React ?
* React is based on the flow architecture
* Here model is the single source of truth 
* Follows 1 way data binding that removes complexity in state management

Q8. Design and implement a modal with form and submit the data using JavaScript
This could have varius possible answers. The gist below could be one possible one:
* https://gist.github.com/havvg/3226804

I was asked a follow up question: How will you allow enter key submit option? 

Q9. How will you print all text in a page?
* This a DOM traversal question. 
* A good solution would be to use querySelector, get reference to a dom element, and then pass it to a function. Start with an empty array, check if child nodes are present. If no child nodes are present, append the nodeValue(here this will provide the text present in that node) of the node to this array. Continue recursing this function till all child nodes are exhausted.

JAVASCRIPT

```
let main = document.querySelector('.container');

function getAllText(node){
  var allText = [];

  function getNodeText(node){
      if(node && node.childNodes && node.childNodes.length){
          for(var i = 0, len = node.childNodes.length; i<len; i++){
              getNodeText(node.childNodes[i]);
          }
      }
      else{
          allText.push(node.nodeValue);
     }
  }
  getNodeText(node);
  return allText.join('');
}


console.log(getAllText(main));
```

HTML

```
<div class="container">
<header><h1>Main Heading</h1></header>
<main>
  <h2>Sub Heading</h2>
  <ul>
    <li>Title 1</li>
    <li>Title 2</li>
    <li>Title 3</li>
    <li>Title 4</li>
    <li>Title 5</li>
  </ul>
</main>
  
</div>
```
Q10. Write a vanilla javascript function to convert the following into links in your page. 
```
var links = {
    "codepen": "www.codepen.io",
    "jsbin": "www.jsbin.com",
    "jsfiddle": "www.jsfiddle.com"
}
```
* Solution:
HTML
```
<section>
<ul id="links"></ul>
</section>
```
JS
```

let links = {
    "codepen": "www.codepen.io",
    "jsbin": "www.jsbin.com",
    "jsfiddle": "www.jsfiddle.com"
}
function displayLinks(){
    let links = document.getElementById('links');
    let key;
    for(key in links){
        links.innerHTML += `<li><a href=${links[key]}>${key}</a></li>`;
    }
}

displayLinks(links);

```

Q11. Write a function that takes a string and a specific character and returns the string without that character.

* Solution:
```
function deleteCharacter(str, i){
  console.log("inside delete now", str, i);
  for(let j=0; j< str.length; j++){  
    if(str[j] === i){
      let newStr = str.slice(0, j) + str.slice(j+1, str.length);
      console.log(newStr);
    }
  } 
}

deleteCharacter("Bhatti", 'h');

```
Q12. Compare 2 arrays and find common values

* Solution

```
let result,
    arr1 = [1, 2, 3, 4],
    arr2 = [2, 3, 6, 9];
    
result = arr1.filter( x => arr2.indexOf(x) !== -1);

console.log(result);

```
Q13. What is the difference between call, apply and bind in JavaScript?
All three methods are used to change the value of this for a given function.
* Call invokes the function and allows you to pass in arguments one by one.
* Apply invokes the function and allows you to pass in arguments as an array.
* Bind returns a new function, allowing you to pass in a this array and any number of arguments.

> Remember which one is which by remembering that Call is for comma (separated list) and Apply is for Array.
> Bind is a bit different. It returns a new function. Call and Apply execute the current function immediately.

Q14. Write a function to find if a string is a palindrome. Find if permutation of the string is palindrome?

* Simple solution to find if a string is palindrome:
```
const isPalindrome = (str) => {
  const reversed = str.split('').reverse().join('');
  return reversed === str;
} 
console.log(isPalindrome('level'));
```

* To check if the permutation of a string is palindrome:
```
const isPermutationPalindrome = (str) => {
  const set = new Set();
  str.split('').forEach( (letter) => {
    // if this letter is found in set, delete it
    if(set[letter]) delete set[letter];
    //if set does not have this letter, add it to set
    else set[letter] = letter;
  });
  // test if the length of keys in set object is at the most 1
  return Object.keys(set).length <= 1;
}
console.log(isPermutationPalindrome('level'));
```

Q15. Write a JS function to find permutation of string:

* The idea is to take one element each in for loop, recursively call the rest elements and concatenate to this element.
```
function permute(str){
  if (str.length<2) return str; // This is the base case
  
  let permutations = []; // resultant string gets stored here
  for(let i =0; i< str.length; i++){
    let letter = str[i];
    
    if(str.indexOf(letter) !== i) continue; // if letter was used earlier, skip it for this iteration
    
    let remaining = str.slice(0, i) + str.slice(i+1,str.length); // '+ ' means concat in JS
    
    for(let subSet of permute(remaining)){
      permutations.push(letter + subSet);      // '+ ' means concat in JS
    }
  }
  
  return permutations;
}

console.log(permute('abc'));
```
