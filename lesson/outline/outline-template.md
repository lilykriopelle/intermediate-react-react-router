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

1. In this lesson, you will learn about routing–the process by which a web application determines what content to show a user based on the URL that user is visiting–as well as React Router–a popular tool for adding routing to React applications. 

2. Routing is powerful because it allows you to organize an application's views. By allowing you to display only what the user has specifically requested to see, routing enables rich, engaging, and clear user experiences. 

3. Walk the learner through the URL of the page displaying this exercise to drive the point home, eg. "Codeacdemy has lots of exercises, but you're currently looking at this one. How did we decide which exercise to show you?", and then break down the URL. The content you see is determined by the URL that you're visiting. 

### Checkpoints Summary
#### What is the purpose of these checkpoints?
### What would you like to have in the workspace for this exercise? Share your plan below.

<hr>

## Exercise # 1.5: Single vs. Multi-Page Architecture

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

## Exercise # 2: _Installing 'react-router-dom'_ and importing `BrowserRouter` 

### Which course outcomes will be covered by this exercise?

1. Learners will be able to add React Router to their projects and import the `BrowserRouter` component.

### Narrative Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/narrative/) for guidance on writing narratives for exercises._
1. In order to use React Router, you will need to include the `react-router-dom` package (the version of React Router built specifically for web browsers) in your project. [Link to docs](https://www.npmjs.com/package/react-router-dom)

2. Once you have added the package to your project, you will need to import `BrowserRouter`. BrowserRouter is the top-level component responsible for containing routing logic. React Router provides several routers (the differences between them and the reasons you might choose one over the other are outside the scope of this lesson, but you can read more about that [here](https://reactrouter.com/web/api/BrowserRouter)), and it is common to alias them to `<Router>` for the sake of simplicity and readability. You can alias `BrowserRouter` like so:

```js
import { BrowserRouter as Router} from ‘react-router-dom’
```
 
3. Talk about [React Router's philosophy](https://reactrouter.com/web/guides/philosophy) here – declarative and dynamic. Whereas other routing paradigms are static (eg. routes are predefined prior to and separate from the process of rendering), React Router requires us to render the routes themslves. Routers and the Routes they contain are components just like any other (demystify RR components so that learners don't think there's anything special about them). 

4. To add routing to your app, you will need to render a Router as the top level component. 
```js
ReactDom.render(<Router><App /></Router>)
```
5. Go into a little bit more detail about what happens when you render a router, eg. just like in the rest of React, parent components (in this case, Router) pass their props to child components. Making `<Router>` the top-level component ensures you can use the router's functionality from anywhere within your app.



### Checkpoints Summary

1. Import BrowserRouter as Router in index.js.
2. Render a Router as the top-level component of your app. 

#### What is the purpose of these checkpoints?
The learner should be able to import a router and render it as the top-level app component.

### What would you like to have in the workspace for this exercise? Share your plan below.
A code editor containing a React app with index.js open. 

<hr>

## Exercise # 3: _Basic routing with `<Route>`_

### Which course outcomes will be covered by this exercise?

1. Learners will be able to create routes.

### Narrative Summary

1. Now that you've created a router, you need to create the routes themselves. Remember, in React Router everything is a component. To add routes to an app, you need to render the `Route` component by nesting it inside a `Router. 
2. First import the `Route` component from the `react-router-dom` package.

```js
import { BrowserRouter as Router, Route } from `react-router-dom`
```

4. Next, render a `Route` inside your `Router`. The `Route` component's function is simple: to render its children when the current URL path matches the value of its `path` prop. For example, the following route renders the `AboutMe` component when the URL path matches `'about-me'`.

```js
<Route path="about-me">
  <AboutMe />
</Route>
```


### Checkpoints Summary

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/checkpoint/) for guidance on writing narratives for exercises._

1. Checkpoint one
2. Checkpoint two

#### What is the purpose of these checkpoints?



### What would you like to have in the workspace for this exercise? Share your plan below.

_Check out the [content standards](http://curriculum-documentation.codecademy.com/Content-Standards/workspaces/) for guidance on writing narratives for exercises._

## Exercise # 4: _Linking to routes_

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

## Exercise # 5: _Dynamic routes_

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

## Exercise # 6: _Nested routes_

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

## Exercise # 7: _Redirects_

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

## Exercise # 8: _`useHistory` and the history API_

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
