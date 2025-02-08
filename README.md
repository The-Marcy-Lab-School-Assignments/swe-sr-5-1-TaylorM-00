# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Imagine you are teaching a friend about OOP. They mainly want to understand what is Encapsulation. Write a brief lesson on Encapsulation that includes the following:

- What is encapsulation?
- What major goal does this help to achieve in software engineering?
- Give an example (in code) of encapsulation.
- An explanation of how the code example demonstrates encapsulation

### Response 1

- Encapsulation is grouping related functions or variables together while we hide and protect the data. A major goal this helps achieve is that we reduce complexity, hide our data, increase reusability and we can get more accurate outcomes.
  Encapsulation code:

```js code
//building our class! we will be using a person class for this example
class Person {
  //we are always going to pass in a name
  constructor(name) {
    //declaring the name we are passing will belong to ‘this’ person
    this.name = name;
  }
  //our function!
  sayHi() {
    //if we call this function correctly we should recieve a ‘hi, i’m (your name)’
    console.log(`hi, i'm ${this.name}`);
  }
}
// we are declaring a new person here, (i’m Ells lol)
const Ells = new Person(“Ells”);
//and i want to say hi!
Ells.sayHi();
//Ben wants to say hi, but would he be able to?
ben.sayHi();
//here we declare Taylor as a new person!
const Taylor = new Person(“Taylor”);
//and she’s able to use the code we have previously written so no need to rewrite it!
Taylor.sayHi();
```

code explanation:
In the code we are seeing how classes are used to keep the data safe. Both Ells and Taylor can access the inner sayHi() function and give us back a console log BUT Ben isn’t able to. Why? Because he was not given permission to access the sayHi function. If we wanted Ben to be able to sayHi() we would simply have to write in:

```js
const Ben = new Person(“Ben”);
```

## Prompt 2

The following `friendsManager` object is an example of an interface that is **NOT** consistent and predictable:

```js
const friendsManager = {
  friends: [],
  addFriend(newFriend) {
    if (typeof newFriend !== "string") return;
    this.friends.push(newFriend);
  },
};

friendsManager.addFriend("daniel");
friendsManager.addFriend(true);
friendsManager.friends.push("emmaneul");
friendsManager.friends.push(42);
```

Explain how the code is not consistent or predictable, then provide an example in code that uses closure to make it more consistent and predictable.

### Response 2

- The code is not consistent or predictable because we see that we are able to add friends through friendsManager using addFriend just like we want and true won’t be passed because we clarified we only want strings. Yet, when we get friends.push we are STILL able to pass friends through! We completely override the fact that we !!!ONLY!!! wanted to add it using addFriend.

```js
//here we are creating a friendsManager class!
class friendsManager {
  //we are starting with *some* friends
  friends = [“taylor”, “ben”];
  //declaring our name ^^
  constructor(name) {
    //name
    this.name = name;
  }
  //our function that will add a new friends name
  addFriend(friend) {
    //we will be pushing our new friend into THIS friends array
    this.friends.push(friend);
    //if it works we will console log that it worked
    console.log(`${friend} has been pushed!`);
  }
  //so we can look at our friend array
  returnFriends() {
    return [...this.friends];
  }
}
//declaring myself
const ells = new friendsManager(“ells”);
//adding gonzalo as my friend
ells.addFriend(“gonzalo”);
//returning our friend array back with. . .Gonzalo in it!
console.log(ells.returnFriends());
//why cant ben add a friend?
//ben doesnt have access to our functions and data inside! sorry ben :(
ben.addFriend(“gonzalo”);
//even though he’s in the array? yes! because he doesn’t have a instance (‘this’) made for him
ben.returnFriends();
```

## Prompt 3

With OOP in JavaScript, it's possible to use factory functions to achieve encapsulation and re-use them to make objects that look alike. However, factory functions have drawbacks and we often use classes instead.

How would you explain to a budding developer what the drawbacks of using factory functions are and why it is better to use classes instead?

### Response 3

- While with both factory functions and classes allows for users to create objects that hold information that can be repeated and reused.
  When using a factory function it works as a function that will create not only a new object but recreates the same methods as well. This only leads to an increased and unnecessary use of storage.
  It would be better for a user to use a class not only for the amount of storage saved but when creating a new instance, the methods will be inherited allowing subclasses to have access and draw from the main class.

## Prompt 4

Do some research on the history of when / how classes were introduced into JavaScript and share your findings. Your response should include:

- What version of JavaScript were classes introduced in and when did it come out?
- Why were classes introduced into JavaScript?

### Response 4

- Classes was first introduced in 2015 during the ECMAScript 6 update, which was a second major revision to JavaScript.
  Classes where first created as a template to create multiple objects

## Prompt 5

OOP can still be achieved in JavaScript without using the `class` keyword and instead using the "Constructor Functions" and the "Prototype Chain" (look them up!)

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function () {
  return `Hi, I'm ${this.name}, and I'm ${this.age} years old.`;
};

const alice = new Person("Alice", 30);
console.log(alice.greet());
```

Provide one point that advocates for the use of this syntax and then provide a counter-argument for the use of classes instead.

### Response 5
