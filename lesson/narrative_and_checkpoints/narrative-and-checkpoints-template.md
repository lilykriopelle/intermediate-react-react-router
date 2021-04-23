# _Front End Routing With React Router_

_Read the content standards for expectations for [narratives](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/), [checkpoints](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/), and [hints](http://curriculum-documentation.codecademy.com/Content-Standards/hint/)._

<hr>

## Exercise 1: _What is routing?_

### Narrative:

In this lesson, you will learn what routing is as well as how to add routing to your React applications with React Router. To reinforce your learning, you will add routing to the codebase for a tech news application built with [Create React App](https://reactjs.org/docs/create-a-new-react-app.html#create-react-app). Before we learn about routing in the specific context of React applications, it's important to understand how routing works in general.

Routing is the process by which a web application determines what content to show a user based on the current **U**niform **R**esource **L**oader (URL). By organizing an application's content and displaying only what the user has requested to see, routing allows for rich, engaging, and clear user experiences

To understand how routing works, it is helpful to review the basic structure of URLs. URLs consist of several components, some of which are mandatory and some of which are optional. The  basic components that make up a URL are:
  1. The scheme (eg. `HTTP`, `HTTPS`, `mailto`, etc), which specifies what [protocol](https://www.codecademy.com/articles/http-requests) should be used to access the resource
  2. The domain (eg. `codecademy.com`), which specifies what website hosts the resource  
  3. The path (eg. `/search`), which identifies the specific resource to which the URL corresponds.
  4. The query string (eg. `?query=react`), which appears after a '?' and assigns values to parameters. Common uses of query strings include search parameters and filters.

When a user enters a URL in the browser, the browser matches the URL's domain name to an IP address and sends a request to that IP address using the specified protocol.

### Instructions:

1. Checkpoint: Take a moment to examine the URL in your browser's address bar. What is the scheme? The domain? The path? Is there a query string?

Hint: 
* The scheme is `https`
* The domain is `www.codecademy.com`
* The path is `/courses/learn-redux/lessons/core-concepts-in-redux/exercises/review
* There are no query parameters

<hr>

## Exercise 2: _Single vs. Multi-Page Architecture_

### Narrative:
React Router emerged as a tool for adding routing to **S**ingle **P**age **A**pplications (SPAs). But what exactly is a SPA and why would you want to create one? To answer that question, it's helpful to understand the predecessors to SPAs: multi-page applications.

In a multi-page application, different pages correspond to different HTML files. When the browser requests a new page, the server responds with new HTML. To load the new page, the browser wipes out the existing HTML and replaces it, causing a distracting flash of the screen and a clunky experience.

Single-page architecture, on the other hand, leverages the power of Javascript to dynamically manipulate the DOM. In a SPA, when the user navigates to a new page, Javascript produces new markup and renders it in the browser. If necessary, the application asynchronously fetches data in the background and inserts into the markup on the page. These partial changes do not require a full page load.

Client-side routing and server-side routing generally coexist: client-side routing determines what view to display in the browser, while server-side routing determines what information to send from the server to the client in response to a particular request. Adding client-side routing to an application does not eliminate the need for server-side routing, but it does allow the client to display different HTML for different routes without having to fetch that HTML from the server.

React Router is the most popular solution for implementing routing in single page React applications. The library provides a few simple tools for displaying different components to the user based on the URLs they visit. In the rest of this lesson, you will learn how to use React Router to add client-side routing to your applications.

### Instructions:

1. Checkpoint: We've provided a diagram that compares and contrasts multi-page and single page architecture. The rest of this lesson will focus on single page architecture, but before moving on, take a moment to review the diagram and make sure you are familiar with how each architecture works.

<hr>

## Exercise 3: Installing React Router

### Narrative:
In order to use React Router, you will need to include the [`react-router-dom` package](https://www.npmjs.com/package/react-router-dom) (the version of React Router built specifically for web browsers) in your project by using `npm` like so:

```
npm install --save react-router-dom
```

Once you have added `react-router-dom` to your project, you can import one of its router components to add routing to your project. React Router provides several router components however the most common one is the `BrowserRouter`. The other option and the reasons you might choose one over the other are outside the scope of this lesson, but you can read more about that [here](https://reactrouter.com/web/api/BrowserRouter).

For the sake of simplicity and readability, it is common to alias `BrowserRouter` as `Router` when importing, like so:

```js
import { BrowserRouter as Router} from ‘react-router-dom’
```

### Instructions:

1. Checkpoint: _Install `react-router-dom`_. To verify that you have successfully added the package to your project, navigate to `package.json` and check that `react-router-dom` appears in the `dependencies` array.

Hint: Use `npm install --save` to add the package to your project.

2. Checkpoint: In **App.js** import `BrowserRouter` from `react-router-dom` and alias it to `Router`.

Hint: Your syntax should look something like this:

```js
import { ComponentName as AliasName } from `name-of-package`
```

## Exercise 4: _Rendering Your `Router`_

### Narrative:
Now that you've imported a `Router`, what do you do with it? In the React Router paradigm, the different views of your application, also called _routes_, along with the `Router` itself, are just React components. To include them in your application, you will need to render them.

Whereas other routing paradigms are static (eg. routes are predefined prior to and separate from the process of rendering), [React Router's philosophy](https://reactrouter.com/web/guides/philosophy) is declarative and dynamic. This means that routes come into being when they are rendered. While this might seem more complicated than configuring your routes statically, it's also more flexible, because your application's route structure can evolve based on user interactions and changing state.

To add routing to your app, simply render a `Router` component as the top level component. In the `render` of your App component in **App.js**, wrap your applications's contents in a `Router` component:

```js
import { BrowserRouter as Router} from ‘react-router-dom’
export default function App () {
  return (
    <Router>
      // render application contents here
    </Router>
  )
}

```
Making `Router` the top-level component prevents URL changes from causing page reloads. When you render a `Router` as your top-level component, URL changes cause the `Router` component to respond by passing information about the current URL's path to its child components as props.

### Instructions:

1. Checkpoint: In **App.js**, wrap your application's content in a `Router`.

Hint: _Insert optional but recommended hint text here._

## Exercise 5: _Basic routing with `<Route>`_

### Narrative:
Once you've created a `Router`, you can start creating different views, or _routes_, for the various URL paths of your application. Remember, everything in React Router is a component. To add a route to an app, you need to render a `Route` component by nesting it inside a `Router`.

First, alongside the `BrowserRouter`, import the `Route` component from the `react-router-dom` package like so:
```js
import { BrowserRouter as Router, Route } from `react-router-dom`
```
Next, render a `Route` inside your `Router`. The `Route` component's function is simple: to render its children when the current URL path matches the value of its `path` prop. For example, the following route renders the `About` component when the URL path matches `'/about'`.

```js
<Route path='/about'>
  <About />
</Route>
```

If you navigate to `'/about'`, your URL path will match the route's `path` prop, and the `About` component will render.

If your router includes a `Route` with no `path` prop, then that route will always match. You can leverage this fact to make your applications render components that you want your user to see regardless of the current route (these are often but not always layout components, such as sidebars and navigation bars) by including those components as children of a route with no `path` prop.

### Instructions:

1. Navigate to **App.js**, which currently renders an empty `Router` and imports an `Articles` component. Inside the `Router` component, add a route that matches the path `'/articles'` and renders the `Articles` component.

Hint: Your syntax for adding a route should look something like this:

```js
<Route path='/your-path-here'>
  <ChildComponent />
</Route>
```

2. In the URL bar, navigate to `'/articles'` to confirm that your code is working. You should see

## Exercise 6: _Linking to routes_

### Narrative:

In the last exercise, you used the URL bar to navigate to a path that matched one of your application's routes. But how do you navigate from within the app itself? React Router provides a `Link` component for doing just that.

To create a link to a particular route, render a `Link` component and set its `to` prop equal to the location to which the link should navigate. The simplest way to specify this location is as a string:

```js
 <Link to='/about' />
```

However, React Router also allows you to provide this location as a [function](https://reactrouter.com/web/api/Link/to-function) or [object](https://reactrouter.com/web/api/Link/to-object), which can be useful if you need to programatically generate the location.

Why should use `Link` instead of the native `a` tag? React Router's `Link` component wraps the native `a` tag you are familiar with, but prevents its default behavior (navigating to the specified path and causing a page reload – the very thing we are trying to avoid with front-end routing).

In addition to providing the `Link` component, React Router provides [`NavLink`](https://reactrouter.com/web/api/NavLink) – a special type of link that displays differently depending on whether or not the current URL path matches the `NavLink`'s `to` prop. These can be quite useful for building navigation menus, as they differentiate between active and inactive content, enabling a user to quickly see which content they are viewing.  

### Instructions:

1. We've expanded the tech news application to include several additional routes and components. First, navigate to **Article.js** and wrap the author's name with a `Link` component with the path `'authors/' + authorName`.

Hint: You will have to import the `Link` component from `react-router-dom`.

## Exercise 7: _Dynamic routes_

### Narrative:
So far, all the routes we've covered have been static, which means they match a single path. This works for certain types of routes, but not all. For example, imagine a tech news site in which every article has is accessible at the path (`'/articles/'` + title). There is no way for us to specify a route for each unique article without knowing every single title, nor should we specify a unique route for every article because such an approach would be brittle and verbose. What we would rather do is express the pattern at a high level with a route will match any path of the form `'/articles/'` + title.

React Router allows us to do that by using URL parameters. URL parameters—placeholders beginning with a semicolon (:)—are dynamic segments of a URL that change based on the specific resource the URL is meant to display. For example, in the URL `'/articles/:title'`, `:title` is dynamic: `'/articles/article-one'` should display the article with title `'article-one'` and `'/articles/article-two'` should display the article with title `'article-two`. A URL can have multiple dynamic segments (eg. `'/articles/:title/comments/:commentId'`) or none (eg. `'articles'`).

To create a dynamic route, provide the `Route` component with a `path` prop that includes a dynamic segment. For example, a `Route` whose path has a dynamic title segment and that renders an `Article` component would look like this:

```js
<Route path='/articles/:title'>
  <Article />
</Route>
```

Now, when we navigate to `'/articles/:title`, an `Article` component render.  

It is common to use URL parameters to retrieve and/or display data in the component that a dynamic route renders. For example, the `Article` component might need to display the title of the current article.

React Router provides a hook, `useParams()` (which you'll need to import from `'react-router-dom'`), for accessing the value of URL parameters. When called, `useParams()` returns an object that maps the names of dynamic segments to their values. To grab a particular value, use destructing assignment like so:


```js
import { Link, useParams } from 'react-router-dom';

export default function Article() {
  let { title } = useParams();

  return (
    <article>
      <h1>{title}</h1>
      // ...
    </article>
  );
}
```

### Instructions:

1. Navigate to **App.js** and add a dynamic route that renders the `Author` component whenever the URL path matches `'/authors/' + AUTHOR_NAME`.

Hint: To add a dynamic route, render the `Route` component and make sure that its `path` prop includes a dynamic segment (a segment beginning with a colon).

2. In **Author.js**, import `useParams` from `'react-router-dom'` and use it to get the value of the route param you defined in the previous step. Display this value in between the `h1` tags we've provided. To test that your code works, navigate to `/authors/ + YOUR_NAME` in the URL bar. You should see your name displayed on the page.

Hint: To get the value of a particular dynamic segment, use destructing assignment like so:

```js
const { nameOfDynamicSegment } = useParams()
```

## Exercise 8: _Query Parameters_

### Narrative:
Path parameters (the values assigned to dynamic segments) are used specify resources; they are non-optional parts of the URLs in which they appear. Query parameters, on the other hand, are optional parameters that are most often used to search, sort and/or filter resources.

React Router provides a mechanism for grabbing query parameters' values: the `useLocation` hook, which returns a [`location`](https://reactrouter.com/web/api/location) object whose `search` property corresponds to the current URL's query string.

Passing this string to the native `URLSearchParameters` constructor will yield an object that maps the names of query parameters to their values. Use `useLocation` and `URLSearchParameters` together like so:

```js
import { useLocation } from 'react-router-dom'
import { sortAscending, sortDescending } from '../utils'

export const SortedList = (numberList) => {
  const { search } = useLocation()
  const queryParams = new URLSearchParams(search)
  const sortOrder = queryParams.get('order')

  if (sortOrder === 'ASC') {
    return sortAscending(numberList)
  } else if (sortOrder === 'DESC') {
    return sortDescending(numberList)
  } else {
    return numberList
  }
}

```

### Instructions:

1. You're going to add a search feature to the `Articles` page that filters the listed articles by whether or not their titles match the search string. Navigate to **Articles.js**, and use `useLocation` along with `URLSearchParams` to grab the value of the `search` parameter from the query string.  

Hint: Import `useLocation` from `react-router-dom`. Remember, the `useLocation` hook returns an object whose `search` property corresponds to the current URL's query string.

2. Pass that value into the `filterArticles` function we've provided.

Hint: _TO DO_

## Exercise 9: _`Switch` and `exact`_

### Narrative:
By design, a `Router` will render _all_ the `Routes` whose paths match the current URL. This allows us to compose layouts in which multiple components should appear or disappear based on the current URL (for example, an application in which the sidebar and main display respond to changes in the current URL). But sometimes, this design choice can produce unintended results. Consider the following (relatively common) setup:

```js
<Router>
  <div>
    <Route path='/articles/new'>
      <NewArticle />
    </Route>
    <Route path='/articles/:title'>
      <Article />
    </Route>
    <Route path='/articles'>
      <Articles />
    </Route>
  </div>
</Router>
```

What should happen when the user navigates to `'articles/new'`? The `NewArticle` component should appear. But what actually happens when the user navigates to that URL is that _all_ routes match – the first route's `path` prop matches exactly, the second route will match `new` to the URL parameter `:title`, and the last route will match because both begin with `/articles`. Because all routes match, the application will render the `NewArticle`, `Article`, and `Articles` components simultaneously.  

React Router provides several mechanisms for preventing this sort of unintended rendering. The first is the `Switch` component. When wrapped around a collection of routes, `Switch` will render the first of its child routes whose `path` prop matches the current URL.

```js
<Switch>
  <div>
    <Route path='/articles/new'>
      <NewArticle />
    </Route>
    <Route path='/articles/:title'>
      <Article />
    </Route>
    <Route path='/articles'>
      <Articles />
    </Route>
  </div>
</Switch>
```

Because the `Switch` checks routes sequentially, the order in which Routes are rendered matters. Consider a similar example but with the order of the routes reversed:

```js
<Switch>
  <div>
    <Route path='/articles/:title'>
      <Article />
    </Route>
    <Route path='/articles/new'>
      <NewArticle />
    </Route>
    <Route path='/articles'>
      <Articles />
    </Route>
  </div>
</Switch>
```

Now imagine that a user navigates to `'/articles/new'`. The `Switch` renders the first route with a matching path, `'/articles/new'` matches `'/articles/:title'`, since `:title` is a dynamic segment. With the routes listed in this order, the `NewArticle` component will never render. In general, you can avoid this problem by listing routes from most- to least-specific.

Sometimes you may want to leverage React Router's composability and render multiple routes simultaneously (this would prevent you from using a `Switch` component) while also ensuring your router distinguishes between static paths and paths including URL parameters. Consider the following example:

```js
<Router>
  <div>
    <Route path='/'>
      <Home />
    </Route>
    <Route path='/sign-up'>
      <SignUp />
    </Route>
  </div>
</Router>
```

Any path will match first route, so the the `Home` component will be rendered whether the user is at `'/'` or `'/sign-up'`. This might be ideal behavior if the component rendered by the `'/'` route should display regardless of the current route.

But what if you only want the `Home` component to be visible to users on the home page and not to those who have navigated to `/sign-up`? By using React Router's `exact` prop on the first route, you can ensure that the route will match _only if the current URL is an exact match_.

```js
 <Route exact path='/'>
   <Home />
 </Route>
```

Now, when a user visits '/', the `Home` component will render. But when a user visits '/sign-up', only the second route will match and only the `SignUp` component will render.  

React Router provides a couple of additional props—[`strict`](https://reactrouter.com/web/api/Route/strict-bool) and [`sensitive`](https://reactrouter.com/web/api/Route/sensitive-bool)—on the `Route` component for fine-tuning when a particular route should match.  

### Instructions:

1. Let's revisit the tech news application's router. If you navigate to `/articles/accessibility-and-html`, you will notice that the `Article` and `Articles` components both render. Use a `Switch` component to ensure that only the `Articles` component renders when you visit `'/articles'` and only the `Article` component renders when you visit `/articles/accessibility-and-html`.

Hint: Import the `Switch` component from `react-router-dom` and wrap the existing routes in a `Switch`.

2. You'll notice we've included a route with a `path` of `/`. Currently, this route will match any path. Use the `exact` prop on that route to ensure that the route only matches when the path is exactly equal to `/`.

Hint: _TO DO: come up with a hint for this that isn't totally obvious, suggestions welcome_

## Exercise 10: _Nested routes_

### Narrative:
Up to this point, we have been working with routers that are small enough to be rendered entirely in a single file. But as an application grows in scope, it can be useful to render routes from multiple components. This allows us to locate routing logic near the related UI logic – you can imagine that on large code bases, it can be advantageous to have code organized this way. Splitting routes up this way also makes an application more lightweight – if a user never navigates to a part of the application that necessitates a route to render, then it never will.

Let's return to our tech news website example, and imagine that the engineering team is building out a `Categories` feature that will organize tech news articles by their category – front end, back end, mobile development, etc. In addition to a `Categories` component (which will render links to each individual category), the team has created a `Category` view that will display all the articles for a given category. Previously, we might have written a router like this:

```js
<Switch>
  <Route path='/categories/:categoryName'>
    <Category />
  </Route>
  <Route path='/categories'>
    <Categories />
  </Route>
</Switch>
```

There's nothing wrong with this way of routing, but as soon as you start to introduce more features into your application, you may find that having all the routes contained in a single router becomes a bit unwieldly. The way around this is to get comfortable rendering routes from components elsewhere in your app.

For example, consider this `Categories` component, which iterates through a list of categories and links to each:

```js
function Categories ({ categories }) {
  return (
    <ul>
      {
        categories.map(c =>
          <li>
            <Link to={`categories/${c.name}`}>{c.name}</Link>
          </li>
        )
      }
    </ul>
  )
}
```

Clicking on a link rendered in this component will cause the URL to change; it will match the route from our previously defined router. But note that, from inside this `Categories` component, in order to know which component will be rendered when the URL updates, we have to navigate back to the component file where the routes were defined.

Because React Router handles routing dynamically (eg. routes exist when they are rendered), you can relocate the route to the components in which they are relevant.

```js
import { Link, Route } from 'react-router-dom'

function Categories ({ categories }) {
  return (
    <div>
      <ul>
        {
          categories.map(c =>
            <li>
              <Link to={`categories/${c.name}`}>{c.name}</Link>
            </li>
          )
        }
       </ul>
      <Route path='categories/:categoryName'>
        <Category />
      </Route>
    </div>
  )
}
```

Rewriting your routes this way makes it very obvious what will happen when the user clicks on a link. It also allows us to clean up our top-level router by removing the route for an individual category.

```js
<Switch>
   <Route path='/categories'>
    <Categories />
   </Route>
</Switch>
```

One potential downside of refactoring your applications this way is that changes to your route structure in one file might have ramifications for routes in other files. For example, suppose we wanted to change all instances of `'/categories'` in our routes to `'/topics'`. In our existing set up, we would have to remember to change not only the top-level `'/categories'` route, but also the `'/categories:categoryName'` sub-routes in the `Categories` component.

React Router provides a hook, `useRouteMatch()` that makes it easy to build relative route paths, creating more generalized and flexible code. Use the `url` property on the object returned by `useRouteMatch()` for creating relative links, and the `path` property for creating relative paths like so:

```js
import { Link, Route, useRouteMatch } from 'react-router-dom'

function Categories ({ categories }) {
  let { path, url } = useRouteMatch()

  return (
    <div>
      <ul>
        {
          categories.map(c =>
            <li>
              <Link to={`${url}/${c.name}`}>{c.name}</Link>
            </li>
          )
        }
       </ul>
       <Route path={`${path}/:categoryName`}>
        <Category />
       </Route>
     </div>
  )
}
```

By removing the hard-coded `'/categories'` from the links and routes in our `Categories` component, we ensure that they will work regardless of the path that caused the `Categories` component to render.

### Instructions:

1. Relocate the `Route` that renders the `Article` component into the `Articles` component (located in **Articles.js**).

Hint: Import the necessary React Router components in **Articles.js** and render a `Route` with the appropriate path.

## Exercise 11: _`Redirect`_

### Narrative:
If you take anything away from this lesson, it should be that React Router treats everything as a component. To get fully comfortable using React Router in your code, you have to embrace this idea and the declarative coding style that follows from it. For the most part, this is pretty intuitive, but it can feel a bit counterintuitive when it comes to redirecting users.

To appreciate the declarative pattern, consider a common case for redirecting a user: a user wants to access a `/profile` page that requires authentication but is not currently signed in.

```js
import { Redirect } from 'react-router-dom'

const UserProfile = ({ loggedIn }) => {
  if (loggedIn) {
    return (
      // ... user profile contents here
    )
  }

  <Redirect to='/' />
}
```
In this example, when the `UserProfile` component renders, if the `loggedIn` prop is `true`, then the component will render normally. Otherwise, the `Redirect` component will render, sending the user to the `/` page.
React Router also provides the option to redirect imperatively. You might choose to do this if you are working on an existing codebase where it is the norm, or to avoid adding local state to a component whose only purpose is to conditionally render a `Redirect`.

One scenario in which you might choose to redirect imperatively is after a form submission. It is common to redirect after successfully submitting a form, and while it would be possible to do this declaratively (by adding some local state that is `false` until the form has been submitted and then becomes `true` and conditionally rendering a `Redirect` based on the value of that state), a simple solution is to imperatively redirect in the event handler that submits the form.

To redirect imperatively, you will need access to the router's `history` object so that you can trigger a change to the current URL. React Router provides a hook, `useHistory()` that returns a [`history`](https://reactrouter.com/web/api/history) object. To update the URL, call the `history` object's  `push` function and pass it the path to which you want to navigate like so:

```js
const onSubmit => (e) => {
  postArticle({ /* form data */ })
  history.push('/articles')
}
```

### Instructions:

1. Let's practice redirecting declaratively and imperatively so that you're comfortable with both conventions. First, let's go the declarative route (we here at Codecademy are not above cheesy puns). Navigate to `'/profile'` in the browser. This route renders a profile component that should only be viewable if there is a user logged in. Alter the component to render a `Redirect` to `'/'` when `loggedIn` is `false`. Test that your code works by refreshing on `'/profile'` and ensuring that you are appropriately redirected.

Hint: You should render the component as-is if `loggedIn` is true, and otherwise render `Redirect` component. You will need to import the `Redirect` component from `react-router-dom`.

2. Great work! Now let's redirect imperatively. Navigate to **SignUpForm.js** and add an imperative redirect to the event handler that runs when the form submits. After signing up, the user should be redirected to `/profile`. Test that your code works by signing up and ensuring that you are redirected to the profile page (which you can now view since `loggedIn` is now `true`).

Hint: Import the `useHistory` hook from `react-router-dom`, call it to get a `history` object, and use the `history` object's `push` function to redirect the user to `'/profile'`.

## Exercise 12: More on `useHistory`

### Narrative:
Great job! Now that you know how to use the `history` object to redirect, let's explore its other functionality. Internally, the `BrowserRouter`'s `history` object uses the [html5 history API](https://developer.mozilla.org/en-US/docs/Web/API/History_API). In brief, browser `history` is a stack that stores the URLs visited by the user and maintains a pointer to the user's current location. This `history` API allows you to navigate through a user's session history and alter the history stack if necessary.

The router's [`history`](https://reactrouter.com/web/api/history) object has its own API with a handful of useful methods and properties that allow you to implement features that rely on session history. Some of the most common features that depend on session history include forward and back buttons.

The `history` object provides useful methods—`goForward()` and `goBack()`— for moving forward or back by one stack entry, and the more general `go(n)`, which moves `n` entries (where positive `n` values are forward and negative `n` values are backward) through history.

To use these methods, you will need to import and use the `useHistory` hook to access the `history` object, and then hook your UI elements up to the relevant `history` methods like so:

```js
import { useHistory } from `react-router-dom`

export const BackButton = () => {
  const { history } = useHistory()

  return (
    <button onClick={() => history.goBack()}>
      Go Back
    </button>
  )
}
```

### Instructions:

1. We've added forward and back buttons to the application's sidebar, but have not connected them to the `history` API. Navigate to **NavButtons.js** and add an `onClick` handler to the back button that calls the `history` API's `goBack` method.

Hint: You will need to import the `useHistory` hook from `react-router-dom`, call it to access a `history` object, and call the `history` object's `goBack` method when the user clicks the back button.

2. Next, add an `onClick` handler to the forward button that calls the `history` API's `goForward` method.

Hint: You will need to import the `useHistory` hook from `react-router-dom`, call it to access a `history` object, and call the `history` object's `goForward` method when the user clicks the back button.
