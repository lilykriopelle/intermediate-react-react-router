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

1. Walk through multipage architecture: GET to different paths would request different HTML from the server, and that HTML would be displayed in the browser. Whenever a page loads the existing HTML is wiped out and replaced, causing a distracting flash of the screen and a clunky experience.
2. Single page architecture (SPA), on the other hand, leverages the power of Javascript to dynamically manipulate the DOM. In a SPA, when the user navigates to a new page, Javascript produces new markup and renders it in the browser. If necessary, the application asynchronously fetches data in the background and inserts into the markup on the page. These partial changes do not require a full page load.
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

## Exercise # 5: _Linking to routes_

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
1. The learner will import `Link` from RR and create a series of `Link` components.
2. The learner will import `NavLink` from RR and create a series of `NavLink` components.

#### What is the purpose of these checkpoints?
To ensure the learner knows how to import and use `Link` and `NavLink`.

### What would you like to have in the workspace for this exercise? Share your plan below.
Code editor and web browser.

## Exercise # 6: _Dynamic routes_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to create dynamic routes

### Narrative Summary
1. So far, all the routes we've covered have been static, which means they match a single path. This works for certain types of routes, but not all. For example, imagine a news site in which every article has is accessible at the path (`'/articles/'` + title). There is no way for us to specify a route for each unique article without knowing every single title, nor should we specify a unique route for every article because such an approach would be brittle and verbose. What we would rather do is express the pattern at a high level with a route will match any path of the form `'/artciles/'` + title.
2. React Router allows us to do that by using URL parameters. URL parameters—placeholders beginning with a semicolon (:)—are dynamic segments of a URL that change based on the specific resource the URL is meant to display. For example, in the URL `'/articles/:title'`, `:title` is dynamic: `'/articles/article-one'` should display the article with title `'article-one'` and `'/articles/article-two'` should display the article with title `'article-two`. A URL can have multiple dynamic segments (eg. `'/articles/:title/comments/:commentId'`) or none (eg. `'articles'`).
3. To create a dynamic route, simply provide a `path` prop that includes a dynamic segment. _walk through creating a route for an article page that renders a single article Now, when we navigate to `'/articles/:title`, an `Article` component will be rendered.  
4. It is common to use URL parameters to retrieve and/or display data in the component that a dynamic route renders. For example, our `Article` component might need to display the title of the current article. _Walk through the `useParams` API and show it in context by displaying the article title in the article component_

### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. The learner will create dynamic route and test that it works by navigating to a route that matches.
2. The learner will import and use the `useParams` hook to get the value of the route param and display it on the page.

#### What is the purpose of these checkpoints?
Learners will be able to write dynamic routes, reason about what URLs will match a route's `path`, and be able to use `useParams` to get the value of route params from within a component.

### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise #7: Switch / exact

### Which course outcomes will be covered by this exercise?

1. Learners will be able to reason about when to use `Switch` and/or `exact` to achieve their desired routing outcomes.

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._

1. By design, a `Router` will render _all_ the `Routes` whose paths match the current URL. This allows us to compose layouts in which multiple components should appear or disappear based on the current URL (for example, an application in which the sidebar and main display respond to changes in the current URL). But sometimes, this design choice can produce unintended results. Consider the following (relatively common) setup:
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
2. What should happen when the user navigates to `'articles/new'`? The `NewArticle` component should appear. But what actually happens when the user navigates to that URL is that _all_ routes match – the first route's `path` prop matches exactly, the second route will match `new` to the URL parameter `:title`, and the last route will match because both begin with `/articles`. Because all routes match, the application will render the `NewArticle`, `Article`, and `Articles` components simultaneously.  
3. RR provides several mechanisms for preventing this sort of unintended rendering. The first is the `Switch` component. When wrapped around a collection of routes, `Switch` will render the first of its child routes whose `path` prop matches the current URL.
_show earlier example wrapped in `Switch` component, walk through what happens when you visit 'articles/new' vs 'articles/title-one'_
4. Because the `Switch` checks routes sequentially, the order in which Routes are rendered matters.
_show the same example with routes reversed, explain that now you will never be able to render the `NewArticle` component since the `Switch` will always render the first Route that matches the current URL_  
5. Sometimes you may want to leverage RR's composability and render multiple routes simultaneously (this would prevent you from using a `Switch` component) while also ensuring your router distinguishes between static paths and paths including URL parameters. Consder the following example
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
6. Any path will match first route, so the the `Home` component will be rendered whether the user is at '/' or '/sign-up'. _talk a little bit about why this can be useful, eg. for making sure that layout components, menus and such, dislplay no matter what_ But what if you only want the `Home` component to be visible to users on the home page and not to those who have navigated to `/sign-up`? By using RR's `exact` prop on the first route, you can ensure that the route will match _only if the current URL is an exact match_.
```js
 <Route exact path='/'>
   <Home />
 </Route>
 ```
