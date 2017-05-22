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

Crux: 
<There is no real multiple inheritance in JavaScript. Inheritance of property values occurs at run time by JavaScript searching the 
prototype chain of an object to find a value. Because an object has a single associated prototype, JavaScript cannot dynamically inherit  from more than one prototype chain.
In JavaScript, you can have a constructor function call more than one other constructor function within it. This gives the illusion of multiple inheritance. 




