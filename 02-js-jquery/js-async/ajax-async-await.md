<img src="https://i.imgur.com/VqMhmBL.png">

---
## Learning Objectives
<br>

<p>Students Will Be Able To:</p><br>

- Describe the Use Case for AJAX
- Use ES2017's `async`/`await` to handle promises synchronously

---
### Roadmap
<br>

1. Setup
2. AJAX - What & Why
3. Make an HTTP Request Using the Fetch API
4. Use ES2017's `async`/`await` to Handle Promises

---
#### Setup
<br>

- We'll be using [Repl.it](https://repl.it) during this lesson to learn about AJAX and `async`/`await`.

- Create a new HTML, CSS, JS repl and name it something like **AJAX with Fetch**.

---
#### AJAX - What & Why
<br>

- **AJAX** is short for **Asynchronous JavaScript And XML**.

- In case you're wondering what the [XML](https://en.wikipedia.org/wiki/XML) is about... It's the granddaddy of all markup languages, including HTML.

- Once upon a time, XML was the de facto format for transferring data between two computers - that's why it's in the name AJAX. However, **JSON** has since become the data transfer format of choice.

---
#### AJAX - What & Why
<br>

- Clients (browsers) use **AJAX** to make HTTP requests using JavaScript.

- The browser can send AJAX requests to any API server, as long as the server is [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) compliant.

- Using AJAX, we can send an HTTP request that uses any HTTP method including, `GET`, `POST`, `PUT` & `DELETE` - no need for `method-override`!

---
#### AJAX - What & Why
<br>

- But, here's the best part - unlike when we click a link or submit a form on a web page, AJAX does not trigger a page reload!

- We can use AJAX to communicate with servers to do lots of things, including to read, create, update & delete data without the user seeing a page refresh.

- AJAX has made possible the modern-day Single Page Application (SPA) like what you're going to build during this unit!

---
#### AJAX - What & Why
<br>

- AJAX was originally made possible back in 1998 when IE5 introduced the `XMLHttpRequest` (XHR) object and today it's in all browsers. However, it's a bit clunky to use.

- One of the reasons jQuery became popular was because it made making AJAX requests easier.

- However, we no longer have to use the XHR object or load jQuery to make AJAX calls thanks to the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) which is part of the collection of [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API) included in modern browsers.

---
#### Make an HTTP Request Using the Fetch API
<br>

- So, the **A** in AJAX stands for **asynchronous**.

- Indeed, making an AJAX request is an asynchronous operation. So far, we've seen two approaches that enable us to run code after an asynchronous operation has completed. <br>❓ **What are they?**

---
#### Make an HTTP Request Using the Fetch API
<br>

- The Fetch API, like any new Web API asynchronous method, uses promises instead of callbacks.

- Let's make a `GET` request to the `/users` endpoint of [JSONPlaceholder](https://jsonplaceholder.typicode.com/), a fake RESTful API for developers:

	```js
	fetch('https://jsonplaceholder.typicode.com/users')
	.then(response => console.log(response))
	```
	When ran, we'll see that the `fetch` method returns a promise that resolves to a Fetch [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response) object, which has properties such as `status`, etc.

---
#### Make an HTTP Request Using the Fetch API
<br>

- To obtain the data in the body of the response, we need to call either the `text` or `json` method which returns yet another promise:

	```js
	// fetch defaults to making a GET request
	fetch('https://jsonplaceholder.typicode.com/users')
	.then(response => response.json())
	.then(users => console.log(users))
	```
	As you can see, the `json()` method returns a promise that resolves to the data returned by the server, as JSON.

---
#### Use ES2017's async/await to Handle Promises
<br>

- Before we continue to use `fetch` any further, let's see how to use a fantastic new way of working with promises:<br>[async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) & [await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)

- The purpose of `async`/`await` is to allow us to work with asynchronous code almost as if it were synchronous!

---
#### Use ES2017's async/await to Handle Promises
<br>

- We use the `async` declaration to mark a **function** as asynchronous when promises are going to be handled using `await` within it.

- We can re-write our code to use `async`/`await` like this:

	```js
	async function printUsers() {
	  const endpoint = 'https://jsonplaceholder.typicode.com/users';
	  let users = await fetch(endpoint).then(res => res.json());
	  console.log(users);
	}
	
	printUsers();
	```
	The `await` operator causes the line of code with `fetch` to "pause" until the promise resolves with its value - in this case an array of users.

---
#### Use ES2017's async/await to Handle Promises
<br>

- When using `async`/`await`, we cannot use a `.catch()` to handle a promise's rejection, instead we use JavaScripts's `try`/`catch` block:

	```js
	async function printUsers() {
	  const endpoint = 'https://jsonplaceholder.typicode.com/users';
	  let users;
	  try {
	    users = await fetch(endpoint).then(res => res.json());
	    console.log(users);
	  } catch(err) {
	    console.log(err);
	  } 
	}
	```
	The `catch` block would run if the `fetch` failed.

---
#### Use ES2017's async/await to Handle Promises
<br>

- So basically, we've seen that `async`/`await` replaces the `.then(<function>)` method for when a promise resolves.

- In addition, JavaScript `try`/`catch` blocks replace the `.catch(<function>)` for error handling when a promise is rejected.

---
#### 💪 Practice Exercise (2 MIN)
<br>

- After the `console.log(users)`, add another AJAX request using `fetch` to JSONPlaceholder's `/posts` endpoint.

- Log out the returned posts.

---
#### References
<br>

- [MDN - Async Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

- [MDN - Await Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