7. Now, when a user visits '/', the `Home` component will render. But when a user visits '/sign-up', only the second route will match and only the `SignUp` component will render.  
8. Talk about `strict` and `sensitive` here? I rarely find that these are necessary, so I would probaby recommend just pointing learners to the docs at this point.

### Checkpoints Summary
_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._
1. Learner will use a combination of `Switch` and `exact` to make a buggy router behave as desired.

#### What is the purpose of these checkpoints?
To cement the learner's understanding of `Switch` and exact and to give learners the chance practice reasoning about and modifying the structure of a router to achieve a specific set of goals.

### What would you like to have in the workspace for this exercise? Share your plan below.
Code editor and web browser.

## Exercise # 8: _Nested routes_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to build nested routers.

### Narrative Summary
1. Up to this point, we have been working with routers that are small enough to be rendered entirely in a single file. But as an application grows in scope, it can be useful to render routes from multiple components. This allows us to locate routing logic near the related UI logic – you can imagine that on large code bases, it can be advantageous to have code organized this way. Splitting Routes up this way also makes an application more lightweight – if a user never navigates to a part of the application that necessitates a route to render, then it never will.
2. Let's return to our newspaper example, and imagine that the engineering team is building out a `Topics` feature that will organize news articles by their category – world news, U.S. news, etc. In addition to a `Categories` component (which will render links to each individual category), the team has created a `Category` view that will display all the articles for a given category. Previously, we might have written a router like this:
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
3. There's nothing wrong with this way of routing, but as soon as your start to introduce more features into your application, may find that having all the routes contained in a single router becomes a bit unweildly _show a router with articles/categories/log in/etc_. The way around this is to get comfortable rendering routes from components elsewhere in your app.
4. For example, consider this `Categories` component, which iterates through a list of categories and links to each:
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
5. Clicking on that a link rendered in this component will cause the URL to change; it will match the route from our previously defined router. But note that from inside this component, we have no way of knowing what component will be rendered when the URL updates.
6. Because RR handles routing dynamically (eg. routes exist when they are rendered), you can relocate the route to the components in which they are relevant.
```js
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
7. Rewriting your routes this way makes it very obvious what will happen when the user clicks on a link.
8. _TO DO iterate on the above example using `match` `path` and `url` to clean up and generalize_

### Checkpoints Summary
_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._
1. Learner will be given a router with lots of top level routes and practice nesting them in the appropriate components.

#### What is the purpose of these checkpoints?
To make sure that learners understand how to nest routes and can refactor routers by nesting routes where appropriate.

### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise # 9: _Redirect_ and _useHistory_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to use RR's `Redirect` component.

### Narrative Summary

1. If you take anything away from this lesson, it should be that RR treats everything as a component. To get fully comfortable using RR in your code, you have to embrace this idea and the declarative coding style that follows from it. For the most part, this is pretty intuitive, but it can feel a bit counterintuitive when it comes to redirecting users.
2. Consider a common case for redirecting a user: a user wants to access a page that requires authentication, but is not currently signed in.
3. Walk through the declarative way to to accomplish redirect: the component receives a boolean prop signifying whether the user is logged in and the component renders a `Redirect` if they are not.
4. For contrast, walk the user through the imperative way to redirect. Eg. introduce the `useHistory` hook and after a form form is submitted, redirect using `history.push`. It's possible to do this declaratively (add state to the component that updates when the form is submitted, use this state to conditionally render a `Redirect`), but adding that state introduces additional complexity, so being imperative might be fine in this instance. _NOTE: I would be interested in discussing this with John. My personal preference is to avoid adding state purely for the purpose of being able to do declarative redirects, but people have *feelings* about stylistic consistency, so..._

### Checkpoints Summary
_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._
1. Render a `Redirect` and test it in the browser
2. Write an imperative redirect using `history.push` in an event handler.

#### What is the purpose of these checkpoints?
Make sure learners are comfortable with imperative and declarative redirects.

### What would you like to have in the workspace for this exercise? Share your plan below.
Code editor and web browser.

## Exercise # 10: _`useHistory` and the history API_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to use the `useHistory` hook and the history API to navigate forward and backward through a user's browser history.

### Narrative Summary
1. Walk the user through the html5 history API.
2. Explain why you might want to use history, common features eg. forward and back buttons, keeping track of previously viewed pages, etc.
3. Show how to import and use the hook and call some of the methods on the history object.

### Checkpoints Summary

1. Connect a "back" button to the history API (`goBack`) and test it in the browser.
2. Connect a "forward" button to the history API (`goForward`) and test it in the browser.

#### What is the purpose of these checkpoints?



### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._
