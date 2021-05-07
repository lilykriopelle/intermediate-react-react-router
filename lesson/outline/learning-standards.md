## What is React Router?

### Learning Standard Text

React Router is a library that provides navigational components for React Developers to create Single-Page Applications (SPAs) with dynamic, client-side routing. Applications that use React-Router can benefit from the separation of content afforded to multi-page applications without the break in the user-experience caused by a new page loading.

### Tags

JavaScript, React, React Router

### Additional Notes / Resources Used

- https://reactrouter.com/

<hr>

## Installing React Router

### Learning Standard Text

To install React Router with `npm`, use the following command:

```sh
npm install react-router-dom
```

> Note: An equivalent package called `react-router-native` may be used in order to create a React Native application.

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used
- https://reactrouter.com/web/guides/quick-start

<hr>

## The `<BrowserRouter>` component

### Learning Standard Text

In order to use React Router, the `BrowserRouter` component must be imported into the top-level component file from `react-router-dom`. This component is often renamed to just `Router`.

This `<Router>` component then wraps the entire top-level component, giving all descendants of this component access to React Router:

```js
// App.js
import React from "react";
import { BrowserRouter as Router } from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <h1> Hello World </h1>
      </div>
    </Router>
  );
}
```

### Tags
JavaScript, React, React Router


### Additional Notes / Resources Used
- https://reactrouter.com/web/guides/quick-start

<hr>

## Basic Routing with `<Route>`

### Learning Standard Text

The `<Route>` component from the `react-router-dom` library creates new "pages" within an application by rendering some UI when its path matches the current URL. 

Unless specified with the `exact` attribute, all `<Route>` components whose `path` matches the beginning of the current URL will be rendered. 

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used


In this example, if a user were to navigate to the index page `/`, they would see "Hello World". If they were to navigate to the `/about` page, they would instead see "I'm a React developer!". 

In this example, if the `exact` attribute were removed from the first `<Route>` component, both `<h1>` elements would be rendered when the user navigates to `/about`.

```js
// App.js
import React from "react";
import { BrowserRouter as Router, Route } from "react-router-dom";

export default App = () => {
  return (
    <Router>
      <div>
        <Route exact path={'/'}>
          <h1> Hello World </h1>
        </Route>
        <Route path={'/about'}>
          <h1> I'm a React developer! </h1>
        </Route>
      </div>
    </Router>
  );
}
```

- https://reactrouter.com/web/guides/quick-start

<hr>

## Navigation UI with `<Link>`

### Learning Standard Text

The `<Link>` component from React Router is used to create navigation links in your application. Rendering a `<Link>` in your application will render an anchor (`<a>`) in your HTML document, though the anchor's default behavior of triggering a page reload will be disabled.

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used

Example:

```js
<Link to="/about">About</Link>
// Rendered: <a href="/about">About</a>
```

- https://reactrouter.com/web/guides/primary-components
<hr>

## Navigation UI with `<NavLink>`

### Learning Standard Text

The `<NavLink>` component from React Router is a special type of `<Link>` that can be assigned an `activeClassName` prop when its `to` prop matches the current location.

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used

Example:

```js
<NavLink to="/home" activeClassName="huzzah">
  Home
</NavLink>
<NavLink to="/about" activeClassName="huzzah">
  About
</NavLink>

// When the URL is /about, this renders:
// <a href="/home">Home</a>
// <a href="/about" className="huzzah">Home</a>
```

- https://reactrouter.com/web/guides/primary-components
<hr>


## URL Parameters and `useParams()`

### Learning Standard Text

URL parameters are are dynamic segments of a `<Route>` component's `path` prop used by React Router to dynamically serve resources based on the current window location. 

The `useParams()` hook from the `react-router-dom` package can be used to access a URL parameter value from within a component rendered by a `<Route>` with a dynamic URL. 

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used

In this example, the `<Page>` component accesses the `id` URL parameter via the object returned by `useParams()`. If the user were to navigate to `/page1`, the component will render `<h3> ID: page1 </h3>`.

```js
import React from "react";
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link,
  useParams
} from "react-router-dom";

export default function App () {
  return (
    <Router>
      <div>
        <Link to="/page1">Page 1</Link>
        <Link to="/page2">Page 2</Link>
        <Link to="/page3">Page 3</Link>

        <Switch>
          <Route path="/:id">
            <Page />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Page () {
  // We can use the `useParams` hook here to access
  // the dynamic pieces of the URL.
  let { id } = useParams();

  return (
    <div>
      <h3>ID: {id}</h3>
    </div>
  );
}
```

<hr>

## Controlling Routes with `<Switch>`

### Learning Standard Text

The `<Switch>` component from the `react-router-dom` library looks through its children `<Route>` components and renders the first one that matches the current URL. 

### Tags

JavaScript, React, React Router

