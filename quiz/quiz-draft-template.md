# Quiz

## Assessment 1

What is React Router?

Response: A library that provides navigational components for React Developers to create Single-Page Applications (SPAs) with dynamic, client-side routing.
* That's right!

Response: A library that provides navigational components for React Developers to create Multi-Page Applications (MPAs) with server-side routing.
* Not quite. React Router is specifically designed to provide client-side routing for Single Page Applications, not MPAs.

Response: A framework for organizing a Single Page Application's code by separating models from views.
* Not quite. React Router does not impose any structure on an application's code, it just provides components you can use to add client-side routing to that application.

Response: A tool for storing and managing application state in Single-Page Applications.
* Not quite. React Router does offer state management – other tools do that. React Router provides components you can use to add client-side routing to applications using whatever state management tool you like.

<hr>

## Assessment 2

Fill in the code so that the nested `Link` and `Route` components render with the correct `to` and `path` props.

```js
import { Link, Route, Switch, useRouteMatch } from __~'react-router-dom'~__;

function User() {
  let { path, url } = __~useRouteMatch()~__;

  return (
    <div>
      <h2>Current User</h2>
      {
        // ... user profile here
      }
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
Reason: Correct! The `match` object's `url` property has the value of route parameters filled in, whereas the `path` property leaves the names of the current URL's URL parameters as-is.

Response: `/users/:userId`, `/users/5`,
Reason: Not quite. The `url` property of the match object has the values of URL parameters filled in, whereas the `path` property leaves their names as-is.

Response: `/5`, `/:userId`
Reason: Not quite. The `url` and `path` objects have the values for the full URL/path respectively, not just the last segment.

Response: `/users`, `/:userId`
Reason: The `url` and `path` objects have the values for the full URL/path respectively, not just individual URL segments.

<hr>

## Assessment 4

What is the difference between Multi- Single-Page Applications?

Response: Multi-Page Applications request distinct HTML files from the server each time the user requests a new page. Single-Page Applications request a single HTML file when the user first visits the application and update the page's contents using Javascript each time the user user requests a new page.

Reason: Correct!

Response: Multi-Page Applications have lots of features and Single-Page Applications have only one feature.
Reason: Not quite. It is possible to build a Single-Page Application with lots of features or a Multi-Page Application that has only one feature. What distinguishes SPAs from MPAs is how the application handles requests to new pages.

Response: Multi-Page Applications make many requests to the server for new HTML each time the user requests a new page, and Single-Page applications make a single request to the server for new HTML each time the user requests a new page.
Reason: Not quite. SPAs request a single HTML file when the user first visits the application and update the page's contents using Javascript from there on out.

Response: Multi-Page Applications use only HTML, whereas SPAs use HTML and Javascript.
Reason: Not quite. It is possible to use Javascript in Multi-Page Applications as well as Single-Page Applications.

<hr>

## Assessment 5

When building a SPA with React Router, you should use React Router's `Link` and `NavLink` components instead of a native `a` tag because:

Response: Clicking an `a` tag causes the page to reload but clicking a `Link` or `NavLink` does not.
Reason: Correct! React Router's `Link` and `NavLink` components disable the anchor tag's default behavior of triggering a page reload.

Response: You should never use HTML tags in React Router code.
Reason: Not quite. It's okay to use semantic HTML tags alongside React Router components when the situation calls for you to do so. Clicking an `a` tag will cause the page to reload, which we want to avoid in SPAs.

Response: `Link` and `NavLink` are more efficient than the `a` tag, and using them is a way to optimize your application's performance.
Reason: Not quite. `a` tags are not less efficient than React Router's `Link` and `NavLink`, but clicking an `a` tag will cause the page to reload, which we want to avoid in SPAs.

Response: You will get a syntax error if you use an `a` tag instead of a `Link` inside of a `Router` component.
Reason: Not quite. React Router doesn't prohibit you from using native `a` tags – they just won't behave the way you want them to since they will cause a page reload.

<hr>

## Assessment 6

What does the `<Switch>` component do?

Response: Renders the first of its children `Route` components whose `path` matches the current URL.
* Reason: Correct! The `Switch` component renders the _first_ child `Route` whose `path` matches the current URL.

Response: Renders every one of its children `Route` components whose path matches the current URL.
* Reason: Not quite! The `Switch` component renders a single child `Route` – specifically the _first_ one whose `path` matches the current URL.

Response: Renders the last of its children `Route` components whose `path` matches the current URL.
* Reason: Not quite. The `Switch` component renders the _first_ child `Route` whose `path` matches the current URL.

Response: Renders all of its children `Route` components except those whose `path` matches the current URL.
Reason: Not quite! The `Switch` component renders a single child `Route` – specifically the _first_ one whose `path` matches the current URL.

<hr>

## Assessment 7

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

## Assessment 8

Rendering a `Redirect` component allows you to change the current URL:

Response: Declaratively
* Reason: Correct! Rendering a `Redirect` will navigate to a new location declaratively – that is, you specify _what_ you want to have happen without specifying _how_ you want it to happen.

Response: Imperatively
* Reason: Not quite! To update the URL imperatively you should use one of the methods on the `history` object (eg. `push`, `goForward`, `goBack`).

<hr>

## Assessment 9

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

## Assessment ???

Do you think this is possible to pull off using FITC, or will it be too confusing?

Fill in the code so that:
* Navigating to `/users/5` causes the `UserProfile` component to render
* Navigating to `/users/5/edit` causes the `EditUser` component to render
* Navigating to `/users` causes the `Users` component to render
* Navigating to `/` causes the `Home` component to render

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

Response:           
```js
<Route exact path='/'>
  <Home/>
</Route>
```
* Hint:

Response:
```js
<Route exact path='/users/:userId/edit'>
  <EditUser/>
</Route>
```
* Hint:

Response:
```js
<Route exact path='/users/:userId'>
  <UserProfile/>
</Route>
```
* Hint:

Response:
```js
<Route exact path='/users'>
  <Users/>
</Route>
```
* Hint:
