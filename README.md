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
Q16. Write a function to create DOM tree 
* Solution:
Lets says we have a given object that looks like this: 
```
const TREE_DATA = {
  name: "Root",
  items: [
    {
      name: "Home"
    },
    {
      name: "Downloads",
      items: [{ name: "budget_report.xls" }, { name: "cat_meme.jpg" }]
    },
    {
      name: "Documents",
      items: [
        { name: "foo" },
        { name: "bar" },
        {
          name: "sub_folder",
          items: [
            { name: "hello" },
            {
              name: "world",
              items: [{ name: "countries.db" }]
            }
          ]
        }
      ]
    },
    {
      name: "Users",
      items: [
        { name: "Linda" },
        { name: "Fred" },
        { name: "James" },
        { name: "Karen" }
      ]
    },
    {
      name: "Applications",
      items: [
        { name: "Notepad" },
        { name: "Google Chrome" },
        { name: "Slack" },
        { name: "Adobe Photoshop" }
      ]
    }
  ]
};
```
And we have initial dom ul declared:
```
<ul id="tree"></ul>
```

The function will take dom reference and the obj as parameters and call itself recursively if items are present. Finally the whole tree gets appended to the dom reference.

```
function createDOMTree(el){
    return function(obj){
        let li = `<li><span>${obj.name}</span></li>`;
        if(obj.items){
            let ul = $('ul').appendTo(li);
            obj.items.forEach(createDOMTree(ul));
        }
        el.append(li);
    };
};

createDOMTree($('#tree'))(TREE_DATA);
```

* I found a similar problem in this [link](https://stackoverflow.com/questions/44586038/recursive-javascript-function-to-return-detail). This is a popular interview question!

Q17. Write a function to find Fibonacii sum.
* This is a very common problem.
* You get extra points if you optimize the solution using memoization.
* Simple Solution: 
```
function fib(num) {
    if n<2 return n;
    else return (fib(n-1) + fib(n-2));
}
```
This indeed is a super simple problem, but I was asked this question during onsite interview of one of the top 4 companies. The motive of the interviewer was to judge if I was capable of breaking down a problem to simplest parts and solve with absolute clarity. A programmer's job is not just programming, but finding out the most optimal solution to a problem and being able to communicate the explanation in a crisp and concise manner :). 

[Click here](https://www.youtube.com/watch?v=zg-ddPbzcKM) to find a Khan Academy link that explains this algorithm very clearly. I found this explanation to be very helpful. 
```
function fibonacii(num, memo){ 
  memo = memo || {};
  if(memo[num]) return memo[num];
  
  if(num <= 1 ) return 1; // base case
  
  return memo[num] = fibonacii(num-1, memo) + fibonacii(num-2, memo);
}

console.log(fibonacii(9));
```

Q18. Implement the fizzbuzz problem.
*  The fizzbuzz problem:
if a number is a multiple of 3, print fizz
if a number is a multiple of 5, print buzz
if a number is a multiple of both 3 & 5, print fizzbuzz

* Solution in es6:
```

for(let i =1; i< 101; i++){
  const isFizz = i % 3 === 0;
  const isBuzz = i%5 === 0 ;
  
  const isFizzBuzz = i % 3 === 0 && i % 5 === 0;
  const result = isFizzBuzz
            ? 'FizzBuzz'
            : isFizz
            ? 'Fizz'
            : isBuzz
            ? 'Buzz'
             : i;
      
  console.log(result);

}
```

Recently I learnt about Array.from() and wrote a simpler (1 Line! :D) script to the problem:

```
const fizzbuzz = Array.from(Array(100).keys()).forEach(x => {
     (x%3 && x%5) ? console.log("FizzBuzz")
    : x%5 ? console.log("Buzz")
    : x%3 ? console.log("Fizz") 
    : null;
  }
  );
```
Q19. Write a function to convert a string to an integer
* Solution in es6 (Typescript)
 ```
const stringToInteger = (str: string): number => {
  const firstCode = "0".charCodeAt(0);

  let sign = 1;
  if (str[0] === "-") {
    str = str.substring(1);
    sign = -1;
  }

  let count = 0;
  for (const char of str) {
    count = count * 10 + (char.charCodeAt(0) - firstCode);
  }

  return sign * count;
}

console.log(stringToInteger("999")); // 999
console.log(stringToInteger("-023")); // -23
 ```
Q20. Write a function to merge 2 objects in JavaScript.
* Solution
```
var mergeObjects = function (obj1, obj2) { 
  /* function to check if parameters passed are objects*/
  function isObject(obj){
    return obj instanceof Object;
  }
  
  /* iterate through each key of the second object passed. */
    for (let key in obj2) {
      /* check if both parameters are still objects */
            if (obj1[key] && isObject(obj1[key]) && isObject(obj2[key])) {
              /* recurse through them if they are objects*/
                mergeObjects(obj1[key], obj2[key]);
            } else {
              /* if any of these 3 conditions, ie, this key just not exist in obj1, AND, this key exists in obj1 AND this key exists in obj2 turn false, assign this key & value to obj1 */
                obj1[key] = obj2[key];
            }
    }
  //finally return obj1
    return obj1;
};


/* pass on the 2 objects you want to merge */
console.log(mergeObjects({
  a: {
    b: {
      c: 0
    }
  },
  d: 1
}, {
  a: {
    b: {
      d: 2
    }
  },
  e: 3
}));


/* ==================== solution using Object.assign ======================= */
let obj1 = {
  a: {
    b: {
      c: 0
    }
  },
  d: 1
};

let obj2 = {
  a: {
    b: {
      d: 2
    }
  },
  e: 3
};

/* simple method that does the same thing*/
let result = Object.assign({}, obj1, obj2);

console.log(result);
```
Q21. What is reflow? What causes forced reflow?
* Solution:
When you change size or position of an element in the page, all the elements after it has to change their position according to the changes you made. For example, if you change height on an element, all the elements under it has to move down in the page to accomodate a change in height. Hence, flow of the elements in the page is changed and this is called reflow.
**Why reflow is bad**: Reflows could be very expensive and it might have a performance hit specially in the smaller devices like phone. As it might causes changes in the portion (or whole) layout of the page.

Q22. What do you understand by specificity?

* Solution:

Specificity is the means by which browsers decide which CSS property values are the most relevant to an element and, therefore, will be applied. Specificity is based on the matching rules which are composed of different sorts of CSS selectors.
The following list of selector types increases by specificity:

Type selectors (e.g., h1) and pseudo-elements (e.g., :before).
Class selectors (e.g., .example), attributes selectors (e.g., [type="radio"]) and pseudo-classes (e.g., :hover).
ID selectors (e.g., #example).

Q23. Explain event delegation
* Solution:
1. relates to DOM events
2. JavaScript event listeners fire not only on a single DOM element but on all of its descendants
3. Event bubbling or propagation is the inverse of event delegation (events on an element bubble up and fire on all parents)

Q24. You have an array of objects containing pairs of partners. Find out the single one!

* Solution:

// The solution is quite simple. Lets say our array is:

```
partners: [
    {
        "partner1": "Tom",
        "partner2": "Monika"
    },
        {
        "partner1": "Jill",
        "partner2": ""
    },
        {
        "partner1": "Sam",
        "partner2": "Tina"
    },
        {
        "partner1": "Kim",
        "partner2": ""
    }
];

console.log(partners.filter(partner => partner.partner2.length));
```

Array .filter() method returns filtered object if the return is truthy, or else ignores. Here if we check length of partner2, we can filter pairs based on truthy or falsy values-> empty length of partner 2 means, that object needs to be ignored. Very simple problem, tests thought process!

