# Quiz

## Assessment 1

What is React Router?

Response: A library that provides navigational components for React Developers to create single-page applications (SPAs) with dynamic, client-side routing.
* That's right!

Response: A library that provides navigational components for React Developers to create multi-page applications (MPAs) with server-side routing.
* Not quite. React Router is specifically designed to provide client-side routing for Single Page Applications, not MPAs.

Response: A framework for organizing a single page application's code by separating data models from views.
* Not quite. React Router does not impose any structure on an application's code, it just provides components you can use to add client-side routing to that application.

Response: A tool for storing and managing application state in single-page applications.
* Not quite. While React Router is technically capable of storing state, its primary purpose it to provides components you can use to add client-side routing to applications which can use any state management tool you like.

<hr>

## Assessment 2

The example below shows a nested `Link` and `Route` within the `User` component. Fill in the code so that the `Link` and `Route` components render with the correct `to` and `path` props relative to the location of the `User` component.

```js
import { Link, Route, Switch, useRouteMatch } from __~'react-router-dom'~__;
import UserProfile from './UserProfile'

function User() {
  let { path, url } = __~useRouteMatch()~__;

  return (
    <div>
      <h2>Current User</h2>
      <UserProfile />  
      <ul>
        <li>
          <Link to={`${__~url~__}/edit`}>Edit</Link>
        </li>
      </ul>

      <Switch>
        <Route path={`${__~path~__}/edit`}>
          <EditProfile />
        </Route>
      </Switch>
    </div>
  );
}
```

Response: `react-router-dom`
* Hint: To use React Router's components, you need to import them from the `react-router-dom` package.

Response: `useRouteMatch`
* Hint: `path` and `url` are properties on the `match` object returned by the `useRouteMatch` hook.

Response: `url`
* Hint: When building relative links, you should use the `match` object's `url` property, which replaces the names of URL parameters with their actual values.

Response: `path`
* Hint: When building relative links, you should use the `match` object's `path` property, which preserves the names of URL parameters rather than replacing them with their actual values.

## Assessment 3
Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/multiple-choice/) for guidance on multiple choice assessments.

Consider the following component, which renders when the browser's location matches `/users/:userId`.

```js
function Users () {
  let { path, url } = __~useRouteMatch()~__;

  return (
    <div>
      <h2>User</h2>
      <ul>
        <li>
          <Link to={`${__~url~__}/followers`}>Followers</Link>
        </li>
        <li>
          <Link to={`${__~url~__}/following`}>Following</Link>
        </li>
      </ul>

      <Switch>
        <Route path={`${__~path~__}/followers`}>
          <Followers />
        </Route>
        <Route path={`${__~path~__}/following`}>
          <Following />
        </Route>
      </Switch>
    </div>
  );
}
}
```

When the browser's location is `/users/5`, what are the values of `url` and `path` respectively?

Response: `/users/5`, `/users/:userId`
Reason: Correct! The `url` property from the object returned by `useRouteMatch()` has the actual value of route parameters filled in (`5` for the `userId`), whereas the `path` property leaves the names of the current URL's URL parameters as-is.

Response: `/users/:userId`, `/users/5`,
Reason: Not quite. The `url` property of the match object returned by `useRouteMatch()` has the values of URL parameters filled in, whereas the `path` property leaves their names as-is.


Response: `/5`, `/:userId`
Reason: Not quite. The `url` and `path` properties from the object returned by `useRouteMatch()`  have the values for the full URL/path respectively, not just the last segment.

Response: `/users`, `/:userId`
Reason: The `url` and `path` properties from the object returned by `useRouteMatch()`  have the values for the full URL/path respectively, not just individual URL segments.

<hr>

## Assessment 4

When building adding in-app navigation to a single-page application (SPA) built with React Router, you should use React Router's `Link` and `NavLink` components instead of a native `a` tag because:

Response: Clicking an `a` tag causes the page to reload but clicking a `Link` or `NavLink` does not.
Reason: Correct! React Router's `Link` and `NavLink` components disable the anchor tag's default behavior of triggering a page reload.

