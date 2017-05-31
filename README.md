# Interview-Experience-Frontend
A collection of front end interview questions I faced and their answers. Answers are based on my understanding and/ or taken from the internet. 


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
