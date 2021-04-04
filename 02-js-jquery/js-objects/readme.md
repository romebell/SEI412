### Objects

Objects, like arrays, store data, but objects are organized differently. Objects store `key: value` pairs, and instead of accessing a value by its index, we access a value by it's associated key. Thus, objects are not ordered like arrays are.

Another name for the keys in an object is **properties**. The keys are said to represent the properties of an object. They hold values that describe those properties for that particular object.

Objects in JavaScript can even hold functions. When a function is a member of an object, it is called a **method**. It is an important nomenclature distinction that can come up in interviews. However, it is easy to remember: if it stands alone, it is probably best called a **function**; if it is the member of a class or object, it is best called a **method**.

#### Creating

The most common way of creating an object is called **object literal syntax**. We bound the object in curly braces `{ }` and literally type our keys and values into them separated by commas:

```js
var friend = {firstName: "Jane", lastName: "Doe"}
```

**Note:** We still use camelCase for the keys in an object.

#### Accessing

There are two ways we can access the properties in an object.

The first, and most common, is called **dot notation** and follows this pattern:

```js
// object.property
// As in the following...

friend.firstName
friend.lastName
```

Or we can use **bracket notation** similar to the way we use arrays. While this isn't quite as pretty, it is very powerful as it allows us to use variables to access the properties, like so...

```js
// We can pass in a string literal that is exactly the name of the key...
friend["firstName"]

// Or we can use whatever value is in this variable...
var myKey = "lastName";
friend[myKey];
```

This gives us a lot of flexibility when accessing keys in an object so it a great one to remember.

#### Adding More Key-Value Pairs

We can add properties, or key-value pairs, even after we've created the object. Simply assigning a value to the key will create the key:

```js
friend.middleName = "Jersey"
```
or with bracket notation:
```js
friend["middleName"] = "Jersey"
```

#### Modifying values

Modifying values is as simple as reassigning a value to that key:

```js
friend.firstName = "John"
```
or
```js
friend["firstName"] = "John"
```

#### Deleting data

It is rare, but you may want to remove an entire key-value pair from an object. This is done with the `delete` instruction:

```js
delete friend.middleName
```
or
```js
delete friend['middleName']
```

#### Methods (functions in objects)

We can add a method to an object as easily as we add a data value. We can either do it when we create the object as a literal:

```js
var mySophisticatedObject = {
  name: "Ulysses S. Grant",
  rank: "General",
  sayHello: function() {
    console.log("Hi!");
  }
}
```

Or we can assign a function to a key after it has been declared:

```js
mySophisticatedObject.sayGoodbye = function() { console.log("Bye!") };
```

To call them, we access the object and the key, but we call it like a function:

```js
mySophisticatedObject.sayGoodBye();
// ==> prints "Bye!" to the console
```

#### Referring to Other Internal Properties - `this`

An object has a way to internally refer to itself. It is the `this` keyword. The concept of `this` can be fairly complicated but used in this capacity is it pretty straightforward. Inside an object, we can use `this.key` to refer to the value in that key in that object:

```js
var firstProgrammer = {
  name: "Ada Lovelace",
  rank: "FIRST!!!",
  brag: function() {
    console.log("I'm " + this.name + " and I'm " + this.rank);
  }
}

firstProgrammer.brag();
// ==> prints "I'm Ada Lovelace and I'm FIRST!!!"
```

#### Looping Over Objects

The **for...in** loop is made for looping through all the key-value pairs in an Object.

```js
var car = {
  wheels: 4,
  doors: 2,
  seats: 5
};
for (var thing in car) {
  console.log("My car has " + car[thing] + " " + thing);
}

// Will print out:
// > My car has 4 wheels
// > My car has 2 doors
// > My car has 5 seats
```

### Exercise

1.) Represent the following values in an object:

````
"John", "Doe", 36, "1234 Park st".
````

2.) Once you've represented the above as an object, update John's address to `1234 Park ln`.

3.) Using a combination of Objects and Array, how would you represent the following data:

```
Moe, Doe, 31, 1234 Park st.
Larry, Doe, 36, 1234 Spark st.
Curly, Doe, 36, 1239 Park st.
Jane, Doe, 32, 1239 Spark st.
Emma, Doe, 34, 1235 Spark st.
Elizabeth, Doe, 36, 1234 Park st.
Elinor, Doe, 35, 1230 Park st.
Mary, Doe, 31, 1231 Park st.
Darcy, Doe, 32, 1224 Park st.
Grey, Doe, 34, 1214 Park st.
Lydia, Doe, 30, 1294 Park st.
Harriet, Doe, 32, 1324 Park st.
```

4.) Mary is taking to the road, so she no longer has an address. Delete her address!