Response: You should never use HTML tags in React Router code.
Reason: Not quite. It's okay to use semantic HTML tags alongside React Router components when the situation calls for you to do so. Clicking an `a` tag will cause the page to reload, which we want to avoid in SPAs.

Response: `Link` and `NavLink` are more efficient than the `a` tag, and using them is a way to optimize your application's performance.
Reason: Not quite. `a` tags are not less efficient than React Router's `Link` and `NavLink`, but clicking an `a` tag will cause the page to reload, which we want to avoid in SPAs.

Response: You will get a syntax error if you use an `a` tag instead of a `Link` inside of a `Router` component.
Reason: Not quite. React Router doesn't prohibit you from using native `a` tags – they just won't behave the way you want them to since they will cause a page reload.

<hr>

## Assessment 5

What does the `<Switch>` component do?

Response: Renders the first (and only the first) of its children `Route` components whose `path` matches the current URL.
* Reason: Correct! The `Switch` component renders the _first_ child `Route` whose `path` matches the current URL.

Response: Renders every one of its children `Route` components whose path matches the current URL.
* Reason: Not quite! The `Switch` component renders a single child `Route` – specifically the _first_ one whose `path` matches the current URL.

Response: Renders the last of its children `Route` components whose `path` matches the current URL.
* Reason: Not quite. The `Switch` component renders the _first_ child `Route` whose `path` matches the current URL.

Response: Renders all of its children `Route` components except those whose `path` matches the current URL.
Reason: Not quite! The `Switch` component renders a single child `Route` – specifically the _first_ one whose `path` matches the current URL.

<hr>

## Assessment 6

React Router allows you to render `Route` components in which of the following places:

Response: Anywhere that renders inside a `Router` component.
* Reason: Correct! React Router allows you to render `Route` components in any component that renders inside a `Router` – either as direct descendents of a `Router` or from within other components rendered by a `Router`. This is what allows you to nest `Route` components throughout your application.

Response: Directly inside a `Router` component.
* Reason: Not quite! While you can render `Route` components as direct descendents of a `Router`, React Router also allows you to render `Route` components in any component that renders as a child of a `Router`. This is what allows you to nest `Route` components throughout your application.

Response: Only inside `Switch` components.
* Reason: Not quite. Not all applications use the `Switch` component, and there's no requirement that `Route`s be rendered from within switches. You can include a `Route` component anywhere that renders inside a `Router`.

Response: Only inside other `Route` components.
Reason: Not quite. While you can nest `Route` components inside each other, that isn't the only place you can render them. React Router allows you to render `Route` components in any component that renders inside a `Router`.

<hr>

## Assessment 7

Rendering a `Redirect` component allows you to change the current URL:

Response: Declaratively
* Reason: Correct! Rendering a `Redirect` will navigate to a new location declaratively – that is, you specify _what_ you want to have happen without specifying _how_ you want it to happen.

Response: Imperatively
* Reason: Not quite! To update the URL imperatively you should use one of the methods on the `history` object (eg. `push`, `goForward`, `goBack`).

<hr>

## Assessment 8

All of the following are properties on the `history` object EXCEPT:

Response: `to`
* Reason: Correct! The `history` object does not have a `to` property.

Response: `push`
* Reason: Not quite! The `history` object has a `push` method that updates the current URL.

Response: `goForward`
* Reason: Not quite! The `history` object has a `goForward` method that moves the history stack's pointer forward by 1.

Response: `goBack`
Reason: Not quite! The `history` object has a `goBack` method that moves the history stack's pointer backward by 1.

<hr>

## Assessment 9

Do you think this is possible to pull off using FITC, or will it be too confusing?

Fill in the code so that:
* Navigating to `/users/5` causes the `UserProfile` component to render
* Navigating to `/users/5/edit` causes the `EditUser` component to render
* Navigating to `/` causes the `Home` component to render
* Navigating to `/users` causes the `Users` component to render

