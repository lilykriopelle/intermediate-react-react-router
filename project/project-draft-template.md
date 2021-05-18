# Pet Adoption Website

## Project Information

### Resource(s)

React Router Docs

1. Resource

### Add client-side routing to a pet adoption website using the concepts you learned in the React Router lesson.

### Objective(s)

This project—a pet adoption website that allows users to view all the adoptable pets of a particular species and view the profiles of specific adoptable pets—gives you the opportunity to practice using React Router to add client-side routing to a React Application.
Currently, the app renders a `HomePage` component that fetches and displays all adoptable pets (you can view the code for this page in **pages/home/index.js**). We have also built a `PetDetailsPage` to display the details for a particular pet (**pages/detail/index.js**), but this component will not render until you create a route to display it.
Your tasks will be to add client-side routing to the application using React Router so that:
* The `HomePage` component responds to the browser's current URL by displaying only pets of the species the user wishes to view.
* The `PetDetailsPage` page displays when the browser's current URL includes a specific pet's `id`.
* The `PetDetailsPage` displays data for the correct pet based on the `id` in the URL parameters' values.
* When the user searches for a pet in the search bar, they are redirected to `/search` and shown the `SearchPage`, which uses the query parameter called `query` to filter pets by name.
* When a user clicks a pet whose details are not available, they are redirected to `/pet-not found`, which displays a `PetNotFoundPage`.
* From the `PetNotFound` page, users can click  "Go Back" button that will take them to page they were previously on.

Before you get started, spend some time familiarizing yourself with the project’s starting code. In particular, take note of the `HomePage`, `PetDetail`, `Search`, and `PetNotFound` components, as well as **App.js**, as you'll be working primarily in these files.
This lesson uses Mock Service Worker (MSW) to replicate the functionality of an external API. To use MSW, you’ll want to use Google Chrome and enable third-party cookies.


### Thumbnail Image URL: https://unsplash.com/photos/bhonzdJMVjY

<hr>

## Task Group #1: Installing React Router and adding a Router to your project.

### Task #1
Install `react-router-dom` so that you can use React Router components in your project. To check that you were successful, ensure that `react-router-dom` appears in the `dependencies` object located within your project's `package.json` file.

### Hint
Use `npm install --save`.

<hr>

### Task #2
In **App.js**, import React Router's `BrowserRouter` component and alias it to `Router`.

### Hint
To alias `BrowserRouter` to `Router`, use the `as` keyword.

<hr>

### Task #3
Wrap your applications contents in a `Router` so that your components can use React Router's components and hooks. 

### Hint
`Router` should be the outermost component rendered by your `App` component.

<hr>

## Task Group #2: Create Your First Route

### Task #4
Great job! Now that you've wrapped your application in a `Router`,  you are ready to start adding `Route`s. First, create a `Route` that renders the `HomePage` component so that this component only appears to the user when the URL's path demands it. The desired functionality is for the home page to render when there is no path (this should render all the pets) or `/:type`, where `:type` corresponds to one of the species of pets (in which case the home page should render only pets of the given species). 

You'll need to import the `Route` component from `react-router-dom`.

### Hint
The syntax for importing `Route` will look like:
```js
import { NameOfComponent } from 'name-of-package';
```

<hr>

### Task #5
Next, wrap your `HomePage` component in a `Route` component. The `Route` should have a `path` prop of `/:type?` so  that the home page will render whatever the species provided in the URL. Note: `?` indicates an optional URL parameter. Since we want the `HomePage` to render even when no species is specified in the URL, we need to make the `:type` parameter optional.

Test that your code works by clicking on the 'Cats' link in the navigation menu – the homepage should still display since the new URL's path (`/cat) matches the path of the `Route` that renders `HomePage`.  

### Hint
The syntax for writing a `Route` that renders `SomeComponent will look like:
```js
<Route path='/path/for/route'>
  <SomeComponent />
