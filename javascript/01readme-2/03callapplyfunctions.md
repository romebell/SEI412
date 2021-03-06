# Call, Apply, and other Functions

### `call`

Call and apply are two functions that allow us to change what `this` represents. This is why `this` can be difficult to deal with in JavaScript.

**Example 1:**

```javascript
const getAge = function(friend) {
  return friend.age;
};

const john = { name: 'John', age: 21 };
getAge(john);
```

rewritten using `call`

```javascript
const getAge = function() {
  return this.age;
};

const john = { name: 'John', age: 21 };
getAge.call(john);
```

**Example 2:**

```javascript
const setAge = function(friend, newAge) {
  friend.age = newAge;
};

const john = { name: 'John', age: 21 };
setAge(john, 35);
```

rewritten using `call`

```javascript
const setAge = function(newAge) {
  this.age = newAge;
};

const john = { name: 'John', age: 21 };
setAge.call(john, 35);
```

### `apply`

`apply` works just like `call`, but your second parameter is an array of objects instead of a comma separated list.

Going back to Example 2, here's what it would look like with `apply`.

```javascript
const setAge = function(newAge) {
  this.age = newAge;
};

const john = { name: 'John', age: 21 };
setAge.apply(john, [35]);
```

### Calling on a solution

Let's talk about using `call` or `apply` to set the `this` context for a function before it is run.

```javascript
function Person(name) {
  this.name = name;
  this.friends = [];
}

Person.prototype.addFriend = function(name) {
  this.friends.push(new Person(name));
};

function Student(name, course) {
  // masks all the constructor properties including name (as the second parameter)
  Person.call(this, name);
  this.course = course;

  // If we wanted to, we could also use .apply like so:
  // Person.apply(this, [name]);
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;
```

The code above is why we forgo talking about `this` until now. In the context of event listener callbacks, `this` refers to the DOM element that trigged the event. But here, `this` can _really be anything you want it to be_.

Still confused? [Understanding `this` once and for all](https://journeyintojavascript.quora.com/understanding-this-once-and-for-all)

## Useful methods when working with inheritance

### `hasOwnProperty`

Object.hasOwnProperty\('nameOfProperty'\) - always make sure the name of the property is in quotes. Classes that inherit from other classes will also return true if the property is checked.

Example 1

```javascript
const taco = {
  food: 'taco'
}

taco.hasOwnProperty(food); // returns an error
taco.hasOwnProperty('food'); // returns true
```

Example 2 with inheritance

```javascript
function Person(name) {
  this.name = name
}

Person.prototype.greet = function() {
  return 'Hello, my name is ' + this.name;
};

function Student(name, course) {
  Person.call(this, name);
  this.course = course;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

const person = new Person('Bob');
const student = new Student('Tom', 'SEI');

person.hasOwnProperty('name'); //returns true
student.hasOwnProperty('course'); //returns true
student.hasOwnProperty('name'); //returns true
```

### `instanceof`

This method is a bit more common, and the syntax looks like this:

`object instanceof Class`

Example 1:

```javascript
const color1 = {};
color1 instanceof Object; // returns true
```

Example 2 with inheritance

```javascript
function Person(name) {
  this.name = name
}

Person.prototype.greet = function() {
  return 'Hello, my name is ' + this.name;
};

function Student(name, course) {
  Person.call(this, name);
  this.course = course;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

const p = new Person('Bob');
const s = new Student('Tom', 'SEI');

s instanceof Person //returns true
p instanceof Student //returns false
Person instanceof Object //returns true
String instanceof Object //returns true
Object instanceof Boolean //returns false
```

### `isPrototypeOf`

This method is used a bit less frequently, but the syntax looks like this:

```javascript
Object.prototype.isPrototypeOf(objectInstance);
```

Example:

```javascript
const p = new Person('Bob');
const s = new Student('Tom', 'WDI');

Person.prototype.isPrototypeOf(s); // returns true
Student.prototype.isPrototypeOf(p); // returns false
```

You can read more about the difference between isPrototypeOf and isInstanceOf [here](http://stackoverflow.com/questions/2464426/whats-the-difference-between-isprototypeof-and-instanceof-in-javascript)