```js
import { BrowserRouter as Router, Switch, Route } from __~'react-router-dom'~__;

function App() {
  return (
    <Router>
      <Switch>
        __~ ~__
        __~ ~__
        __~ ~__
        __~ ~__
      </Switch>
    </Router>
  );
}
```

* Hint: Remember, a `Switch` renders the first (and only the first) `Route` whose `path` matches the current location. Consider the fact that `/users/5/edit`, `/users/5`, `/users`, and `/` will all match `/users/5` – which `Route` should come first in order to produce the desired behavior?
* Hint: Remember, a `Switch` renders the first (and only the first) `Route` whose `path` matches the current location. Consider the fact that `/users/5`, `/users`, and `/` will all match `/users` – which `Route` should come first in order to produce the desired behavior?
* Hint: Remember, a `Switch` renders the first (and only the first) `Route` whose `path` matches the current location. Consider the fact that `/users`, and `/` will all both match `/users` – which `Route` should come first in order to produce the desired behavior?
* Hint: Since `/` will match any path, it should come last in the ordered list or it will prevent the rendering of any other `Route`.

Response:           
```js
<Route path='/'>
  <Home/>
</Route>
```


Response:
```js
<Route exact path='/users/:userId/edit'>
  <EditUser/>
</Route>
```

Response:
```js
<Route exact path='/users/:userId'>
  <UserProfile/>
</Route>
```

Response:
```js
<Route exact path='/users'>
  <Users/>
</Route>
```

## Assessment 10

Which of the following demonstrates the proper syntax for rendering a `<Route>` and `<Link>` component:

Response:
```js
<Route path='/'>
<Link to='/'>
```
* Correct! The `<Route>` component uses the `path` prop to define the location for which it should render. The `<Link>` component uses the `to` prop to define the location to navigate to when it is clicked.

Response:
```js
<Route to='/'>
<Link path='/'>
```
* Not quite. The `<Route>` component uses the `path` prop to define the location for which it should render. The `<Link>` component uses the `to` prop to define the location to navigate to when it is clicked.

Response:
```js
<Route url='/'>
<Link destination='/'>
```
* Not quite. The `<Route>` component uses the `path` prop to define the location for which it should render. The `<Link>` component uses the `to` prop to define the location to navigate to when it is clicked.

Response:
```js
<Route location='/'>
<Link url='/'>
```
* Not quite. The `<Route>` component uses the `path` prop to define the location for which it should render. The `<Link>` component uses the `to` prop to define the location to navigate to when it is clicked.

<hr>

## Assessment 11

Fill in the code below to properly import and render the `BrowserRouter` component.

```js
// App.js
import { __~BrowserRouter as Router~__ } from __~'react-router-dom'~__;

export default function App() {
  return (
    __~<Router>~__
      __~<div> Application contents...</div>~__
    __~</Router>~__
  );
}

Hints (top to bottom, left to right)
* The `BrowserRouter` component is often aliased to `Router`.
* The `BrowserRouter` component can be imported from the `'react-router-dom'` package.
* The `<Router>` component should wrap around the contents of the application.
* The contents of the application should be nested inside the `<Router>` component.
* The `<Router>` component should wrap around the contents of the application.

<hr>

## Assessment

Consider a music application that renders a `Song` component for URLs that match the location `/favoriteSongs/:songId`. Which method from `'react-router-dom'` can be imported and used within the `Song` component to access the value of the URL parameter `songId`?

Response: The `useParams()` method.
* Correct! The `useParams()`  method returns the URL parameters as key/value pairs in an object. In this case, you could access the `songId` by writing `const { songId } = useParams()`.

Response: The `useLocation()` method.
* Not quite. The `useLocation()` method returns the location object that represents the current URL.

Response: The `useHistory()` method.
* Not quite. The `useHistory()` method returns an object which represents the full URL location.

Response: The `useRouteMatch()` method.
* Not quite. The `useRouteMatch()` method returns an object with the `url` and `path` properties which are useful for creating relative links and routes.