### Additional Notes / Resources Used

In this example, if the user navigates to `/users/123`, then only the `<SingleUser>` component will render. If the `<Switch>` were removed, then both `<SingleUsers>` and `<UsersList>` would render as their `<Route>`s both match the URL.

```js
// App.js
import React from "react";
import { 
  BrowserRouter as Router, 
  Route,
  Switch 
} from "react-router-dom";

export default function App() {
  return (
    <Router>
      <Switch>
        <Route path={'/users/:userID'}>
          <SingleUser />
        </Route>
        <Route path={'/users'}>
          <UsersList />
        </Route>
      </Switch>
    </Router>
  );
}
```

- https://reactrouter.com/native/api/Switch
<hr>

## Route Nesting and the `useRouteMatch()` hook

### Learning Standard Text

Since routes are regular React components, they may be rendered anywhere in the app, including in child elements. 

The `useRouteMatch()` hook from the `react-router-dom` package may be used access the `match` object which contains `url` and `path` values. The `path` is used to build `<Route>` paths that are relative to the parent route, while the `url` is used to build relative `Link` paths.

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used

Example:

This helps when it's time to code-split your app into multiple bundles because code-splitting a React Router app is the same as code-splitting any other React app.

```js
import React from "react";
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link,
  useParams,
  useRouteMatch
} from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/topics">Topics</Link>
          </li>
        </ul>

        <Switch>
          <Route exact path="/">
            <Home />
          </Route>
          <Route path="/topics">
            <Topics />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Home() {
  return (
    <div>
      <h2>Home</h2>
    </div>
  );
}

function Topics() {
  // The `path` lets us build <Route> paths that are
  // relative to the parent route, while the `url` lets
  // us build relative links.
  let { path, url } = useRouteMatch();

  return (
    <div>
      <h2>Topics</h2>
      <ul>
        <li>
          <Link to={`${url}/rendering`}>Rendering with React</Link>
        </li>
        <li>
          <Link to={`${url}/components`}>Components</Link>
        </li>
        <li>
          <Link to={`${url}/props-v-state`}>Props v. State</Link>
        </li>
      </ul>

      <Switch>
        <Route exact path={path}>
          <h3>Please select a topic.</h3>
        </Route>
        <Route path={`${path}/:topicId`}>
          <Topic />
        </Route>
      </Switch>
    </div>
  );
}

function Topic() {
  // The <Route> that rendered this component has a
  // path of `/topics/:topicId`. The `:topicId` portion
  // of the URL indicates a placeholder that we can
  // get from `useParams()`.
  let { topicId } = useParams();

  return (
    <div>
      <h3>{topicId}</h3>
    </div>
  );
}
```

- This example code was taken from https://reactrouter.com/web/example/nesting

<hr>

## Redirecting Declaratively with `<Redirect>

### Learning Standard Text

The `<Redirect>` tag is used to force a redirect to the given route using its `to` prop.

### Tags

JavaScript, React, React Router


### Additional Notes / Resources Used

Example:

```js
import { Redirect } from 'react-router-dom'
 
const UserProfile = ({ loggedIn }) => {
  if (loggedIn) {
    return (
      // ... user profile contents here
    )
  }
 
  // redirect to the sign-up page.
  <Redirect to='/sign-up' />
}
```

Sources:
- https://reactrouter.com/web/guides/primary-components/navigation-or-route-changers
- https://reactrouter.com/web/api/Redirect

<hr>

## The history object and the `useHistory()` hook

### Learning Standard Text

The `useHistory()` hook from by the `react-router-dom` package returns an instance of the `history` object. 

The `history` object has a mutable stack-like structure that keeps track of the user's session history. Notably, it contains the following useful methods 
* `history.push(location)` - imperatively redirects the user to the specified `location`
* `go(n)` - Moves the pointer in the history stack by n entries
* `goBack()` - Equivalent to `go(-1)`
* `goForward()` - Equivalent to `go(1)`

### Tags

JavaScript, React, React Router

### Additional Notes / Resources Used

Examples:

1. Imperative Redirects:
```js
import { useHistory } from `react-router-dom`
 
export const exampleForm = () => {
 
  const history = useHistory()
 
  const handleSubmit = e => {
    // Submit the form data
    // Then imperatively redirect
    history.push('/')
  }
 
  //...
 
  return (
    <form onSubmit={handleSubmit}>
      // form elements
    </form>
  )
}
```

2. Forward/Back navigation

```js
import { useHistory } from `react-router-dom`
 
export const ForwardBackNav = () => {
  const history = useHistory()
 
  return (
    <nav>
      <button onClick={() => history.goBack()}>
        <-
      </button>
      <button onClick={() => history.goForward()}>
        ->
      </button>
    </nav>
  )
}
```

Sources
* https://reactrouter.com/web/api/history

<hr>