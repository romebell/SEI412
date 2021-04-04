# Create React App

### Learning Objectives

_After this lesson, you will be able to:_

* Build a React app using `create-react-app`
* View `create-react-app` working locally

## Initial Setup

Let's jump right in! We'll create a skeleton React project and walk through it as we go.

An easy way to start React projects is to use a Terminal program called [`create-react-app`](https://reactjs.org/docs/create-a-new-react-app.html). This excellent tool, created by Facebook, will help you set up a bare-bones React app instantly. Check out the docs to see how to start a new `create-react-app`!

We'll call the example app "hello\_world", since that'll be our first project.

```bash
$ npx create-react-app hello_world
```

Read more about npx [here](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b).

The tool creates a new directory for your app, so move into it...

```bash
$ cd hello_world
```

Use `npm start` to start a server that will serve your new React application!

```bash
$ npm start
```

> You have now set up a Hello World app that you will continue working on during this lesson's exercises!

After running `$ npm start`, it will open your new app in your default browser at `http://localhost:3000`.

> Note: If you ever need to stop the server, you can hit `ctrl-c` in the terminal window.

## Stop / Catch Up / Investigate

Take some time and look at what's been generated. Specifically pay attention to `src/App.js` and `src/index.js`

Make small changes to the code in `src/App.js`, `src/index.js`, and `public/index.html` just to see what happens.

You'll notice the web page for our app automatically refreshes every time we save a file in the directory. This is an awesome feature of `create-react-app`

Your basic React app is up and running. Now you're ready to add complexity.

