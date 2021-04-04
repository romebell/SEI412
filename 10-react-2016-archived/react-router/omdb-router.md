#OMDB with React Router

In order ease into React Router, we're going to use a familiar API: OMDB. We'll
use this API to create a simple application with multiple routes.

###Getting Started

Fork and clone the starter repo below to get started.

https://github.com/WDI-SEA/react-omdb


###The App

* `/` - home page with a search form, to display results
* `/results/:imdbID` - page to see movie details
* `/about` - a static about page


##OMDB Search Component

After verifying that the starter code runs, let's make a `OMDBSearch` component
inside a new file `src/components/OMDBSearch.jsx`. It should contain the
following:

* React
* A new React component
  * a `render` function to render some text
* Module export

```js
import React, { Component } from 'react';

class OMDBSearch extends Component {
  render () {
    return (
      <div>
        <h1>Search for Movies</h1>
      </div>
    );
  }
}

module.exports = OMDBSearch;
```

##About Component

Let's also make an `About` component for our About page. It will be very
similar to the component above, inside a new file `src/components/About.jsx`,
only it will say **About**.

```js
import React, { Component } from 'react';

class About extends Component {
  render () {
    return (
      <div>
        <h1>About</h1>
        <p>Movie searching!</p>
      </div>
    );
  }
}

module.exports = About;
```

Modify `src/app.jsx` to render these components.

```js
import React, { Component } from 'react';
import About from './About';
import OMDBSearch from './OMDBSearch';

class App extends Component {
  render () {
    return (
      <div>
        <OMDBSearch />
        <About />
      </div>
    );
  }
}

export default App;
```

**Once finished**, run `npm start` and navigate to the page. The two components
should render on the page.

##React Router

Now, let's make this a little more useful by installing `react-router`, in
order to get the `OMDBSearch` and `About` components to appear on different
pages.

```
npm install --save-dev react-router
```

Then, require the following dependencies from `react-router` in `src/app.jsx`.

```js
const Router = require('react-router').Router
const Route = require('react-router').Route
const Link = require('react-router').Link
const browserHistory = require('react-router').browserHistory;
```

These will give us the necessary modules to add **routing** to the application.
Let's add the `Router` and set up `Routes` in the `render` function inside
`App`.

```js
class App extends Component {
  render () {
    return (
      <Router history={browserHistory}>
        <Route path="/" component={OMDBSearch} />
        <Route path="/about" component={About} />
      </Router>
    );
  }
}
```

This is what we need to set up our Router. The `Router` component contains the
routes and history for our frontend routes. Each `Route` component contains a
path and a component to render for that route.

Try navigating to `http://localhost:3000` and `http://localhost:3000/about` and
see if the routes work.

##Search Route

We're missing one route, the route for search results. We'll need one more
component for that route, so let's make a component called `ShowMovie` in
`/src/components/ShowMovie.jsx`.

```js
import React, { Component } from 'react';

class ShowMovie extends Component {
  render () {
    return (
      <div>
        <h1>imdbID: {this.props.params.imdbID}</h1>
      </div>
    );
  }
}

module.exports = ShowMovie;
```

In the Router, we'll be able to pass parameters through the route, and they'll
be available through `props`! Completing the Router:

The complete `/src/app.jsx`

```js
import React, { Component } from 'react';

import About from './About';
import OMDBSearch from './OMDBSearch';
import ShowMovie from './ShowMovie';

const Router = require('react-router').Router
const Route = require('react-router').Route
const Link = require('react-router').Link
const browserHistory = require('react-router').browserHistory;

class App extends Component {
  render () {
    return (
      <Router history={browserHistory}>
        <Route path="/" component={OMDBSearch} />
        <Route path="/about" component={About} />
        <Route path="/results/:imdbID" component={ShowMovie} />
      </Router>
    );
  }
}

module.exports = App;
```

Before moving forward, make sure the routes we defined render components. Our
next step will be adding movie search functionality to `OMDBSearch` and
`ShowMovie`.

