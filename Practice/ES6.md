## Next-gen Javascript (ES6)

### Let and Const
- let & const are different ways of creating variables.
- let - used to store variable values
- const - used to store constant values

> Example:

- let 
```
let myName = "Meg";
console.log(myName); //Meg

myName = "Raj";
console.log(myName);  //Raj
```

> variable is reassigned the value

- const 
```
const myName = "Meg";
console.log(myName); //Meg

myName = "Raj";
console.log(myName);  //Error
```
> const variable can't be reassigned another value


### Arrow functions
They are new next-generation javascript syntax for creating javascript functions.

> Normal javascript function syntax

```
function myFunc() {
    ...
}
```

> ES6 arrow funcion syntax

```
const myFunc = () => {
    ...
}
```

ES6 arrow functions can shorten the javscript function syntax, since it omits `function` keyword and it also solves a lot of issue of `this` keyword in javascript.
When you use `this` inside the arrow function, it will always keep its context and not change in runtime.

`this` keyword is important when we add function to objects.


## Practice time!
```
function printMyName(name) {
    console.log(name);
}
printMyName("Meggie"); //"Meggie"
```

> Rewritten as:
```
const printMyName = (name) => {
    console.log(name);
}
printMyName("Meggie"); //"Meggie"
```

Note: If we're passing only one argument, we can omit the parenthesis too to shorten the syntax. Isn't it wonderful?
```
const printMyName = name => {
  console.log(name);
}
printMyName("Meggie");
```


Similary, make another function -
```
const multiplyNum = num => {
    return num*2
}
console.log(multiplyNum(5)); //10
```

Extra notes: How to do condense the code more?
If there's only one line of code returning something, we can omit the curly braces{} and `return` keyword too, and bring the whole code in one line!

```
const multiplyNum = num => num*2;
console.log(multiplyNum(5)); //10
```


### Understanding `this`

At this point, with React we are dealing with methods, not normal functions. A method is a normal function that is inside (related to) a class or an object (object literal). 

A normal function doesn't have a `this`. For the most part, we won't be dealing with normal functions. Instead of normal functions, we will replace them with arrow functions. 

- When you click a button (a DOM event),  you want the class's `this` to continuously be retained by that class. 
- If the button (event) invokes a method, that method will capture the `this` from that class. You can use bind(),  but that's a different topic. 
- But, if instead of a method, you use an arrow function, the class's `this` will not be captured by that arrow function. This is because arrow functions don't understand what a this is. Arrow functions are a simplified function. 

EXTRA  NOTE: 

The special relationship between a method and a class (or an object), is their `this` relationship. 

Reminder: A normal function & an arrow function don't understand what a this is. 
`this` is like an electrical wire that connects a battery to an electrical device. You can remove the connection from one electrical device and connect that same battery & same wire to a different electrical device. 


### Exports/Imports
- Export default means you're exporting something from a given file.
- While making import statement in another file, it imports the default and only export of the file. Name is upto you!

Example:

> person.js
```
export default person;
```
> app.js
```import Person from person; 
or
import prs from person;
```

- If we write direct export statement/ named exports
> utility.js
```
export const ...
export const ...
```
>app.js

we're importing from 2 different constants so we use curly braces {} to explictely target specific things from the file. Here we have to write the correct name of the constant defined. Name is defined by export.
```
import {base} from utility.js
or import {base as myObject} from utility.js
or import {* as bundled} from utility.js //access with bundled.base etc.
```


### Classes
Classes are blueprints for objects, here javascript objects. A class is created with the `class` keyword and it can have properties and methods.
```
class Person {
    name = "meg", //property
    call = () => {} //method
}
```

- Methods are simply functions attached to classes. Properties are variables attached to class.

- A class is instantiated with a `new` keyword
```
const myPerson = new Person()
```

Called by constructor functions:
```
myPerson.call()
console.log(myPerson.name)
```

- Classes are covenient way of creating constructor functions, so we create js objects with classes as blueprints.

- Classes also support `inheritance` which means you have another class which you inherit from taking all its properties and methods and potentially adding new properties and methods. You might notice them from prototypes.

```
class Person extends Master
```

##### Practice time

In simplest form properties added by adding a constructor which is a default function/method you can add to any class which will be executed whenever you instantiate the class.
Inside the constructor funct., set propeties by `this.___` keyword

Also, add a method in the class to print the name referring to the name property created.

```
class Person {
  constructor() {
    this.name = "Meg"
  }
  
  printMyName() {
    console.log(this.name);
  }
}
```

Use this class to store an instance in a constant, and execute it.
```
const person = new Person();
person.printMyName();
```

##### Practice time - Inheritance

```
class Human {
  constructor() {
    this.gender = "female"
  }
  
  printGender() {
    console.log(this.gender);
  }
}

class Person extends Human {
  constructor() {
    super();
    this.name = "Meg";
    this.gender = "male";
  }
  
  printMyName() {
    console.log(this.name);
  }
}

const person = new Person();
person.printMyName();
person.printGender();

```

Here, even though we're calling printGender(), it prints female, because it's extended by Persons. That means by inheritance we can access parent class' porperties and methods, and apply further changes on them.

 - Must call super constructor in derived class. If you're extending another class, and implementing constuctor method, then you have to add `super method` in the constructor. Its a keyword and it executes the parent constructor to initialize the parent class.

- Classes are used by react to create components.
- Classes are blueprints of javascript obejcts and are very comparable to constructor fucntions, while inheritance is comparable to prototypes