# Lesson Name

Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/outline/) for guidance on writing lesson outline.

## Lesson Information

### Resource(s)

_Insert any resources you used while researching to help plan your lesson._

### Learning Standards
Check out the [content standards](http://curriculum-documentation.codecademy.com/Resources/outcomes-standards-objectives/#learning-standards) for guidance on writing learning standards.

1. What is routing and why use React Router?
2. Installing and importing `BrowserRouter` from 'react-router-dom'
3. Basic routing with `<Route>`
4. Linking to routes
5. Dynamic routes
6. Nested routes
7. Redirects
8. `useHistory()` and the history API

<hr>

## Exercise # 1: _What is routing?_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to understand the purpose of routing, identify features that would require an app to implement routes, and name React Router as a popular solution for adding routing to React applications.

### Narrative Summary

1. In this lesson, you will learn about routing–the process by which a web application determines what content to show a user based on the current URL–as well as React Router–a popular tool for adding routing to React applications. 
2. Routing is powerful because it allows you to organize an application's views. By allowing you to display only what the user has specifically requested to see, routing enables rich, engaging, and clear user experiences. 
3. Walk through the basics of URL structure – protocol/domain/path.
4. Walk the learner through the URL of the page displaying this exercise to drive the point home, eg. "Codeacdemy has lots of exercises, but you're currently looking at this one. How did we decide which exercise to show you?", and then break down the URL. The content you see is determined by the URL that you're visiting. 

### What would you like to have in the workspace for this exercise? Share your plan below.
A diagram of URL structure – protocol/domain/path.

<hr>

## Exercise # 2: Single vs. Multi-Page Architecture

### Which course outcomes will be covered by this exercise?

1. Learners will be able to understand the difference between single page architecture and mult-page architecture

### Narrative Summary

1. Walk through multipage architecture: GET to different paths would request different HTML from the server, and that HTML would be displayed in the browser. Whenever a page loadsm the existing HTML is wiped out and replaced, causing a distracting flash of the screen and a clunky user experience. 
2. Single page architecture, on the other hand, leverages the power of Javascript to dynamically manipulate the DOM. In a SPA, when the user navigates to a new page, Javascript produces new markdown and renders it in the browser. If necessary, the application asynchronously fetches data in the background and inserts into the markdown on the page. Because this set-up does not require the server to produce new HTML, it eliminates that annoying flash that occurs whenever a page reloads.     
3. React Router is the most popular solution for implementing routing in single page React applications. The library provides a few simple tools for displaying different components to the user based on the URLs they visit. 

### Checkpoints Summary
We've provided a table that compares and contrasts multi-page and single page web applications. The rest of this lesson will focus on single page architecture, but before moving on, take a moment to review the table and make sure you are familiar with how each architecture works.

#### What is the purpose of these checkpoints?
To familiarize users with the differences between muti- and single-page architecture so that understand how each architecture works.

### What would you like to have in the workspace for this exercise? Share your plan below.
A table comparing single and multi-page architecture – how routing works in each, pros and cons of each, etc.

<hr>

## Exercise # 3: _Installing `react-router-dom` and importing `BrowserRouter` 

### Which course outcomes will be covered by this exercise?

1. Learners will be able to add React Router to their projects and import the `BrowserRouter` component.

### Narrative Summary

1. In order to use React Router, you will need to include the `react-router-dom` package (the version of React Router built specifically for web browsers) in your project. [Link to docs](https://www.npmjs.com/package/react-router-dom)
2. Once you have added the package to your project, you will need to import `BrowserRouter`. BrowserRouter is the top-level component responsible for containing routing logic. React Router provides several routers (the differences between them and the reasons you might choose one over the other are outside the scope of this lesson, but you can read more about that [here](https://reactrouter.com/web/api/BrowserRouter)), and it is common to alias them to `<Router>` for the sake of simplicity and readability. You can alias `BrowserRouter` like so:
```js
import { BrowserRouter as Router} from ‘react-router-dom’
```
3. Talk about [React Router's philosophy](https://reactrouter.com/web/guides/philosophy) – declarative and dynamic. Whereas other routing paradigms are static (eg. routes are predefined prior to and separate from the process of rendering), React Router requires us to render the routes themslves. Routers and the Routes they contain are components just like any other (demystify RR components so that learners don't think there's anything special about them). 
4. To add routing to your app, you will need to render a Router as the top level component. 
```js
ReactDom.render(<Router><App /></Router>, document.getElementById('root'))
```
5. Go into a little bit more detail about what happens when you render a router, eg. just like in the rest of React, parent components (in this case, Router) pass their props to child components. Making `<Router>` the top-level component ensures you can use the router's history from anywhere within your app.
6. Talk about the [html5 history API](https://developer.mozilla.org/en-US/docs/Web/API/History_API).


### Checkpoints Summary

1. Import BrowserRouter as Router in index.js.
2. Render a Router as the top-level component of your app. 

#### What is the purpose of these checkpoints?
The learner should be able to import a router and render it as the top-level app component.

### What would you like to have in the workspace for this exercise? Share your plan below.
A code editor containing a React app with index.js open. 

<hr>

## Exercise # 4: _Basic routing with `<Route>`_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to create routes.

### Narrative Summary

1. Once you've created a router, you'll need to create the routes themselves. Remember, in React Router everything is a component. To add a route to an app, you need to render a `Route` component by nesting it inside a `Router`.
2. First, you'll have to import the `Route` component from the `react-router-dom` package.
```js
import { BrowserRouter as Router, Route } from `react-router-dom`
```
3. Next, render a `Route` inside your `Router`. The `Route` component's function is simple: to render its children when the current URL path matches the value of its `path` prop. For example, the following route renders the `About` component when the URL path matches `'about'`.
```js
<Route path="about">
  <About />
</Route>
```
4. Now, navigating to "/about" will cause the URL path to match the route's `path` prop, and the `About` component will render.
5. If your router includes a `Route` with no `path` prop, then that route will always match. You can leverage this fact to make your applications render components that you want your user to see regardless of the current route by including those components as children of a route with no `path` prop. 

### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. The learner will add a route to an empty router
2. The learner will navigate to the route's path using the URL bar to test that their code works.

#### What is the purpose of these checkpoints?
To ensure that the learner knows how to add routes to an application and how to test that those routes are working as expected.

### What would you like to have in the workspace for this exercise? Share your plan below.
Code editor with index.js open and a web browser

## Exercise # 6: _Linking to routes_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to link to routes and articulate why they should use `Link` instead of an `a` tag.

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._
1. In the last exercise, you used the URL bar to navigate to a path that matched one of your application's routes. But how do you navigate from within the app itself? React Router provides a `Link` component for doing just that.
2. To create a link to a particular route, render a `Link` component and set its `to` prop equal to the location to which the link should navigate. The simplest way to specify this location is as a string: 
```js
 <Link to='/about' /> 
```
3. However, RR also allows you to provide this location as a function or object, which can be useful if you need to programatically generate the location. 
_TODO example_
4. Why should use `Link` instead of the native `a` tag? RR's `Link` component wraps the native `a` tag you are familiar with, but prevents its default behavior (navigating to the specified path and causing a page reload – the very thing we are trying to avoid with front-end routing). Internally, `Link` uses the Router's `history` prop (accessible to all of the Router's chidren) to change the URL path. When the URL path changes, the corresponding `Route` renders and that route's children display on the page.
5. In addition to providing the `Link` component, RR provides `NavLink` – a special type of link that displays differently depending on whether or not the current URL path matches the `NavLink`'s `to` prop. These can be quite useful for building navigation menus, as they differentiate between active and inactive content, enabling a user to quickly see which contet they are viewing.  

### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?


### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise # 7: _Dynamic routes_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to create dyamic routes

### Narrative Summary
1. So far, all the routes we've covered have been static, which means they match a single path. This works for certain types of routes, but not all. For example, imagine a social networking site in which every user has a profile accessible at the path (`'/users/'` + USER_ID). There is no way for us to specify a route for each unique user ID without knowing every single one, nor should we because such an approach would be brittle and verbose. What we would rather do is express the pattern at a high level so that a route will match any path of the form `'/users/'` + USER_ID. 
2. React Router allows us to do that by using URL parameters. URL parameters—placeholders beginning with a semicolon (:)—are dynamic segments of a URL that change based on the specific resource the URL is meant to display. For example, in the URL `'/users/:userId'`, `:userId` is dynamic: `'/users/1'` should display the user with id 1, and `'/users/2'` should display the user with id 2.

### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?


### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._


## Exercise # 5: Switch / exact

### Which course outcomes will be covered by this exercise?

1. Learners will be able to reason about when to use `Switch` and/or `exact` to achieve their desired routing outcomes.

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._

1. By design, a `Router` will render _all_ the `Routes` whose paths match the current URL. This can 
2. 

### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?


### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._


## Exercise # 8: _Nested routes_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to...

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._



### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?



### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise # 9: _Redirects_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to...

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._



### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?



### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise # 10: _`useHistory` and the history API_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to...

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._



### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?



### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._
