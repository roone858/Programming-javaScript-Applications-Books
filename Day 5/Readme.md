## JavaScript Object Properties
Properties are the most important part of any JavaScript object.
### JavaScript Properties
Properties are the values associated with a JavaScript object.
### Accessing JavaScript Properties
The syntax for accessing the property of an object is:

```javascript 
objectName.property      // person.age
```
or
```javascript 
objectName["property"]   // person["age"]

```
or
```javascript 
objectName[expression]   // x = "age"; person[x]

```


A JavaScript object is a collection of unordered properties.

Properties can usually be changed, added, and deleted, but some are read only.
## Objects :
- In JavaScript, all types of functions, arrays, key/value pairs, and data structures in general
are really objects.
- JavaScript has one of the most flexible and expressive object systems available in any popular programming language
- so that you can call their prototype methods. For example:



``` javascript
'mahmoudg.dev@gmail.com'.split('@')[1]; 
```
```
gmail.com
```
- You simply  don’t need all of the common cruft to accomplish the stated goals. For instance, because  JavaScript is classless

## Classical Inheritance Is Obsolete
In Design Patterns: Elements of Reusable Object Oriented Software, the Gang of Four
opened the book with two foundational principles of object-oriented design :
1.  Program to an interface, not an implementation.
2. Favor object composition over class inheritance.

Think of it this way: classical inheritance is like Ikea furniture. You have a bunch of pieces
that are designed to fit together in a very specific way. If everything goes exactly ac‐
cording to plan, chances are high that you’ll come out with a usable piece of furniture;
but if anything at all goes wrong or deviates from the preplanned specification, there is
little room for adjustment or flexibility. Here’s where the analogy (and the furniture and
the software) breaks down: the design is in a constant state of change.
## Fluent-Style JavaScript
- Programmers with a background in other languages are like immigrants to JavaScript.
- , programmers with a background in classical OO tend to have a hard time letting constructors go .
- Using constructor functions is a clear and strong accent, because they are completely unnecessary in JavaScript
- Unfortunately, most JavaScript learning materials will teach you that you build objects using constructor functions
- You’re ignoring two of the best features of JavaScript:
   1. dynamic object extension (you can add properties
to any object in JavaScript after instantiation) and prototypal inheritance.
  1. The two combined are a much more powerful and flexible way to reuse code than classical
inheritance

## prototypes
- All JavaScript objects inherit properties and methods from a prototype
- The JavaScript prototype property allows you to add new properties or new method to object constructors:
```javascript
  function Person(first, last, age, eyeColor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyeColor;
}
Person.prototype.nationality = "English";
  ```

  All JavaScript objects inherit properties and methods from a prototype:

Date objects inherit from Date.prototype
Array objects inherit from Array.prototype
Person objects inherit from Person.prototype
The Object.prototype is on the top of the prototype inheritance chain:

Date objects, Array objects, and Person objects inherit from Object.prototype.


- It is similar to a class in that you can use it to construct any number of object instances
- but different in the sense that it is an object itself
- There are two ways that prototypes can be used:
   1. you can delegate access to a single, shared prototype object (called a delegate)
   2. or you can make clones of the prototype.

### Delegate Prototypes

  In JavaScript, objects have an internal reference to a delegate prototype
  - When an object is queried for a property or method :- 
      1.  the JavaScript engine first checks the object
      2.  If the key doesn’t exist on that object, it checks the delegate prototype
      3.  and so on up the prototype chain. The prototype chain typically ends at the Object prototype.
  
When you invoke a constructor with the new keyword, the object referenced by the constructor’s prototype property gets set as the delegate for the newly created object.
- As you can see, this Object.create() polyfill is simply a shortcut that creates a new constructor function
- sets the object you pass in as the constructor’s prototype property
- and then returns a new object with that prototype. Here’s how you use it:

```javascript
var switchProto = {
    isOn: function isOn() {
      return this.state;
    },
    toggle: function toggle() {
      this.state = !this.state;
      return this;
    },
    state: false,
  },
  switch1 = Object.create(switchProto),
  switch2 = Object.create(switchProto);
switch1.state = true;
console.log(switch1.isOn());
console.log(switch2.isOn());
```
```
true
false
```
changing state on switch1 did not change state on switch2

### Prototype Cloning
- Sometimes you don’t want to share data on a prototype property
- Instead, you want each instance to have its own unique copy of the prototype’s properties
- Popular JavaScript libraries have been shipping with a suitable method for cloning prototypes 
- Unfortunately, extend() is not included in the JavaScript 
- The cloning method is usually called .extend()
- extend() is included in both jQuery and Underscore