</Route>
```

<hr>

## Task Group 3: Using URL Parameters in Your React Components

### Task #6
Notice that even after you navigate to `/cats`, the `HomePage` component still renders all the pets (not just the cats). Your next task is to fix that by building on the code we've provided for the `HomePage` component. 

In **pages/home/index.js**, import the `useParams` hook from `react-router-dom`.


### Hint
The syntax for importing `someHook` from `name-of-package` will look like:
```js
import { someHook } from 'name-of-package';
```

<hr>

### Task #7
Within the `HomePage` component, we've defined a variable, `type`, and set it equal to an empty string. Delete this variable declaration, and instead use destructuring assignment to get the value of the `type` URL parameter, which you can access by calling `useParams`, and store it in a constant called `type. We've passed `type` to our API's `getPets` method so that the URL parameters affect which species of pets the user sees on the home page. 

To test that your code works, click on one of the species links – you should now see only pets of that type. 

### Hint
The syntax for using destructing assignment to get the value of `someValue` from the object returned by a call to `someHook` will look like:
```js
const { someValue } = someHook()
```

<hr>

## Task Group 4: Replacing `a` Tags with React Router Elements

### Task #8
When you tested your work for the last task by clicking on one of the species links in the navigation bar, you may have noticed a conspicuous page reload. Recall that this happens when we use native `a` tags (instead of React Router's `Link` and `NavLink` components) to navigate to client-side routes. 

In the Navigation component (located in **components/navigation/index.js**), improve your user's experience by replacing the `a` tags with React Router's `NavLink` component. First, you will have to import `NavLink` from `react-router-dom`.

### Hint
The syntax for importing `NavLink` will look like:
```js
import { SomeComponent } from 'name-of-package';
```

### Task 9
Next, replace the `a` tags in the `Navigation` component with `NavLinks. As you give these `NavLink` components their props,  remember that `NavLink` has a `to` prop instead of the `a` tag's `href` attribute.

Recall that `NavLink` also accepts an `activeClassName` property that will be applied to the `NavLink` whose `to` prop matches the current URL.In `index.css`, we've written a CSS selector for the class `.nav-link-active` that will darken the background of any element with that class name. Give your `NavLink` components an `activeClassName` prop and set it equal to `".nav-link-active"` so that the `NavLink` whose `to` prop matches the current URL will appear darker than the others.

### Hint
The syntax for writing a `NavLink` looks like:

```js
<NavLink
  to="/path"
  className="non-active-classname"
  activeClassName="active-classname"
>
  Text
</NavLink>

```

### Task 10
Nice job! While you're replacing native HTML elements with React Router components, go ahead and change the `a` tags in the `HomePage` component (**pages/home/index.js**) to React Router `Link`s. Like `NavLink`, the `Link` component has a `to` property in place of  the `a` tag's `href`.

### Hint
The syntax for writing a `Link` looks like:

```js
<Link
  to="/path"
>
  Text
</Link>

```

<hr>

## Task Group 5: Adding Another Route

### Task 11
Great work! Next let's add a `Route` to display the detail view for an individual pet, which should display whenever the URL matches the form `/:type/:id`.  

Add a `Route` to your `Router` with a `path` prop of `/:type/:id` that renders the `Detail` component we've imported for you. To test that your code works, click on one of the pets listed on the home page. You should be redirected to the detail view of a single pet.


### Hint
The syntax for writing a `Route` that renders `SomeComponent will look like:
```js
<Route path='/path/for/route'>
  <SomeComponent />
</Route>
```

### Task 12
You may be wondering why the whose details you are viewing is not the one you clicked on. That's because we've hard-coded a pet `id` in the `PetDetailsPage` component. To make this page render the details for the actual pet your user has selected, update the value of `id` in **pages/detail/index.js** to match the value of the URL parameter named `id`. To do so, you'll need to first import the `useParams` hook, then call it and use destructuring assignment to get the value of the `id` property on the resulting object and store it in a constant named `id`.

To test that your code works, refresh the page. You should see the details for the pet whose picture you clicked previously. 

### Hint
The syntax for using destructing assignment to get the value of `someValue` from the object returned by a call to `someHook` will look like:
```js
const { someValue } = someHook()
```

### Task 13
Great work! There's one problem though: now, when you navigate to `/:type/:id` not only will you see the detail view for a particular pet, but also the list of all pets that share the current pet's species. This is because React Router's `Router` will render _all_ the `Route` components nested within it whose `path` matches that of the current URL. 

Return to **App.js** and wrap your `Route`s with a `Switch` component so that only one `Route` will render at a time. Remember: `Switch` renders only the _first_ `Route` that matches the current URL, so you'll have to think about what order you should list your routes in to achieve the desired behavior. Test your code to ensure that the `HomePage` renders when the URL path matches `/:type` and the `PetDetailsPage` renders when the URL path matches `/:type/:id`.

### Hint
You'll want to order your routes from most to least specific.


## Task Group 6: Adding a Search Feature

### Task 14
Nice job. Your next task will be to add a search feature to the pet adoption website. 

First, in **App.js** add a `Route` that renders the `SearchPage` component we've imported for you. 

### Hint
You'll want to order your routes from most to least specific.

### Task 15
Next, in **pages/search/index.js**, import React Rouer's `useLocation` hook.

### Hint
You should import `useLocation` from `react-router-dom`.

### Task 16
Next, call `useLocation` and get the value of the `search` object it returns.

### Hint
You can use destructuring assignment to get the value by doing something like:
```js
const { nameOfProperty } = nameOfHook()
```

### Task 17
Pass the `search` object to the [`URLSearchParams`](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) constructor and store the result in a constant called `queryParams`.

### Hint
Documentation about the `URLSearchParams` interface is accessible [here](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams).

### Task 18
Last, you'll have to pass the query parameter to the API call to `getPets`. Observe that usingthe search bar appends a query parameter called `search` to the search page's URL. To filter all the pets by the value of the `search` query parameter, you will have to add a second argument to the search page's call to `getPets`. That argument should get the value of the `search` query parameter out of the `queryParameters` object.

### Hint
To get a property `nameOfProperty` from a `URLSearchParams` object, you can use the `get` method like so:

```js
searchParamsObject.get('nameOfProperty')
```

## Task Group 7: Adding a `PetNotFound` Page 

### Task 19
Nice work! The next (and last) feature you'll add to the application is a page to display in the event that the user clicks on a pet whose details are not yet available. First, in **App.js**, add a `Route` that renders the `PetDetailsNotFound` component we've imported for you when the current URL's path is `'pet-not-found'`. 

### Hint

### Task 20
If a pet's details are not found, an API call to `getPetDetails` for that pet's `id` will return an error. Your task is conditionally redirect the user to '/pet-not-found' whenever that happens. In **pages/details/index.js**, import React Router's `Redirect` component.
### Hint
You should import `Redirect` from `react-router-dom`.

### Task 21
Next, update the component to render a `Redirect` whose `to` prop matches the `Route` you added to your application if the `getPetDetails` API call returns an error and return the pet's details otherwise.

### Hint
If the API call returns an error, then `error` will be `true`. When that happens, render a `Redirect` whose `to` prop equals `/pet-not-found`.

### Task 22
It would be nice if the user could easily navigate away from the `PetDetailsNotFound` page to the page they were on before. We've provided a button for this purpose, but you will need to use React Router's `history` object to imperatively redirect the user when it is clicked. First, import React Router's `useHistory` hook.

### Hint
You should import `useHistory` from `react-router-dom`.

### Task 23
Call `useHistory` to get access to React Router's `history` object.

### Hint
The `useHistory` hook returns the `history` object when called.

### Task 24
Add an `onClick` prop to the `Go Back` button. Use the `history` object's `goBack` method to redirect the user to the previous page.

### Hint
To use the `history` object's `goBack` method, you'll need to call it like so: `history.goBack()`.
