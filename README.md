# FrontEndExpert
## Taite Thomas
### 11/18/23
#### algoexpert.io
---

# React Crash Course

## 0: Setup

```sh
cd FrontendExpert

mkdir react_crash_course
cd react_crash_course

mkdir 1_introduction
mkdir 2_react_basics
mkdir 3_jsx
mkdir 4_props
mkdir 5_event_driven_programming
mkdir 6_state
mkdir 7_component_lifecycle
mkdir 8_refs
mkdir 9_imperative_react
mkdir 10_contexts
mkdir 11_components_list
mkdir 12_performance
mkdir 13_writing_custom_hooks
mkdir 14_portals
mkdir 15_class_based_components
mkdir 16_error_handling
mkdir 17_debugging_react
mkdir 18_best_practices
mkdir 19_react_under_the_hood
mkdir 20_companion_libraries

```

Next, open your VSCode editor to the folder of 'react_crash_course'.

Finish by updating Git:

```sh
cd algoexpert.io

git status
git add .
git commit -m "Began FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 1: Introduction

### Key Terms

### Notes from the video

Other Crash Courses in FrontendExpert: Learning about common interview topics of Frontend Dev
- Companies want to see you be good with Vanilla JS
    - They can teach you everything else after...
        - Smaller and medium sized companies may test you out on the actual frameworks, so React is a good one to learn

This course: Learning about a JS Framework, React
- More realistic scenarios
- Start basics 
- Work way up using industry best practices
- React = Very valuable skill to have
    - You will probably work on a React project at some point
    - Good / translatable skills come from learning React

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 1 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```


## 2: React Basics

### Key Terms

#### React

A JavaScript library developed by Facebook for building user interfaces.
- Uses a component-based architecture to create interfaces with an intuitive declarative approach

Learn more: https://react.dev/

#### Component

A reusable independent piece of a user interface.
- In modern React: Components are usually functional components
    - ie. simply functions that return JSX

Note: JSX = JavaScript XML, a syntax extension for linking XML and HTML in JS.

#### JSX (Short for JavaScript XML)

A JavaScript syntax extension for inlining XML and HTML in JavaScript.

For example: This code could be compiled into standard JavaScript functions calls to create a heading element:

```js
const h1 = <h1>Hello World</h1>;
```

Learn more: https://react.dev/learn/writing-markup-with-jsx

#### ReactDOM

A package used with React to work as the bridge between React elements and the actual DOM in the browser.
- The most frequently used ReactDOM function: `render`
    - Adds a component to the DOM

For example:

```js
ReacTDOM.render(
    <h1>Hello World</h1>,
    document.getElementById('root')
);
```

Learn more: https://react.dev/reference/react-dom

### Notes from the video

#### Setup

```sh
cd 2_react_basics
echo > 
```

#### Key Characteristics

React: JS Library for Building UI
- Sounds vague, but will expand on that.

Key Characteristics:
- Declarative: Describe what UI should look like, not all of implementation details
- Component-based: Reusable pieces of UIs, like custom HTML tags
- Undirectional data flow: Data flows in 1 direction (parents, down to children)
    - dynamic

Let's look closer at Components.

#### Component-Based

Component: Not specific to React, seen in a lot of Frameworks.

When looking at a UI, what are the different components?
- Generally speaking: Anything reusable or self contained should be a component

Example of FrontendExpert Questions page:

![Example of Components from AlgoExpert.io Website](./figures/react/0.png)

Components:

1. Progress indicator
- sub-component: title/text 
- sub-component: progress bar
- sub-component: 2 buttons below progress bar

2. Interview questions
- sub-component: tab car component (category vs. randomly)
- sub-component: container for all interview questions (4 of the same components with different props/params)
    - sub-component: list of interview questions


#### JSX

React components use JSX (JavaScript XML), ie. an extension for JS XML
- Not specific to React (Vue uses it)
    - Compiles into React, though

- Essentially: Using what looks like HTML in our JavaScript

```js
const hello = <p>Hello World</p>;
```

Note: See how there is a semicolon at the end, because this is still JavaScript.

How does this code above compile into JavaScript/what does it turn into?
- It goes from JavaScript code into React.createElement!

The following creates a React Element, which can be later append to a DOM:

```js
const element = (
    <p id="hello">
    Hello <em>World</em>
    </p>
);
```

=>

```js
var element = React.createElement(
    'p',
    { id: "hello" }, // optional props, key value pairs
    'Hello ', // extra parameters (children)
    React.createElement('em', null, 'World') // another React.createElement !
);
```

Notes:
- We use a parentheses for a multi-line JavaScript expression
- React.createElement is similar to document.createElement
    - We almost NEVER use this function directly, given that JSX compiles into this
        - Good to know, nonetheless!

Parameters:

React.createElement(type, [props], ...children)
- type: the type of _ our JSX compiles into
- optional props: object

#### ReactDOM

Final step: Take the React element we just created, and put it on the DOM. How do we do this?

Package: ReactDOM
- Package for inserting React elements into the DOM

```js
ReactDOM.render(element, DOMContainer);
```

#### Functional Components

We said we want to use re-usable components.
- So far: We have put JSX into variables
- What we actually want: Functional Components!

Functional Components: Functions that returns a React element ie. JSX
- 

Example:

```js
function SayHello() {
    return <p>Hello World</p>;
}
```

->

```js
// using the SayHello function from above^
function App() {
    return (
        <div>
            <SayHello /> // component is used as an element
            <p>Welcome to React!</p>
        </div>
    );
}
```

Notes:
- Instead of camel case, we are using Pascal case
    - Uppercase first letter: Custom components
    - Lowercase first letter: Standard HTML element
        - not all custom components will be functions though... there are classes (technically)

#### Creating React Apps

Many ways to create a React app, but let's start with the most common: `create-react-app`.

```sh
cd react_crash_course

npx create-react-app test-app
```

Notes:
- npx: comes with node.js
- test-app: the name of the new app

Now, run the app on localhost:

```sh
cd test-app

npm start
```

In your browser (at http://localhost:3000/), you should now see the standard template that comes with a React app.

Let's look at all of the files and directories that were created for us when we used `create-react-app`.

- `node_modules`: all of the dependencies downloaded
    - if you have worked with any other projects with node before, this is the same thing
    - you almost never need to open this/do anything with this!

- `public`: Contains vanilla files that are needed to send up to the browser
    - favicon.ico: icon that browser shows
        - make sure to change this!
    - index.html: the main file of our website
        - for the mostpart: standard HTML
        - has some interesting/important lines of code (these are not super important):
            - apple-touch-icon: the file used if an iPhone user saves your website to the home page
            - manifest.json file: what the icons/names should be
            - title tag: name of website
                - Default: 'React App'
            - body: 
                - noscript is there for users who have disabled JS
            - div: 
                - this is where we append values to in the DOM
    - logo192.png: used for template (we can delete this)
    - logo512.png: used for template (we can delete this)
    - robots.txt: tells robots how to treat your website
        - Example: google search engine

- `package-lock.json`: Standard file for node application

- `package.json`: Standard file for node application

- `README.md`: Has helpers for those starting out

- `src`: Source. The main directory we work from!
    - advice: organize this directory, or it will balloon on you
        - advice: 1 components per JS file, then organizational structure to find the files

    files in src:
    - logo.svg: a logo we probably won't use (can delete)
    - reportWebVitals.js: implementation of a function we probably won't use (can delete)
    - setupTest.js: If you do choose to write tests in App.test.js, this will run before
    - .gitignore: React automatically makes a git repo, so this will untrack certain files

    - App.css: The styling guide for the app
    - App.js: Will come back to this later
    - App.test.js: Can be useful (it shows how to write tests)
    - index.css: Styling guide
    - Index.js: Entry point of our application!

Note: What does index.js actually do:

```js
// imports
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

// React.DOM.render is what puts React on the page
// - here, we are appending to the root from index.html
//      - we are appending App (will talk more about React.StrictMode later)
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App /> // can put other imports or HTML here
  </React.StrictMode>
);

reportWebVitals(console.log); //  we do not need this, usually can delete it! (it gives performance metrics ... )
```

Note: create-react-app uses webpack, which essentially ignores the public directory

Let's take a look at the App.js file that Index.js is using:

```js
// app.js
import logo from './logo.svg'; // notice: photo is imported, then used as {logo} below!
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
// notice how App has to be exported (so that index.js can import it later)
export default App;
```

Notes:
- Usage of className instead of class

Let's change it to look like this:

```js
// app.js
// import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div>
      <SayHello />
      <SayHello />
    </div>
  );
}

function SayHello() {
  return <p>Hello World</p>;
}

export default App;

```

Notes:
- We will go much further on components in this crash course
- I commented out the top line of code that imports logo.svg since I am no longer importing it into App.js

#### Takeaways

Pros of create-react-app:
- saves TONS of time

Cons of create-react-app:
- many un-needed files that we have to delete

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 2 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 3: JSX

JSX = Short for JavaScript XML
- What happens when you try and combine JavaScript and HTML into one.
- Extremely important when working with React!

### Key Terms

#### React.Fragment

A React container component that renders its children without adding any additional DOM nodes.
- Can be used for returning multiple adjacent elements without wrapping them in an unnecessary element

Example:

```js
<React.Fragment>
    <h1>Hello World</h1>
    <p>React is Awesome!</p>
</React.Fragment>
```

Fragments can also be created by using an empty tag, rather than the `Fragment` export from React. For example:

```js
<>
    <h1>Hello World</h1>
    <p>React is Awesome!</p>
</>
```

Learn more: https://react.dev/reference/react/Fragment

#### Conditional Rendering

The process of changing the returned element of a component based on some condition.
- Can be achieved in a variety of ways
    - Most common: Utilizing ternary operators OR short circuit evaluation
        - This works because the following all render absolutely nothing:
            - null
            - undefined
            - true
            - false

For example:

```js
<React.Fragment>
    { myBool ? <h1>Hello World</h1> : null }
    { myOtherBool && <p>React is Awesome!</p> }
</React.Fragment>
```

Learn more: https://react.dev/learn/conditional-rendering

### Notes from the video

#### Setup

Head into `test-app/src` for this:

```js
// App.js
import './App.css';
import React from 'react';

export default function App() {
    return (
        <h1>Hello World</h1>
    );
}
```

```css
/* App.css */
.center {
    text-align: center;
}
```

#### JSX

Interesting import - You used to need this, but now you do not:

```js
import React from 'react';
```

Why don't we need it anymore?
- Any JSX used to compile into React elements
- Modern React: You do not need it
    - We will use it for something else, so keep it in!

Next, let's look at the `export default`:

```js
export default function App() {
    return (
        <h1>Hello World</h1>
    );
}
```

Because this function returns some JSX ie. `<h1>Hello World</h1>`, this function becomes a component.

#### Self-Closing Tags

Next, let's look at some things that are different between JSX and standard HTML.

When you use a self-closing tag, you must do the syntax with the forward slash at the end. Example:

```js
export default function App() {
    return (
        // error
        <h1>Hello <br> World</h1>
        // good
        <h1>Hello <br /> World</h1>
    );
}
```

#### Fragments

Let's talk about returning multiple JSX elements:

```js
// this gives an error
export default function App() {
    return (
        <h1>Hello World</h1>
        <p>Test<p>
    );
}
```

This would give an error, since we must always return a single JSX element.

What about this way, if we wrap the returns in a `div`?

```js
import './App.css';
import React from 'react';

export default function App() {
    return (
        <div>
            <h1>Hello World</h1>
            <p>Test</p>
        </div>
    );
}
```

This works! Try this out in your browser now:

```sh
cd test-app

npm start
```

You should see 'Hello World' at the header, and 'Test' beneath it.

What if we do not want to add a `div` to our code?
- This adds div to the DOM
    - Adding extra elements to the DOM will eventually slow down the page, make screen readers jobs hard, etc.

How do we wrap all of the elements?

React has built-in fragments just for this job!

Method #1:

```js
import './App.css';
import React from 'react';

export default function App() {
  return (
      <React.Fragment>
          <h1>Hello World</h1>
          <p>Test</p>
      </React.Fragment>
  );
}
```

Method #2:

```js
import './App.css';
// import React from 'react';

export default function App() {
  return (
      <>
          <h1>Hello World</h1>
          <p>Test</p>
      </>
  );
}
```

Notes:
- React.Fragment comes from import statement on Line 2
- After saving the App.js file, it will look the same, but this is better
    - We can use empty tags if we'd like
        - 1st difference: Can delete import on line 2
        - 2nd difference: No way to add a prop to the empty elements

My takeaway: For the mostpart, I will use the React.Fragment!

#### JavaScript Expressions

How do we use JavaScript Expressions inside of our JSX?

```js
// App.js
import './App.css';

export default function App() {
  const name = 'Myles';
  return (
      <>
          <h1>Hello {name.toUpperCase()}</h1>
          <p>Test</p>
      </>
  );
}
```

Notes:
- Curly braced syntax = JavaScript
- This is safe from injection attacks, as the JSX gets passed as a string regardless
    - even if a malicious actor tried to pass bad code...

#### Conditional Rendering

Start by writing some code that returns a different value depending on an error:

```js
// App.js
import './App.css';

export default function App() {
  const error = true;
  if (error) {
    return <h1>Error!</h1>;
  }
  return <h1>Success!</h1>;
}
```

This is one way - but we have more options!

Ternary operator:

```js
import './App.css';

export default function App() {
  const error = false;
  return error ? <h1>Error!</h1> : <h1>Success!</h1>;
}
```

Both of these methods are good, but have totally different return statements.
- You may not want this if it is a small part of the JSX

What to do now? Return a fragment with 2 different ternaries:

```js
import './App.css';

export default function App() {
  const error = true;
  return (
    <>
    {error ? <h1>Error!</h1> : null}
    {!error ? <h1>Success!</h1> : undefined}
    </>
  );
}

```

Notes:
- Using null is more popular than undefined/other values (for the else portion of if-else)
- Can use short circuit evaluation (&& and ||) if you'd like instead

One more way to do conditional rendering:

```js
import './App.css';

export default function App() {
  const error = false;
  return <h1>{error ? 'Error' : 'Success'}</h1>
}
```

Notes:
- When in the curly braces, make sure to use '' for strings since we are in JavaScript!

#### Attributes / Props

Let's remove the code from above and start looking at attributes, but better known as props!

This will create an input box that cannot go longer than 3 characters:

```js
import './App.css';

export default function App() {
  return (
    // using the Fragements again ...
    <>
      <label htmlFor="input">Input: </label>
      <input id="input" type="text" maxLength="3" />
    </>
  );
}

```

Notes:
- maxLength is camelCase, this is because JS/JSX decided to use camelCase
- for is a reserved word in JavaScript, so JSX uses htmlFor instead

We can also use JavaScript expressions for these values!

```js
import './App.css';

export default function App() {
  const props = {
    id: 'input',
    type: 'text',
    maxLength: '3',
    
  }
  return (
    <>
      <label htmlFor="input">Input: </label>
      <input {...props} placeholder="user" />
    </>
  );
}

```

Note: This combines props with the standard syntax, hence the `placeholder="user"`.

Next, change the code up so all we return is a paragraph:

```js
import './App.css';

export default function App() {
  return <p className="center">Hello World</p>
}

```

Notes:
- we have to use className instead of class=
- This code will center the 'Hello World'

Next, we can also use inline styles:

```js
import './App.css';

export default function App() {
  return <p style={{
    color: "red",
    textAlign: 'center',
    fontSize: '48px' // 48 works too
  }}>Hello World</p>
}

```

Notes:
- This makes the text large, red, and in the middle of the screen
- Good practice: Adding units at end of fontSize 
    - avoid using pixels

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 3 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 4: Props

Props in React = Things you pass from component to component (Simple, but useful!)

### Key Term

#### Props

A JavaScript object passed as a parameter to functional components.
- Contains all of the key-value pairs that were passed as attributes to the component.

For example, look at this JSX:

```js
<MyComponent message="hello" number={42} />
```

The `MyComponent` function would take in props with two key-value pairs:

```js
function MyComponent(props) {
    console.log(props.message); // "hello"
    console.log(props.number); // 42
    return <h1>Hello World!</h1>;
}
```

Learn more: https://react.dev/learn/passing-props-to-a-component

### Notes from the video

#### Setup

Current state of App.js:

```js
// import './App.css';

export default function App() {
  return (
    <>
      <h1>Hello Conner</h1>
      <h1>Hello Clement</h1>
    </>
  );
}
 
```

#### Props

Props = Attributes for our components
- Components: Custom HTML tags
- Props: Parameters to those functions

Motivation behind props?
- When there is redundancy, we want to make helper functions to avoid repeating code.

Example, turning the example from above into better code by using props:

```js
export default function App() {
  return (
    <>
      <Hello name="Conner" />
      <Hello name="Clement" />
      <Hello name="Myles" />

    </>
  );
}

function Hello(props) {
  return <h1>Hello {props.name}</h1>
}
```

Notes:
- We take in 'name' as a parameter to the function + we pass in the parameter via props

#### Destructuring Props

One thing people find annoying about props is that because we pass in 1 props variable, there is no way to look at the function and see what the prop expects.

Way to improve: Using Destructuring syntax!

```js
export default function App() {
  return (
    <>
      <Hello name="Conner" />
      <Hello name="Clement" />
      <Hello name="Myles" />
    </>
  );
}

function Hello({name}) {
  return <h1>Hello {name}</h1>
}
```

You can now look at this function and easily know what the function needs.

#### Default Props

We can use the destructuring to also have default values.

```js
// import './App.css';

export default function App() {
  return (
    <>
      <Hello name="Conner" />
      <Hello name="Clement" />
      <Hello name="Myles" />
      <Hello />
      
    </>
  );
}

function Hello({name = 'User'}) {
  return <h1>Hello {name}</h1>
}

// Hello.defaultProps = {
//   name: 'User'
// }
```

Notes:
- Method #1: Adding as params to the function
- Method #2: Using .defaultProps

They work the exact same way!
- Recommendation: Method #1
    - it is much more common than using .defaultProps

#### Children

Next, let's add another component, which is a comment that takes in some props:

```js
export default function App() {
  return (
    <Comment username="Conner" time={(new Date()).toString()}>
      <h1>Hello World</h1>
      <p>This is a comment!</p>
    </Comment>
  );
}

function Comment({username, time, children}) {
  return (
    <section>
      <p>{username} commented at {time}</p>
      {children}
    </section>
  )
}
```

Notes:
- `children` is the actual contents of the comment
    - It defaults to whatever is between opening/closing tags of `Comment`

More Notes:
- You do not need to use the Fragment braces because you are returning 1 Comment
- Concept of having components inside of components: component composition!
- Any of these custom components you make, only the actual DOM elements get added to the page 
    - Browser has no clue what a comment is, it only sees section/paragraph/children
    - Inspect > Elements, you will not see `Comment`, you just see the HTML elements
        - There may be a lot of nesting, but it eventually gets to HTML!


#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 4 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 5: Event-Driven Programming

Old adage "better to be proactive than reactive" does NOT apply here!

### Key Term

#### SyntheticEvent

The object type passed to React event handler functions.
- Generally: Work the same as native events
    - Has more consistency across browsers, though

Learn more: https://react.dev/reference/react-dom/components/common#react-event-object

### Notes from the video

#### Setup

```js
// App.js
export default function App() {
  return (
    <button>Click Me</button>
  )
}

```

```sh
cd test-app

npm start
```

Next, head to Inspect > Console.

#### Event-Driven Programming

Specifically: Event-Driven Programming in React
- Remember: React code compiles down to JavaScript, so if you know how that works, you should understand most

What we will learn: Differences between Vanilla JS and React's Event-Driven Programming

Vanilla JS: addEventListener()
- not the React way to do things

React: Use JSX

General rule: With React, use JSX whenever possible!
- Avoid regular DOM manipulation
    - Use attributes/props

Try running this code and clicking the button to see an output in the console:

```js
export default function App() {
  return (
    <button onClick={() => {
      console.log('clicked');
    }}>Click Me</button>
  )
}

```

You can also create a named function instead:

```js
export default function App() {
  const handleClick = () => {
    console.log('clicked');
  };

  return (
    <button onClick={handleClick}>Click Me</button>
  )
}

```

Notes:
- Because we have handleClick inside the App component, that means we make a new handleClick every time the app renders
    - This is not good!

Moving it to the bottom is more typical:

```js
export default function App() {
  return (
    <button onClick={handleClick}>Click Me</button>
  )
}

function handleClick() {
  console.log('clicked');
};
```

Note: Standalone function keyword is preferred over the arrow function syntax (when outside of function)
- Avoids problems with 'hoisting'

#### Synthetic Events

Event Handlers in React: Works the same as standard JS!
- Take event as parameter
- Pass event to console

```js
export default function App() {
  return (
    <button onClick={handleClick}>Click Me</button>
  )
}

function handleClick(event) {
  console.log(event);
};
```

What is this? A synthetic based event.

Synthetic event: Object type passed to event handler functions
- Works same as standard event most of the time
    - Pros: Adds consistency across browsers

Note: Idk why you would need it, but if you wanted to use native event, you culd use event.nativeEvent


#### Adding Event Listeners

Next, what happens if we try to add a click event or any event to a custom component?

Remember: Browser controls event listeners
- Problem: Browser does NOT know about the custom components (since they end up just being standard DOM elements ie. HTML...)

Let's create another component to help explain:

What this custom component does:
- Adds style to the buttons (replaces native elements)

```js
// App.js
export default function App() {
  return (
    <MyButton onClick={handleClick}>Click Me</MyButton>
  );
}

function handleClick(event) {
  console.log(event);
};

function MyButton(props) {
  // make sure to add onClick={props.onClick}, or else the console won't log the event!
  // even better: use the spread syntax (...props) so that it inherits more than just onClick!
  return (
    <button
      {...props}
      style={{
        color: 'red'
      }}>
      {props.children}
    </button>
  );
}

```

Now, the custom button works like a regular button.

Notes:
- We don't need to have {props.children} if we already have {...props} at the top of the button.
- If we want, we can make the button a self closing tag.

#### Takeaways

Event Driven Programming is very similar in Vanilla JS as it is in React!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 5 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 6: State

In React: State is how you store stuff (that's pretty much it - very useful!)

### Key Terms

#### State

Data specific to an instance of a component that persists between renders and causes re-renders when changed.
- "State, a component's memory"

Learn more: https://react.dev/learn/state-a-components-memory

#### Hook

A JavaScript function used to "hook" into React features such as state and the larger component lifecycle. The names of hooks always begin with *use*, and they cannot be called conditionally.

#### useState

A React hook for creating useful stateful components.
- The `useState` function takes in an initial state value (or a function that returns that initial value), and it returns an array with 2 elements:
    - current state value
    - setter function

For example:

```js
const [number, setNumber] = useState(42);
```

Learn more: https://react.dev/reference/react/useState

#### useReducer

An alternative React hook for creating stateful components
- Oftentimes: Used for more complex state

The `useReducer` function:
- takes in a reducer function and the initial state
- returns an array with 2 elements:
    - current state value
    - dispatch function

The reducer function takes in the previous state and an action object as parameters, then it returns the new state.
- Usually: the action object will have a `type` property, which will be used in a switch statement.

For example:

```js
function reducer(state, action) {
    swtich (action.type) {
        case 'increment':
            return {count: state.count + action.num};
        case 'decrement':
            return {count: state.count - action.num};
        default:
            throw new Error('Unknown action type');
    }
}
```

The dispatch function will then take in an object, which will be passed as the action to the reducer function.

For example:

```js
const [state, dispatch] = useReducer(reducer, {
    count: 0
});

return (
    <button onClick={() => dispatch({
        type: 'increment',
        num: 1
    })}>Increment</button>
);
```

Learn more: https://react.dev/reference/react/useReducer

#### Lifting State Up

A common React pattern of moving shared state up to the lowest common ancestor component in the tree.
- This allows for a single component to keep track of the state and pass the current value and setter function down through props.

Learn more: https://react.dev/learn/sharing-state-between-components#lifting-state-up-by-example

#### Controlled Component

A pattern of using React state to control the current state of an input, rather than allowing the native elements to control their own state (known as *uncontrolled component*).

For example: An input can be controlled via the `value` and `onChange` props:

```js
const [value, setValue] = useState('');
return <input value={value} onChange={e => setValue(e.target.value)} />;
```

Note: In React, the `onChange` works the same as `onInput`

Learn more: https://react.dev/learn/sharing-state-between-components#controlled-and-uncontrolled-components

### Notes from the video

#### Setup

Update App.js to have some code that does not work.
- This code will help us understand why we need state

```js
export default function App() {
  let count = 0;
  return (
    <>
      <button onClick={() => count++}>
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Start it up in Chrome:

```sh
cd test-app

npm start
```

The fact that this does not work right away, is going to show us WHY we need state! 

#### useState

Why doesn't anything happen when you click 'increment'?
- Good: The variable count IS incrementing by 1
- Bad: Nothing has told React to update the DOM
    - React is not fully reactive
    - We must tell it that something important happened that deserves a re-render

How to do this: State!
- Local to single instance of a component
- Is a value, like a variable
- Has a setter function
    - If setter function is called to change the state value, that instance of the component will render again (to update the component)

Let's see it in action!

```js
// not a default export, so use curly braces when importing!
import { useState } from "react";

export default function App() {
  const [count, setCount ] = useState(0);
  
  // let count = 0;
  return (
    <>
      <button onClick={() => setCount(count + 1)}>
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Notes:
- useState is a function
    - takes in default value (0)
    - need to de-structure the return value (an array)
        - count
            - you never want to change a state variable ie. count++
        - setter Function (setCount)
            - you will use this to change the count ie. setCount(count + 1)

- useState() is a hook, ie. it is special and hooks into react features
    - anything that starts with 'use' is a hook
    - we will look at hooks more later in the course
        - idea: return value from useState has ability to cause the component to re-render

Note: He used auto import, which I learned more about here (for which Extensions I should have in VSCode):
- [Link to StackOverflow](https://stackoverflow.com/questions/38210604/visual-studio-code-automatic-imports/53015835#53015835)

Next, learn 1 rule about hooks: Cannot be called conditionally!

Example:

```js
if (true) {
    const [count, setCount ] = useState(0);
}
```

Why this is an issue:
- React Hooks must be called in the same exact order in every component render
    - Internally, React depends on the ordering of the Hook Functions

#### useState Function Parameters

useState: Does not have to take in a value, can take in a function!

Example, which does the same as above:

```js
export default function App() {
  const [count, setCount ] = useState(() => {
    return 0;
  });
...
}
```

Purpose of this:
- If you have a complex computation (for how to determine initial state), it should be inside of a function
    - When JS renders, if an input for a function is a complicated function, then we need to wait for the complicated function EVERY time

This would be some mock code for that problem:

```js
const [count, setCount ] = useState(somethingComplicated());
```

Notes:
- If you have anything complicated, wrap it in a function
    - Value being passed to useState is now a function itself
        - JS doesn't need to execute the function before using useState

Now, it is pretty rare having to pass in a function to useState, so let's put the code back to having a default value of 0:

```js
export default function App() {
  const [count, setCount ] = useState(0);
...
}
```

#### Adding Multiple State Variables

Next, you must know that we can have multiple pieces of state, with 1 component
- All you have to do is multiple calls to useState()

For example:

```js
// not a default export, so use curly braces when importing!
import { useState } from "react";

export default function App() {
  const [count, setCount ] = useState(0);
  const [otherCount, setOtherCount ] = useState(50);
  
  return (
    <>
      <button onClick={() => setCount(count + 1)}>
          Increment
      </button>
      <p>Count: {count}</p>
      <button onClick={() => setOtherCount(otherCount + 10)}>
          Increment
      </button>
      <p>otherCount: {otherCount}</p>
    </>
  );
}

```

Notes:
- These are completely separate pieces of state
    - count: starts at 0, ++1
    - otherCount: starts at 50, ++10

Another fact about state is that it is specific to a single instance of a component.

Let's create another component to illustrate this idea:

```js
import { useState } from "react";

export default function App() {
  return (
    <>
      <Counter startingCount={0} />
      <Counter startingCount={100} />
    </>
  );
}

function Counter({startingCount = 0}) { // default value = 0
  const [count, setCount ] = useState(startingCount);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Notes:
- Both of the counters are on their own, separately both increment by 1
    - They are separate instances, w/ their own state
        - 1 starts at 0
        - 2 starts at 100

#### Setter Functions

1 thing about Setter Functions: They only update the state value once the component is able to re-render
- Until the call stack is empty, there is no re-render

This only increments by 1:

```js
<button onClick={() => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
}}>
    Increment
</button>
```

Another key point: Whenever you have multiple state values, they will be batched together
- 

Let's look at an example with setCount AND setOtherCount:

```js
<button onClick={() => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
    setOtherCount(otherCount + 1);
    
}}>
    Increment
</button>
```

All of the state values are updated, and then the re-render occurs.

If we want our setCount to use the value that was added before, we can pass in a function to setCount:

```js
<button onClick={() => {
    setCount(prevCount => prevCount + 1);
    setCount(prevCount => prevCount + 1);
    setCount(prevCount => prevCount + 1);
}}>
    Increment
</button>
```
Notes:
- While these setCount's are still run together, they are run in the order they are called (in a queue)
- When you call setCount with a function, it will take in the previous value from setCount
- Functions we are passing in are not relying on 'count' from the useState declaration

Let's put the function back to increment by 1 before moving on.

#### Object State

If we have a value of useState as an Object (or an Array, since it is an object), there are some special properties we need to be aware of!

Main thing: useState will not cause the component to re-render, unless you set the value of useState to another value
- You cannot change the values inside of the object itself
- You must set useState to a brand new object

For example, let's update this number:

```js
setCount({num: count.num + 1})
```

If we want to add a new property, we must create a new object, and spread the old object
- This is to 

```js
setCount({...count, otherCount: 0})
```

This creates a new object that has everything from count, in addition to new key-value pair of key=otherCount,value=0.

Since arrays are objects, the same holds true with Arrays:

```js
const [count, setCount ] = useState([1,2,3]);

setCount([...count, 4])
```

Let's reset back to startingCount = 0 before proceeding.

#### Lifting State Up

What if we wanted both counters to use the same state?
- Data/React moves in 1 direction, from parents down to children
    - The shared State needs to be high enough in the component tree that it can be sent down to the children we want it to.

How to do this?
- Move count, setCount into App()
    - Make sure to pass in count, setCount as params to function Counter() ie. Counter(){count, setCount}
- Updated App() so that when you call Counter in JSX, you are providing the required params

Let's see it in the code:

```js
import { useState } from "react";

export default function App() {
  const [count, setCount ] = useState(0);

  return (
    <>
      <Counter count={count} setCount={setCount} />
      <Counter count={count} setCount={setCount} />
    </>
  );
}

function Counter({count, setCount}) {
  return (
    <>
      <button onClick={() => setCount(count + 1)}>
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Now, if you click Increment, regardless of which one, both of the counts go up!

#### Controlled Components

What we want to show now: Controlled Components
- In a way, the counter is a controlled component
    - Uses setter as a prop
    - Uses whatever parent says as a method for what it does (when you click the button)

- Far more common usage of controlled components: Inputs!

Let's say we have another state, `value`, and let's add an input tag for this.
- We want our setter function called onChange

```js
import { useState } from "react";

export default function App() {
  const [count, setCount ] = useState(0);
  const [value, setValue ] = useState('');
  
  return (
    <>
      <input
        type="text"
        value={value}
        onChange={(event) => setValue(event.target.value)} />
      <Counter count={count} setCount={setCount} />
      <Counter count={count} setCount={setCount} />
    </>
  );
}

function Counter({count, setCount}) {
  return (
    <>
      <button onClick={() => setCount(count + 1)}>
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Now, the input element is controlled by the state.
- Whenever you type into the input box, it re-renders, the value changes, and we get the input of the new value.

Let's remove this input tag and the 2nd useState line before moving forward.

#### useReducer

Finally, an alternative to useState.
- Usually: useState
- Sometimes when it is more complex: useReducer

useReducer:
- Does not just take in state
    - Takes in a function (reducer)
    - Takes in state (as an object)
- Return value:
    - Does not return value/setter functions
    - Does return the current state object ie. state AND a dispatch function

Reducer function:
- input params:
    - previous state
    - action (an object)
- returns: new state
    - usually: the action object has `action.type`, which is used in a switch statement

Here is an implementation of useReducer and a reducer function:

```js
import { useReducer, useState } from "react";

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      //return {count: state.count + 1} 
      return {count: state.count + action.num}; // return an object with the new state
    case 'decrement':
      return {count: state.count - action.num};
    default:
      throw new Error('Unknown action type');
          
      
  }
}

export default function App() {
  const [state, dispatch ] = useReducer(reducer, {
    count: 0
  });
  
  return (
    <>
      <Counter
        count={state.count}
        onClick={() => dispatch({ // dispatch: calls the reducer (has to take in the reducer's action!)
          type: 'increment',
          num: 1 // increment by 1
        })} /> 

      <Counter
        count={state.count}
        onClick={() => dispatch({
          type: 'decrement',
          num: 100
        })} /> 
      
    </>
  );
}

function Counter({count, onClick}) { // change this to onClick
  return (
    <>
      <button onClick={onClick}> {/* change this to onClick */}
          Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Takeaways
- useReducer: Overkill
- useState: Pretty much always will do the trick!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 6 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 7: Component Lifecycle

Let's take a peek into the fascinating life of a React component!

### Key Terms

#### Component Lifecycle

The different stages that an instance of a component goes through. There are 3 primary stages to the React lifecycle:

1. Mounting: The component renders for the 1st time

2. Updating: The component re-renders whenever state changes OR the props are updated by the parent component.
- A component may updated many times without ever mounting again

3. Unmounting: The componenet is removed from the DOM. (Final stage of the lifecyce)
- Component cannot update again once it has been unmounted
    - A new instance of the component can still be mounted, though

#### useEffect

A React hook for performing side effects around the component lifecycle. The `useEffect` hook takes in a callback function and an optional dependency array.

Dependency array:
- no dependency array is provided: callback function runs on EVERY render.
- dependency array provided: callback function runs on *mount* OR when an item in that array has changed
    - note: Objects must be new objects to be considered to have changed
    - to avoid bugs related to effects using stale values from previous renders, the dependency array should contain all values that the callback uses, that could change between renders.

The callback function can also return a cleanup function, which will run on *unmount* and before the main effect function runs on any re-renders.

Example:

```js
useEffect(() => {
    console.log('count changed');

    return () => console.log('cleanup count changed effect');
}, [count]);
```

Learn more: https://react.dev/reference/react/useEffect

#### useLayoutEffect

A React hook for performing side effects around the component lifecycle in the same way as `useEffect`. 

The only difference between the two functions is that `useLayoutEffect` works synchronously
- What this means: The effects always finish running before the browser paints
- This hook should only be used for effects that will make visual changes to the DOM
    - Otherwise: The synchronous nature will give worse performance than `useEffect`, without any benefits!

Learn more: https://react.dev/reference/react/useLayoutEffect

### Notes from the video

#### Setup

Create Counter.js and write some code:

```sh
cd test-app
cd src
echo > Counter.js
```

```js
// Counter.js
import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    const [bool, setBool] = useState(false);

    return (
        <div className='counter'>
            <button onClick={() => setBool(!bool)}>Re-Render</button>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <p>Count: {count}</p>
        </div>
    );
}
```

Update App.js:

```js
// App.js

```

View in Google Chrome:

```sh
cd test-app

npm start
```

What is going on in this App:
- State for isShown that defaults to true
- Button that toggles isShown from true/false
    - true: button says 'Hide Counter'
    - false: button says 'Show Counter'
        - Counter is either hidden or shown based on the isShown state

- Counter component from Counter.js
    - button 1: re-render (toggles the boolean state)
    - button 2: increment: works like a normal counter

Notes:
- The count resets when you hit 'show counter', because it is making a new counter.
- Re-Render currently does nothing
    - Changed values are not being displayed

#### Component Lifecycle

Idea of Component Lifecycle: The different stages a component can be in!

1. Mount / initial render: Component is added to screen for the first time
- Clicking 'Show Counter'

2. Updates / re-render: Whenever the state or props value is changing, it needs to update (Change values + update DOM)
- Clicking 'Increment'
- Clicking 'Re-Render'

3. Unmount / leave the screen: Component is being deleted 
- Clicking 'Hide Counter'


#### useEffect

Sometimes, we have to hook into a component lifecycle to do something. That is when useEffect comes in.

useEffect: 

```js
import { useState, useEffect } from 'react';
...
    const [count, setCount] = useState(0);
    const [bool, setBool] = useState(false);

    useEffect(() => {
        console.log('render');
    });
```

Notes on useEffect:
- useEffect runs after every render
    - YES: mount
    - YES: re-render
    - NO: unmounted

- Input: Usually use arrow functions
    - Can use regular/any function too
    - Just cannot use async functions

#### Dependency Array

Now, we only want to call this for certain renders. Let's add another useEffect() to help explain this:

```js
// Counter.js
import { useState, useEffect } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    const [bool, setBool] = useState(false);

    useEffect(() => {
        console.log('render');
    });

    useEffect(() => {
        console.log('pressed re-render');
    }, [bool]);

    useEffect(() => {
        console.log('mounted');
    }, []);

    return (
        <div className='counter'>
            <button onClick={() => setBool(!bool)}>Re-Render</button>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <p>Count: {count}</p>
        </div>
    );
}

```

Notes:
- You can (and usually will) have 2+ useEffect
    - They run in order

- 2nd argument of useEffect: Dependency array
    - Anything in this array determines when the effect will run
        - default: runs everytime
        - with dependency array: only run if an element changes!
            - empty array: only runs on mount

#### Cleanup Functions

Next, these effects can also return a 'cleanup' function.

Cleanup Functions: 
- Used to cleanup code from previous effect

In action:

```js
import { useState, useEffect } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    const [bool, setBool] = useState(false);

    useEffect(() => {
        console.log('count changed');

        return () => console.log('cleanup count changed');
    }, [count]);

    useEffect(() => {
        console.log('render');
    });

    return (
        <div className='counter'>
            <button onClick={() => setBool(!bool)}>Re-Render</button>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <p>Count: {count}</p>
        </div>
    );
}
```

Notes:
- Pressing 'Hide Counter' does the following:
    - print 'cleanup count change' (count changes)

- Pressing 'Increment' does the following:
    - print 'cleanup count change' (count changes)
    - print 'count changed' (count changes)
    - print 'render' (that useEffect has no dependency array, so it runs everytime!)


#### Avoiding Infinite Loops

One last thing with useEffect: Infinite Loops (Common error)

Let's look at this chunk of code:

```js
useEffect(() => {
    setCount(count + 1);
}, [count]);
```

What happens/Why this is bad:
- Count is in the dependency array
    - So: When count changes, useEffect needs to run
        - Then: This cause useEffect to run again, and again, and again

#### useLayoutEffect

Next, let's look at an example:

```js
import { useState, useEffect } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    const [bool, setBool] = useState(false);

    useEffect(() => {
        if (count === 3) {
            setCount(4);
        }
    }, [count]);

    useEffect(() => {
        console.log('render');
    });

    const startTime = new Date();
    while (new Date() - startTime < 100) {} // This does some stalling to help see what's going on on the screen

    return (
        <div className='counter'>
            <button onClick={() => setBool(!bool)}>Re-Render</button>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <p>Count: {count}</p>
        </div>
    );
}
```

useEffect: Runs asynchronously, after the render, and after being painted to the screen
- This causes the 3 to appear on the screen for a moment, and then become 4 after
    - This is not ideal, as we don't want 3 to show on the screen at all!
        - Most of the time, this does not matter, but there is a remedy...

useLayoutEffect: Runs synchronously AFTER the render, but BEFORE the painting to the screen
- This will allow the 3 to not appear on screen at all

Change this code to see it in action:

```js
import { useState, useEffect, useLayoutEffect } from 'react';
    ...
    useLayoutEffect(() => {
        if (count === 3) {
            setCount(4);
        }
    }, [count]);
```

What happens now:
- We get 1, 2, 4
    - When count is set to 3, we don't get it painted to the screen

Word of advice: Avoid using useLayoutEffect!
- Its synchronous nature can cause things to run slowly

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 7 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 8: Refs

In React, refs are special things to store special stuff.
- Easy
- Very useful!

### Key Terms

#### Ref

A React value specific to an instance of a component that persists between renders, but updating the value does not cause a re-render (unlike state)
- Oftentimes: Used to reference the DOM node associated with the component
    - Can be achieved with the attribute `ref`

Learn more: https://react.dev/learn/referencing-values-with-refs

#### useRef

A React hook for creating a ref.
- Input: Initial value
- Return: a ref

The ref is simply an object with a `current` property set to the current value:

```js
const div = useRef(null);
return <div ref={div}>This div has a ref</div>;
```

Learn more: https://react.dev/reference/react/useRef

#### React.forwardRef

A function used by a custom component to forward a ref attribute on to a child element.
- higher-order component: Which means, it takes in a component and returns a new one
    - input: component
    - return: component

- In this case: Takes a component that has a 2nd parameter for the ref

Example:

```js
function Parent() {
    const ref = useRef(null);
    return <Child ref={ref}>This child has a ref</Child>;
}

const child = forwardRef(function (props, ref) {
    return <div ref={ref}>{props.children}</div>;
});
```

Learn more: https://react.dev/reference/react/forwardRef

### Notes from the video

#### Setup

Update App.js to look like this:

```js
// App.js
import { useState } from "react";

export default function App() {
  const [seconds, setSeconds] = useState(0);

  const startTimer = () => {
    setInterval(() => {
      setSeconds(currSeconds => currSeconds + 1);
    }, 1000);
  };

  const stopTimer = () => {
    //
  };

  return (
    <>
      <button onClick={startTimer}>Start</button>
      <button onClick={stopTimer}>Stop</button>
      <p>seconds: {seconds}</p>
    </>
  );
}

```

What this is:
- State initialized to 0
    - seconds
    - setter: setSeconds

- startTimer function: starts an interval, updates the seconds variable
    - we use `setSeconds(currSeconds => currSeconds + 1);` to avoid any stale values

- stopTimer function: has not been implemented yet...

- return value: 2 buttons
    - start button
    - stop button
        - also, a paragraph to tell how many seconds have passed

Run in Chrome:

```sh
cd test-app

npm start
```

Open up the Console so we can view logging via Chrome > Inspect > Console.

#### useRef

Let's start writing the functionality for stopTimer:

```js
export default function App() {
  const [seconds, setSeconds] = useState(0);
  const [timerID, setTimerID] = useState(null);

  const startTimer = () => {
    setTimerID(setInterval(() => {
      setSeconds(currSeconds => currSeconds + 1);
    }, 1000));
  };

  const stopTimer = () => {
    clearInterval(timerID);
  };
```

What we did here:
- use clearInterval to Stop the interval
- Set timer ID (using state)
    - If we want a value to persist across renders, we must use state!
    - When we tried doing this with let timerID = 0, when we click startTimer, we lose access to timerID because it becomes null

Note: This is still sub-optimal, every time we start the interval, we call setTimerID (we don't need to re-render, so it is unnecessary)
- Only 1 render so not a big issue, but in other cases this could cause an infinite loop

How do we solve this so that updating timerID does not cause a re-render?

Answer: Make the state variable an object (instead of null!)
- Using an object with `current: null` will allow the App to function how we expect
- Why does this work:
    - We are no longer calling setTimerID (which causes a re-render...)
    - We are simply accessing/changing a value in the object
        - obj.current

```js
import { useState } from "react";

export default function App() {
  const [seconds, setSeconds] = useState(0);
  const [timerID, setTimerID] = useState({
    current: null,
  });

  const startTimer = () => {
    timerID.current = setInterval(() => {
      setSeconds(currSeconds => currSeconds + 1);
    }, 1000);
  };

  const stopTimer = () => {
    clearInterval(timerID.current);
  };

  return (
    <>
      <button onClick={startTimer}>Start</button>
      <button onClick={stopTimer}>Stop</button>
      <p>seconds: {seconds}</p>
    </>
  );
}

```
    
Notes
- Not the cleanest code, we are kind of hacking
    - not using setTimerID function (we get a warning "'setTimerID' is assigned a value but never used")
    - not using the state variable

Lucky for us: React has something built in to fix this! The ref.

```js
// App.js (line 5)

// old
const [timerID, setTimerID] = useState({
    current: null,
  });

// new
import { useState, useRef } from "react"; // import 
...
const timerID = useRef(null); // line 5
```

Notes:
- This works that same as useState with an object.current
    - It does not return a value with array and setter function, but just the timerID value!

- While refs have specific functionality, they are basically just syntactic sugar around passing a value to state, when you don't need the setter function
    - Value persists across renders
    - Changing the value never causes a re-render!

#### ref Attribute

Common use case of Ref: 

Start by putting the code in this state:

```js
import { useState, useRef } from "react";

export default function App() {
  const inputRef = useRef(null);
  console.log("Before render: " + inputRef); // null

  const focusInput = () => {
    inputRef.current.focus();
  };
  
  return (
    <>
      <input ref={inputRef}/>
      <button onClick={focusInput}>Focus</button>
    </>
  );
}

```

What we did:
- Return value: Input, button
- Goal: Input box w/ a button that has you 'focus' on the input text

Notes:
- We need the actual input from the DOM for `focusInput` in order to make it focus, so we used the React way of using JSX and useRef()
    - Created inputRef
    - In the JSX/return area, set the input's ref to be inputRef
    - Edited focusInput() so that it makes inputRef.current to .focus()

One key point: At the top of the function (before the DOM node is created), the inputRef is still null
- Point: cannot use inputRef until the first render completes!

#### forwardRef

Key point: Ref attributes can only be added to DOM nodes
- Cannot be added to custom components

This will give an error of "Warning: Function components cannot be given refs. Attempts to access this ref will fail. Did you mean to use React.forwardRef()?" AND "Uncaught TypeError: Cannot read properties of null (reading 'focus')":

```js
...
  return (
    <>
      <MyInput ref={inputRef}/>
      <button onClick={focusInput}>Focus</button>
    </>
  );
}

function MyInput(props) {
  return <input {...props} style={{color: 'red'}} />
}
```

But, there is a work-around/way to do this...

How to hack and add to custom components - forwardRef!

```js
const MyInput = forwardRef(function (props, ref) {
  return <input ref={ref} {...props} style={{color: 'red'}} />
});
```

You should now see your input with the custom color of red.

What we did here:
- Wrap entire functional component in a forwardRef
    - Remove name 'MyInput' from function
    - Save the forward ref as const 'MyInput'
    - Add `ref` as 2nd parameter
    - Use the ref (Tell the return value which DOM element is going to use the Ref)
        - ie. `<input ref={ref} ... >`

Note:

Idea: We are using an input that is not controlled by any state (using refs instead via `inputRef.current.value`) is known as an uncontrolled component
- Most of the time: Don't want to do this
    - Using a controlled component with state is best, typically

- For times we do want an uncontrolled component OR we want a Ref on a controlled component:
    - Use state for the value
    - Have values of un-controlled by using Ref

#### Callback Refs

To this point: We have created refs with `useRef`.

But, what if we want to use the ref callback to store a reference to a DOM node in an instance property:

```js
export default function App() {
  return (
    <>
      <MyInput ref={handleRef}/>
      {/* <button onClick={focusInput}>Focus</button> */}
    </>
  );
}

function handleRef(domNode) {
  console.log(domNode);
}
```

What we did here:
- handleRef(): Runs on mount and un-mount (not on all re-renders)
    - takes in: DOM node
    - gives back: 
        - when it runs on mount: domNode
        - when it runs on re-render: nothing at all
        - when it runs on unmount: null

Note: We don't use this very much!
- useRef hook does the job for most, such as:
    - focusing hooks
    - keeping track of a persistent value that we want to change, without re-rendering

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 8 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 9: Imperative React

This is where React starts to get a bit complicated. You've been warned...

### Key Term

#### useImperativeHandle

A React hook for customizing the value provided to a parent component when using a ref.

useImperativeHandle hook:
- Takes in a ref as 1st parameter
- Takes in a callback function
- Optional: Dependency array

The return value of the callback function will act as the `current` value of the ref.
- If any item in the dependency array changes between renders, the callback function will be invoked again to recalculate the `current` value

Since `useImperativeHandle` requires a ref on custom component, it should always be used with `React.forwardRef`.

For example:

```js
forwardRef(function (props, ref)) {
    const [count, setCount] = useState(0);

    useImperativeHandle(ref, () => {
        return {
            resetCount: () => setCount(0)
        };
    });

    return (
        <button onClick={() => setCount(count + 1)}>
            Increment
        </button>
    );
}
```

### Notes from the video

#### Setup

Current state of App.js:

```js
// App.js
import Counter from './Counter';
import CustomInput from './CustomInput';
import './App.css';

export default function App() {
  return (
    <>
      <Counter />
      <CustomInput placeholder="Type something..." />
      <button>
        Reset
      </button>
    </>
  );
}

```

Counter.js:

```js
// Counter.js
import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
            <p>Count: {count}</p>
        </>
    );
};

```

Finally, CustomInput.js:

```js
// CustomInput.js
import { useState } from 'react';

export default function CustomInput(props) {
    const [value, setValue] = useState('');

    return (
        <input
            {...props}
            value={value}
            onChange={event => setValue(event.target.value)}
            style={{color: 'red'}} />
    );
};

```

Goal here: Add clickEventHanldler to the reset button, that will reset 2 things:
- count
- text in custom input

Run in Google Chrome:

```sh
npm start
```

Right click > Inspect > Console.

#### Coding

What we know: React is a declarative library
- Sometimes: We want to use our components in an imperative way

Note: declarative vs. imperative
- declarative: specifying the result you want
- imperative: writing explicit sequence of commands


So, back to the example, let's think, how do we get the 'Reset' button to reset both of the components??
- Method 1: We can lift the state up
    - This would work, but separates the state from components they are related to
        - Does not make sense to have them higher up
            - In more complicated examples, this can cause app component to balloon out of control

- Method 2: Add a clickEventHandler to the buttons (We want an imperative way to control these components)
    - What we want this function to do:
        - RESET counter
        - RESET custom input
            - We cannot just do it like this currently, so we must do it another way

- Method 3: Use a Ref to reference the counter and custom input
    - 

```js
// import Ref
import { useRef } from 'react';

// add to App
const counterRef = useRef();
const customInputRef = useRef();

// add to JSX
...
<Counter ref={counterRef} />
<CustomInput ref={customInputRef} placeholder="Type something..." />

```

After this, we are sure to be able to come into this button and use onClick to reset both. No? Why is that?
- When we use a Ref, the current value is set equal to a DOM node
    - DOM nodes know nothing about React state
        - React state is handled by React...

What do we need to do, then?
- Go into Counter AND CustomInput components
    - control what values they pass to their parent as a ref

Steps to doing this:
1. Add a forwardRef
- Since it is a custom component, we need to use forwardRef
- Make sure to import forwardRef from 'react'
- Make sure the component takes in `props` and `ref`
- use another hook known as `useImperativeHandle()` from 'react'
    - inputs:
        - ref: 
        - function: 
    - outputs: object
        - object (returned from function, it is the current value of the ref)
            - key: .reset
            - value: function that will setCount(0)
    
Notes:
- Not going to pass ref to the button (or another element) - We don't want the ref to be equal to a DOM node, so
- If we only wanted to calculate return value on mount, we can add an empty dependency array, or could add something like [count]
    - Most of the time you don't add a dependency array

2. 

Let's head into these files and make the changes:

```js
// Counter.js
import { useState, forwardRef, useImperativeHandle } from 'react';

export default forwardRef(function Counter(props, ref) {
    const [count, setCount] = useState(0);

    useImperativeHandle(ref, () => {
        return {
            reset: () => setCount(0)
        };
    });

    return (
        <>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
            <p>Count: {count}</p>
        </>
    );
});
```

```js
// CustomInput.js
import { useState, forwardRef, useImperativeHandle } from 'react';

export default forwardRef(function CustomInput(props, ref) {
    const [value, setValue] = useState('');

    useImperativeHandle(ref, () => {
        return {
            reset: () => setValue('')
        };
    });

    return (
        <input
            {...props}
            value={value}
            onChange={event => setValue(event.target.value)}
            style={{color: 'red'}} />
    );
});

```

Finally, head back over to App.js and make the button's onClick call 2 things:
- counterRef.current.reset();
- customInputRef.current.reset();

```js
// App.js
<button onClick={() => {
    counterRef.current.reset(); // new
    customInputRef.current.reset(); // new 
}}>
    Reset
</button>

```

You can now head over to the browser, type into the customInput, increment the count, and when you press reset, everything goes back to the initial state!!

Takeaways:
- useImperativeHandle(): A hook that lets us use the componenet we have refs to, in an imperative way
    - We are calling some function from the components
    - Can also access any data that we pass up to the ref

- Use this with caution! ("escape hatch")
    - It is good to know about and can be helpful, but...
    - If you use it too much, that is not good because you take away from React's declarative nature!
        - Your code will get hard to read

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 9 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 10: Contexts

Just as context is important in real life, so too is it important in a React codebase!

### Key Terms

#### Context

A way to pass values down a component tree without needing to pass props through all of the components (this is known as prop drilling)
- Contexts are generally useful for global state, needed throughout an application/page
    - It would be very inconvenient to have to pass props to every element on the page...

Learn more: https://react.dev/learn/passing-data-deeply-with-context

#### React.createContext

A react function for creating a context object.
- Takes in: Default value, which is used if there is not a matching context provider in a tree

For example, this would create a context that could be used to keep track of a user's selected theme:

```js
const ThemeContext = createContext({
    mode: 'dark'
});
```

This context would then have a .provider component, which must be above any components in the tree that wish to use the context. The `value` prop will be passed as the value to all children using the context. For example:

```js
return (
    <ThemeContext.Provider value={{mode: 'dark'}}>
        {props.children}
    </ThemeContext.Provider>
);
```

Learn more: https://react.dev/reference/react/createContext

#### useContext

A React hook for using a context.
- Takes in: A context object (created with `createContext()`)
- Returns: The value from the first context provider of that context above it in the tree

For example:

```js
const theme = useContext(ThemeContext);
console.log(theme.mode); // 'dark'
```

Learn more: https://react.dev/reference/react/useContext

### Notes from the video

#### Setup

We have 5 JavaScript files this time around, so buckle up...

```sh
cd test-app
cd src

echo > App.js
echo > Profile.js
echo > WelcomeBanner.js
echo > Course.js
echo > UserContext.js 
```

```js
// App.js
import { useState } from 'react';
import Profile from './Profile';

const conner = {
  name: 'Conner',
  course: 'FrontendExpert', 
};

const clement = {
  name: 'Clement',
  course: 'AlgoExpert', 
};

export default function App() {
  const [user, setUser] = useState(conner); // default state: user = conner

  const toggleUser = () => {
    if (user === conner) {
      setUser(clement);
    } else {
      setUser(conner);
    }
  }

  return (
    <main>
      <Profile user={user} />
      <button onClick={toggleUser}>Toggle User</button>
    </main>
  );
}

```

```js
// Profile.js
import WelcomeBanner from './WelcomeBanner';
import Course from './Course';

export default function Profile({user}) {
    return (
        <>
            <WelcomeBanner user={user} />
            <Course user={user} />
            
        </>
    );
}

```

```js
// WelcomeBanner.js
export default function WelcomeBanner({user}) {
    return <h1>Hello {user.name}</h1>
}
```

```js
// Course.js
export default function Course({user}) {
    return <p>Your course is {user.course}</p>
}
```

```js
// UserContext.js

// empty for now, since the example works without it right now!

```

Run the App in Chrome:

```sh
npm start
```

What you should see:
- Hello 'name'
- Your course is 'course'

#### Prop Drilling

Context = Another form of state in React

Looking at App.js, we can see why it could be useful:
- State for a user
    - toggleUser: will be used to toggle between Conner/Clement

- Return value: Main tag
    - profile: takes in user as a prop
    - button: toggles the user

What this current state is known as:
- Lifting state up
    - State was lifted to App.js component (that is the lowest level component that has all of the components needing state, as its children)
- Prop drilling
    - Sending that state (or some prop) deeply down a React tree

This is fine, but in a more complex situation with more components, passing around props like that is not great!

This is where Context comes in.

#### Context

Context: Allows you to create some state that is accessible by all children (of a component)

Let's edit UserContext.js and create our first context:

```js
// UserContext.js
import { createContext } from "react"

export const UserContext = createContext({
    name: null, // default values
    course: null,
}); 

```

We have created a userContext with default values of null.

Head back over to App.js and implement the UserContext:
- Remember: Context works by sending some state down to all of the children

What to do:
- Import the context we just created
- Edit the return value to use UserContext as a JSX element
    - specifically: UserContext.Provider
        - creates state, sends the state down to all the children
            - only the pieces that actually need access to the actual user
                - ie. Profile, since it needs the `user={user}`

Note: Make sure to add `value={user}` in the UserContext.Provider
- This makes it so that anything inside of the UserContext has access to the user object
    - We no longer even need to pass it as a prop to Profile now!

```js
// App.js
import { UserContext } from './UserContext';
...
  return (
    <main>
      <UserContext.Provider value={user}>
        <Profile />
      </UserContext.Provider>
      <button onClick={toggleUser}>Toggle User</button>
    </main>
  );

```

#### useContext

Now, it does not work yet, because we have to go into the individual components and have them use the Context instead of using the prop.

Let's do that now:
- delete the prop from function inputs
- make a call to useContext hook function

```js
// Profile.js
import WelcomeBanner from './WelcomeBanner';
import Course from './Course';
import { useContext } from 'react';
import { UserContext } from './UserContext';

export default function Profile() {
    const user = useContext(UserContext);
    return (
        <>
            <WelcomeBanner user={user} />
            <Course user={user} /> 
        </>
    );
}

```

To explain this again:
- Profile gets the user from the UserContext
    - useContext looks for the 1st instance of a context provider of this type in the tree above it, ie. 
        - once we get the value from that state, we can use it just as if it was a prop

Once you save your files, go back to your App in Chrome.

Everything should be working again!

Now, we are still using props in the WelcomeBanner.js and Course.js files, so let's fix that:

```js
// Profile.js

import WelcomeBanner from './WelcomeBanner';
import Course from './Course';

export default function Profile() {
    return (
        <>
            <WelcomeBanner />
            <Course /> 
        </>
    );
}

```

```js
// WelcomeBanner.js
import { useContext } from 'react';
import { UserContext } from './UserContext';

export default function WelcomeBanner() {
    const user = useContext(UserContext);
    return <h1>Hello {user.name}</h1>
}
```

```js
// Course.js
import { useContext } from 'react';
import { UserContext } from './UserContext';

export default function Course() {
    const user = useContext(UserContext);
    return <p>Your course is {user.course}</p>
}
```

Once again, everything is working as before!

What we did for each (WelcomeBanner.js / Course.js):
- Add imports
- Remove prop from function input
- Add user = useContext(UserContext) to the function

Important Note: Profile.js, an intermediary component, does not even know that the Context exists
- Because it doesn't need to know, they don't need to be passing props down
    - Good: bc no prop drilling + more simple components overall

This is why Contexts are so powerful!!!

#### Custom Provider Components

Next goal: move some of this logic that is connected to the Context, into context itself!

What we are going to do:
- Move the objects into the Context
    - conner
    - clement
- Move the function(s) into the Context
    - toggleUser()

Let's move these into the UserContext!

Step 1: Create a UserContextProvider in UserContext.js
- Contains all extra logic (keep it all in one place)
- Input: {children}
- Output: UserContext.Provider with {children}

Step 2: Move the objects/function from App.js into UserContext.js
- Objects: clement/conner
- Function: toggleUser

Step 3: Add toggleUser() to the `value={}` of the UserContext.Provider in UserContext.js
- We need a way to call toggleUser() when the button is clicked on

Step 4: Go into App.js and replace UserContext.Provider with UserContextProvider
- This is our custom component, so make sure to import it from ./UserContext
- Another note: remove the value={user}, that is taken care of in UserContext.js

Step 5: Create a helper function in App.js
- What this helps with: It is a component to hold the children (just so we can use the ContextProvider)
- We need a way to allow the button in App.js to access toggleUser()
    - We de-construct and grag toggleUser() from useContext(UserContext)

Note: We cannot call useContext inside of App.js
- The ContextProvider is inside of App.js children, and it would need to be a parent!

Step 6: In App.js, edit the return value for the JSX
- use AppInteral instead of Profile
- You can also remove the button (it is in AppInteral already!)

Step 7: Go to the components that are using the context (WelcomeBanner.js/Course.js) and get the user from that object that is being returned
- De-construct user via `const { user } = useContext(UserContext);`

Step 8: In UserContext.js, make a couple last changes
- import useState
- update the default values to be the same shape
    - toggleUser: null
    - user: object
        - key: name
        - key: course

Note: This doesn't matter much, but it is good practice to update the created UserContext's default values

#### Takeaways

Context: Creates some state that can be accessible by all children of the context provider
- works just like state
    - when the value changes, the components will re-render (giving same effect as state) without using prop drilling to send values throughout children

This makes for much easier to read code!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 10 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 11: Component Lists

Welcome to lists in React! Where this:

```js
<li>1</li>
<li>2</li>
<li>3</li>
```

Turns into this:

```js
<>{[1,2,3].map(num => <li key={num}>{num}</li>)}</>
```

### Key Term

#### Kep Prop

A prop passed to each element in a list to help React keep track of those elements.
- Should be unique identifiers

By passing key props, if the list changes, React can easily know which elements need to be mounted/updated/un-mounted.

For example, when rendering an array of messages from the server, message IDs could be used as a key prop:

```js
return (
    {
        messages.map(message => {
            return <p key = {message.id}>{message.text}</p>;
        });
    }
);
```

Learn more: https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key

### Notes from the video

#### Setup

```js
// App.js
import { useState } from 'react';

export default function App() {
  const [items, setItems] = useState([]);
  const [newItem, setNewItem] = useState('');
  
  return (
    <>
      <ul>
        {/* { TO DO} */}
      </ul>

      <input
        type="text"
        value={newItem}
        onChange={(event) => setNewItem(event.target.value)}/>

      <button onClick={() => {
        setItems([...items, newItem]);
        setNewItem('');
      }}>
        Add List Item
      </button>
    </>
  );
}

```

View in the Browser:

```sh
npm start
```

View the Console via Chrome Right click > Inspect > Console.

#### Rendering Lists

How can we take an array of data, and turn it into a list of JSX elements that can be added to the DOM?

What we have right now:
- 2 items of state
    - items: default of empty array
    - newItem: default of empty string

- return value
    - unordered list
    - input value (input a new list item ie. newItem)
    - button (saves whatever you put in the input, into the items state array)

Goal: Create a list item for each item in the array

How to do this: 1 nice feature of React is that inside of a JSX return value, you can have an array of elements, that all get added to the screen 
- You need to add a "key" prop to each item in the list
    - This is makes sure that React knows which list item is which, so it can mount/un-mount/update the right components
    - We should not be hard coding these values, but should be using the items from useState.

#### Key Props

How do we do this?
- Create an array
- Use the .map function
    - convert the strings into list items
    - make sure to add a unique key prop

```js
// App.js
import { useState } from 'react';

export default function App() {
  const [items, setItems] = useState([]);
  const [newItem, setNewItem] = useState('');
  
  return (
    <>
      <ul>
        { items.map(item => {
          return (
            <li key={item}>{item}</li>
          );
        }) }
      </ul>

      <input
        type="text"
        value={newItem}
        onChange={(event) => setNewItem(event.target.value)}/>

      <button onClick={() => {
        setItems([...items, newItem]);
        setNewItem('');
      }}>
        Add List Item
      </button>
    </>
  );
}

```

Now, when you add a new list item, this works as you would expect:
- 1 caveat: if you add a duplicate item, you will get a warning message
    - "2 children have the same key"
    - make sure you always have unique keys!
        - most of the time you are iterating with data from the server, and they will be unique
        - backup: use an index

Example of using an index:

```js
...
<ul>
{ items.map((item, i) => {
    return (
    <li key={i}>{item}</li>
    );
}) }
</ul>
...
```

Note: Using index as a key should be LAST RESORT
- It can run into issues with React losing track of which element is which
    - Especially when elements are added in the middle of the list...

#### Fragments

One final point: Fragments

Example: We are returning a fragement, with list item inside of the fragment

```js
<ul>
{ items.map((item, i) => {
    return (
    <>
        <li key={i}>{item}</li>
        <li key="test">Test</li>
    </>
    );
}) }
</ul>
```

We now have the same issue as before! (The direct items inside of the list is now the fragment, not the list item, so we no longer have key items)

We cannot add a key prop to the fragment, so instead of using short name syntax, we have to use the full fragment name. Steps:
- import Fragment from react
- Use the full fragment name in the return value JSX
- add a `key` prop to the Fragment
    - ie. key={item}
    - you no longer need the keys for the children, as they are not in a list (the only items directly in the last are the Fragments!)

```js
<ul>
{ items.map((item, i) => {
    return (
    <Fragment key={item}>
        <li>{item}</li>
        <li>Test</li>
    </Fragment>
    );
}) }
</ul>
```

#### Takeaways

That is all you need to know to render a component list!
- Make sure any element directly in that list gets a key prop
- From there, add an array of elements into the JSX

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 11 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 12: Performance

To write performant React code, follow 2 simple steps:

Step 1: Never write the code below:

```js
useEffect(() => {
    setUselessNumber(uselessNumber + 1);
}, [uselessNumber]);
```

Step 2: Watch this video!

### Key Terms

#### useMemo

A React hook for memoizing a value.
- Takes in:
    - A function that returns a value to be memoized
    - dependency array
- Returns:
    - The memoized value
        - Only calls the passed in function to recalculate the value IF an item in the dependency array changes

Example:

```js
const value = useMemo(() => slowFunction(x, y), [x, y]);
```

Learn more: https://react.dev/reference/react/useMemo

#### useCallback

A React hook for memoizing a function. This function works the exact same as `useMemo`, except rather than memoizing the return value of a function, it memoizes the entire function.
- Can be useful for a variety of reasons
    - Example: If a callback function is passed into a dependency array that requires it to not change on every render

For example:

```js
const callback = useCallback(() => console.log(x, y), [x, y]);
```

Learn more: https://react.dev/reference/react/useCallback

#### React.memo

A React *higher-order component*
- takes in: a component
- returns: a memoized version of that componnet

If the props have not changed, wrapping a component in `React.memo` will cause it to avoid re-rendering
- Optional: This function can take in a 2nd callback function as a parameter
    - Determines when the component should re-render, with more fine control

For example, this component will only need to re-render when the number prop changes:

```js
function areEqual(oldProps, newProps) {
    return oldProps.number === newProps.render;
}

const MemoizedComponent = React.memo(myComponent, areEqual);
```

Learn more: https://react.dev/reference/react/memo

#### React.lazy

A React function for dynamically importing components, creating a potential performance boost when certain components are included in a module but not necessary for the initial render.
- Takes in: Callback function (that is run when the component is used)
- Returns: A call to the `import` function

Example:

```js
const LazyComponent = react.lazy(() => import ('./MyComponent'));
```

Learn more: https://react.dev/reference/react/lazy

#### React.Suspense

A react component for specifying a fallback interface while a child component is preparing to render (such as waiting for a lazy import)
- Takes in: `fallback` prop of a React element
- `children` prop: A suspending component

For example:

```js
<React.Suspense fallback={<LoadingIndicator />}>
    <LazyComponent>
</React.Suspense>
```

Learn more: https://react.dev/reference/react/Suspense

### Notes from the video

#### Setup

Setup App.js and MyButton.js:

```js
// App.js
import './App.css';
import { useState } from 'react';
import MyButton from './MyButton';

export default function App() {
  const [num, setNum] = useState(10);
  const [logValue, setLogValue] = useState('');

  return (
    <>
      <h1>Fib {num} is {fib(num)}</h1>
      <input
        type="number"
        value={num}
        onChange={(event) => setNum(parseInt(event.target.value))}
      />

      <input
        type="text"
        value={logValue}
        onChange={(event) => setLogValue(event.target.value)}
      />

      <MyButton onClick={() => {
        console.log(logValue)
      }}>Log Value</MyButton>
    </>
  );
}

function fib(n) {
  if (n === 2) return 1;
  if (n === 1) return 0;
  return fib(n - 1) + fib(n - 2);
}

```

```sh
cd src 

echo > MyButton.js
```

```js
// MyButton.js
export default function MyButton(props) {
    return <button {...props} style={{color: 'red'}} />;
}
```

View in Chrome:

```sh
cd test-app

npm start
```

View the Console via Right Click > Inspect > Console.

#### Intro

What we are going to look at in this video: Performance
- 2 main categories:
    - How to make renders more efficient / take less time
    - How to minimize the number of renders

Taking a look at our example, here is what we have:
- 2 pieces of state
    - number: 10
    - logValue: ''
- input: num
- input: text

- MyButton: A button that makes the text red
- fib function: 
    - Used as a placeholder for a slow function (we did not opitimze the time complexity of this function!) 

#### useMemo

Ways to make this code more performant:

First, we want to minimize how long 1 render takes. What is currently happening in each render?

- Create a huge return value
    - Calculate fib of the numeric input
        - Even if we type text into the 2nd input, which does not affect the 1st input/fib(num), we are still re-rendering

Memoization: an optimization technique that stores the results of expensive function calls to pure functions and returning the cached result when the same inputs occur again.

Idea: We do not need always calculate this function againt
- Parameters:
    - Parameters met: Calculate
    - Parameters NOT met: Don't do anything, use previous value

How to do this in React: Hook named `useMemo()`
- Input: Function
    - () => fib(num)
- Output: a return value of useMemo()
    - fibValue = fib(num)
        - This is only called IF something in a dependency array has changed
            - Here: Pass in dependency array of [num], so if we changed num, then we will call fib(num)

In the JSX that gets returned, make sure to change fib(num) for fibValue!

```js
// App.js
import './App.css';
import { useState, useMemo } from 'react';
import MyButton from './MyButton';

export default function App() {
  const [num, setNum] = useState(10);
  const [logValue, setLogValue] = useState('');

  const fibValue = useMemo(() => {
    console.log('calculating fib value');
    return fib(num); // this is returned IF num changes
  }, [num]);

  return (
    <>
      <h1>Fib {num} is {fibValue}</h1>
      <input
        type="number"
        value={num}
        onChange={(event) => setNum(parseInt(event.target.value))}
      />

      <input
        type="text"
        value={logValue}
        onChange={(event) => setLogValue(event.target.value)}
      />

      <MyButton onClick={() => {
        console.log(logValue)
      }}>Log Value</MyButton>
    </>
  );
}

function fib(n) {
  if (n === 2) return 1;
  if (n === 1) return 0;
  return fib(n - 1) + fib(n - 2);
}

```

Now, this is what we are seeing:
- change the input number: fib is calculated again
- change the input text: nothing happens!

Note: Even if a number is repeated ie. 10, we are doing the calculation again
- useMemo() IS checking if the dependency array is changing
- useMemo() is NOT saving the calls we have done to a cache or anything like that

Note: we could make it changed each time by making the dependency array `[num, logValue]`
- each letter typed has the value calculated again

Remove logValue from the dependency array and save before moving on.

To sum up this idea: If you have something calculated that does not change every render, use the useMemo() Hook
- It will save the component, from needing to calculate a value that hasn't changed, over again

#### React.memo

First, we looked at minimizing how long 1 render takes.

Next, we would like to minimize the number of renders we need to make!

Head over to MyButton.js and add this log statement so we can begin to understand just how often we are re-rendering the screen:

```js
// MyButton.js
export default function MyButton(props) {
    console.log('Rendering MyButton');

    // const startTime = new Date();
    // while (new Date() - startTime < 1000) {} (This will make the page take 1 second every render)

    return <button {...props} style={{color: 'red'}} />;
}
```

As it currently stands, we single time we add a new letter in the text input box, we are re-rendering the screen.
- Anytime the state changes, we are re-rendering MyButton

This is not optimal by any stretch of the imagination!

What if MyButton was slow to render? This would be a large issue. (Uncomment the code above and you'll see just how annoying it is...)

So, how do we fix this? We can memoize the entire component!
- What this will do: If the props have not changed, just use the old version of the component
    - Instead of updating it and rendering it again...

```js
// MyButton.js
import { memo } from 'react';

export default memo(function (props) {
    console.log('Rendering MyButton');

    const startTime = new Date();
    while (new Date() - startTime < 1000) {} // (This will make the page take 1 second every render)

    return <button {...props} style={{color: 'red'}} />;
});

```

What did we do here:
- Import memo from React
- Wrap the entire function/component that gets expored with memo()
    - similar to forwardRef function

Note: concept of functions that take in a component, and returns a new component, is known as a higher order component
- Typically we leave these functions as anonymous, so that's why we removed `MyButton` before (props)
    - This doesn't really matter tho...

What this is now saying: "In the case that the props have not changed, just use the previous version of this component"

Also worth noting: You can customize this behavior with a 2nd function

Example: areEqual

```js
import { memo } from 'react';

export default memo(function (props) {
    console.log('Rendering MyButton');

    const startTime = new Date();
    while (new Date() - startTime < 1000) {} // (This will make the page take 1 second every render)

    return <button {...props} style={{color: 'red'}} />;
}, areEqual);

function areEqual(prevProps, newProps) {
    return true;
}
```

What this does:
- Takes in previous/current props, tells you if they are equal
    - IF returns true: The component never needs to re-render (you are saying prevProps == newProps)
    - IF returns false: Re-rendering occurs

small aside: when you say it doesn't need to re-render, it does not guarantee it won't
- simple a performance increase (react CAN make it)
- do not rely on NEVER re-rendering
    - it should still work!

Delete the areEqual function as well as parameter #2 of the return value before moving along.
- Now, it will act as expected ie. just check if we have all of the same keys/value
    - If you change either inputs: Slow render
        - Rendering `MyButton` still takes 1 second
    - If you press the Log Value button: No re-render!
        - No need to re-render `MyButton`

#### 

Note: This does not fully work how we want yet. Why?
- In App.js, we are passing in a function as a prop
    - Each render of App.js component, we create a brand new function
        - Even tho it does the same thing, it is not equal, so MyButton will render everytime

How do we make sure that the function does not change, unless logValue changes?

We will memoize the function with useMemo() !

```js
import './App.css';
import { useState, useMemo } from 'react';
import MyButton from './MyButton';

export default function App() {
  const [num, setNum] = useState(10);
  const [logValue, setLogValue] = useState('');

  const fibValue = useMemo(() => {
    console.log('calculating fib value');
    return fib(num); // this is returned IF num changes
  }, [num]); // , logValue

  const onClickLog = useMemo(() => {
    console.log('clicking button ... ');
    return () => {
      console.log(logValue);
    };
  }, [logValue]); // only re-render if `logValue` changes

  

  return (
    <>
      <h1>Fib {num} is {fibValue}</h1>
      <input
        type="number"
        value={num}
        onChange={(event) => setNum(parseInt(event.target.value))}
      />

      <input
        type="text"
        value={logValue}
        onChange={(event) => setLogValue(event.target.value)}
      />

      <MyButton onClick={onClickLog}>Log Value</MyButton>
    </>
  );
}

function fib(n) {
  if (n === 2) return 1;
  if (n === 1) return 0;
  return fib(n - 1) + fib(n - 2);
}

```

What we did here:
- Created onClickLog()
    - Make it the onClick= for the MyButton in the return value of the JSX
        - This made it so that changing the logValue is the only way to get the MyButton to do the slow 1 second re-render

So, what is our current status now when we change items on the screen:
- Input number: Changes without re-rendering the slow MyButton
- Input text: Changes Renders the slow MyButton
- Log Value Button: Changes without re-rendering the slow MyButton

#### useCallback

useCallback: Makes it so that you do not need to nest functions when memoizing
- useMemo: Memoizes a value
- useCallback: Memoizes an entire function

```js
// App.js
import './App.css';
import { useState, useMemo, useCallback } from 'react';
import MyButton from './MyButton';

export default function App() {
  const [num, setNum] = useState(10);
  const [logValue, setLogValue] = useState('');

  const fibValue = useMemo(() => {
    console.log('calculating fib value');
    return fib(num); // this is returned IF num changes
  }, [num]); // , logValue

  const onClickLog = useCallback(() => {
    console.log('clicking button ... ');
    console.log(logValue);
  }, [logValue]); // only re-render if `logValue` changes
```


#### React.lazy

We still have the issue of the page taking 1 second to load due to `MyButton`, so how do we fix that?

For one, we don't even need `MyButton` on the initial render - we don't need it until something has been typed into the Logged Value input.

How to handle this: Change the import statement

Old:

```js
import MyButton from './MyButton';
```

New:

```js
const MyButton = lazy(() => import('./MyButton'));
```

Why is this better?
- We won't make the long/slow import of MyButton, until MyButton is actually used!

Lazy: Dynamically import
- Input: A component/function
- Output: A component that can be conditionally rendered

Make sure to conditionally render `MyButton` in the JSX return value from App.js:

```js
// App.js
{
    // if logValue exists; render; if not, don't render
    // initial render: NO MyButton
    logValue.length ?
        <MyButton onClick={onClickLog}>Log Value</MyButton> : 
        null
}
```

Now, when we do this, the page works fast. BUT, if we try to put text input into the logValue, we get an error!

Why do we get this error message that "A React component suspended while rendering, but no fallback UI was specified"?

"We got to this point where we lazily rendered MyButton (we tried to render once logValue.length was > 0), but then this is going to take some time, so we need to tell React what it needs to show in the UI while we wait for MyButton!

How to do this: Suspense!

#### Suspense

Suspense: Takes in a fallback that can be rendered while we Suspense/Wait on something to load
- 

Change our code from before to have suspense with the conditional rendering:

```js
// App.js
import { useState, useMemo, useCallback, lazy, Suspense } from 'react';
...
  return (
    <>
    ...
      {
        logValue.length ?
          (
            <Suspense fallback={<div>Loading...</div>}>
              <MyButton onClick={onClickLog}>Log Value</MyButton>
            </Suspense>
          ) : 
          null
      }
    </>
  );
}

```

What this does:
- While `MyButton` is suspended/loading, we instead will render a 'fallback'
    - Fallback: A prop that will be component

Now, 
- Changing number: Slow
- Changing text: Shows right away, 1 second wait for the `MyButton` to show up
    - logValue is a memoized component, does not slow down the page while we change fib

#### Takeaways

We have accomplished 2 powerful goals:
- Minimize number of renders
- Minimize speed of renders

Takeaways:
- It can be detrimental to memoize components that don't need them 
- Use these functions/methods sparingly!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 12 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 13: Writing Custom Hooks

```js
const useIUnderstandCustomHooks = () => {
    const [IUnderstand, setIUnderstand] = useState(false);

    useEffect(() => {
        setIUnderstand(true);
    }, [customHooksVideoIsWatched]);

    return IUnderstand;
}
```

### Key Term

#### Custom Hook

A helper function that uses hooks.
- When hook code becomes redundant or too long to easily read, it can be helpful to move that code into a helper function
- To denote that this helper function uses a hook itself, the name should be prefixed with `use` just like the built-in React hook functions

Learn more: https://react.dev/learn/reusing-logic-with-custom-hooks

### Notes from the video

#### Setup

Edit the code in App.js:

```js
import { useState, useRef, useEffect,  } from 'react';

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState('');
  
  const prevCount = useRef();
  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  const prevText = useRef();
  useEffect(() => {
    prevText.current = text;
  }, [text]);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <p>Count: {count}</p>
      <p>Previous render count: {prevCount.current}</p>

      <input
        value={text}
        onChange={(event) => setText(event.target.value)} />
      <p>Previous render text: {prevText.current}</p>
    </>
  );
}

```

Run it in Google Chrome:

```sh
npm start
```

Head to the Console via Chrome > Right click > Inspect > Console.

#### Full Tutorial

What is going on in this example:
- Increment button
- Count
    - Previous render count (each time there is a render, this updates to last render's value)
- Input Text box
    - Previous render text (each time there is a render, this updates to last render's value)

Note: Make sure NOT to confuse previous STATE with previous RENDER. (Previous render text/count can be the same as the previous render!)


How is this all working on the code:
- 2 states
    - count/setCount
    - text/setText

- 2 useRef(): Remember, these values don't cause re-render when changes!
    - prevCount()
    - prevText()

- Return JSX
    - Button: Increments count
    - Count: Displays count
    - Previous Render Count: Displays count
    - Text: Input for text
    - Previous Render Text: Displays text
    
So, this code all works, and nothing is wrong with it. But there is some redundancy...

- 2 different useEffect(), which both do essentially the same thing w/ different Refs

- 2 differnet useRef()
    - the 4 lines of code for prevCount are basically the EXACT same as for prevText

With traditional programming, we would see that an create a custom helper function.

This is exactly what a custom helper function that uses Hooks is!

Here is our Custom Helper Function:

```js
function usePrevious(value) {
  const prevRef = useRef();
  useEffect(() => {
    prevRef.current = value;
  }, [value]);

  return prevRef.current;
}
```

About this custom helper function:
- When you have a helper function that uses hooks, have it start with "use ..."
    - Since our function calls other Hook functions, we want to make sure React applies the same linting

- Next, 
    - Take values that are specific ie. prevText, and change to be more general ie. prevRef

- Make sure to make the return value prevRef.current!

We can now use this function, instead of the redundant code, ie:

```js
const prevCount = usePrevious(count);
const prevText = usePrevious(text);
```

Finally, the last thing we need to do is change is to remove the .current from the prevCount/prevText in the JSX return statement
- This is because usePrevious() already goes straight to prevRef.current for us!

```js
return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <p>Count: {count}</p>
      <p>Previous render count: {prevCount}</p>

      <input
        value={text}
        onChange={(event) => setText(event.target.value)} />
      <p>Previous render text: {prevText}</p>
    </>
  );
```

We can now increment the count and change the text, as you'd expect!

#### Takeaways

Custom Hooks: Writing helper functions for our hooks
- There are an infinite amount you can write
- Make sure to start helper with 'use' prefix, if you are using React hooks (it becomes a hook itself...)
- Just like a standard helper function in standard JS, there are a few different times to write a custom hook:
    1. Redundancy (want code in 1 place)
    2. Lots of code (very long useEffect(), make it more readable, so component is easier to read)

You will see a variety of custom hooks as we proceed!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 13 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 14: Portals

In React, portals are weird things that do weird stuff. That's pretty much it!

They're super useful tho...

### Key Term

#### Portal

A built-in method for rendering React elements into a DOM node outside of the parent React tree.

A portal is created by using the `ReactDOM.createPortal` function
- Takes in:
    - React element (gets appended the the 2nd arg, the DOM node)
    - DOM node

- Returns:

Note: The element will be appended to that DOM node, but it will still act the same as any other element in the original React tree (it can still take props, read from context providers, have events bubble up, etc.) 

Learn more: https://react.dev/reference/react-dom/createPortal

### Notes from the video

#### Setup

Update the code for App.js:

```js
// App.js
import { useState } from 'react';
import './App.css';

export default function App() {
  const [isHidden, setIsHidden] = useState(true);
  return (
    <>
      <div className="container">
        <button onClick={() => setIsHidden(!isHidden)}>
          {isHidden ? 'Show Modal' : 'Hide Modal'}
        </button>
        {isHidden || <Modal />}
      </div>

      <p className="other">
        Other Content
      </p>
    </>
  );
}

function Modal() {
  return <p className='modal'>Modal</p>
}

```

Next, update the code for App.css:

```css
/* App.css */
.container {
  position: relative;
  z-index: 0;
  background-color: lightgreen;
  height: 100px;
  padding: 10px;
}

.other {
  position: relative;
  z-index: 1;
  background-color: orange;
  height: 100px;
  padding: 10px;
}

.modal {
  position: fixed;
  z-index: 2;
  background-color: lightblue;
  width: 90px;
  height: 75vh;
  padding: 10px;
  top: 5vw;
  left: 50%;
  transform: translate(-50%);
}
```

Create index.html:

```sh
cd src

echo > index.html
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Portals</title>
</head>
<body>
    <div id="root"></div>
</body>
</html>

```

Run the code in the Browser:

```sh
npm start
```

View the Console via Chrome > Right click > Inspect > Console.

#### Full Video

What is currently in our example:
- state (boolean)
- Container div
    - Button (if clicked, changes state)
        - if state is false renders a `Modal`
- Paragraph (other content)
- Modal (a paragraph with className="modal")

Right now, this is probably not working how you'd expect it to...
- Modal is being created
    - You may think this means React is working, but it is below the other content
        - Sign that something may be wrong with our CSS!

What is going on in the CSS:
- .modal has a z-index of 2, which is higher than .container (0) and .other (1)
    - Why isn't it on top? / Why is it not working?
        - Stacking contexts. Essentially, because Modal is inside of Container div, the z-index of 2 only applies inside of that div
            - Outside of the div, the .container's z-index of 0 is used

How to solve this?
- Method #1: Move `Modal` outside of the container div
    - Let's not do this and pretend we need it inside...

- Method #2: Change the CSS
    - Getting rid of `position: relative` in .container and .other would do the job!
        - For sake of demonstration, pretend we need those CSS declarations like this too...

- Method #3: Use a Portal
    - Simple concept: Allows you to take a React element, leave it where it is, but when it is rendered on the DOM, change where it is rendered!


How we will do this:

Head over to index.html and add another div:

```html
<div id="root"></div>
<!-- new -->
<div id="modal-root"></div>
```

What we did here:
- Instead of putting `Modal` inside of the id="root" with the other elements, we used another div with id="modal-root"

Next, head back to App.js and create a Portal to move the Modal into that new div location we are creating:

```js
import { createPortal } from 'react-dom';

...

function Modal() {
  return createPortal(
    <p className='modal'>Modal</p>,
    document.getElementById('modal-root')
  );
}
```

What we did here:
- Imported createPortal from 'react-dom' (react-dom: bridge between react tree and DOM tree)
- Whenever we use Modal, change where it goes in the DOM
    - "Instead of adding the return value of Modal to where it is in the React Tree, append it to this other location!"

After saving, our Modal is now on top of the other elements!

Final point: When we use a portal, that element is still in its standard place in the React tree
- Access to props/context providers/events in the React tree

Example: Add an onClick event listener to the container div:

```js
// App.js
return (
    <>
      <div className="container" onClick={() => {
        console.log('Clicked container');
      }}>
...

```

After doing this, you will see 'Clicked container' in the console each time you click on the Modal. (You are essentially clicking on the container because of event bubbling)

Final note: Using a Portal does not change anything EXCEPT its actual location when it gets rendered on the DOM
- You won't use it very often, but good to know!
    - Most commonly used for: Modules/Tooltips

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 14 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 15: Class-Based Components

You'll never use these, but we still want you to watch a video about them.

### Key Term

#### Class-Based Component

A JavaScript class that extends the `React.Component` class and acts as a React component.
- All class-based components must implement a `render` method, which usually returns JSX similar to a functional component
- Instead of taking props as a parameter, all class-based components store their props in the `this.props` instance variable
    - Moreover, state is stored in `this.state` and updated using the `this.setState` method.

Class-based components cannot use hooks - instead, they can implement a variety of lifecycle methods that work similar to hooks. Here are some of the more commons ones:

- `componentDidMount`: Runs immediately after the component mounts.
    - Usually used for setting up subscriptions.

- `componentDidUpdate`: Runs immediately after the componenet updates due to a state or props change. 
    - Common use case: Network requests that depends on props or state

- `componentWillUnmount`: Runs right before a component unmounts
    - Usually used for cleaning up any subscriptions

- `shouldComponentUpdate`: Similar to `React.memo`, determines if the componenet should re-render based on new props and new state values

Learn more: https://react.dev/reference/react/Component

### Notes from the video

#### Setup

Update the code for App.js:

```js
// App.js
import { useState } from 'react';

export default function App() {
  return (
    <>
      <Counter startingCount={10} />
      <Counter />
    </>
  );
}

function Counter({ startingCount = 0 }) {
  const [count, setCount] = useState(startingCount);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

```

Run the code in the Browser:

```sh
npm start
```

View the Console via Chrome > Right click > Inspect > Console.

#### Converting Functional to Class-Based

So far, we have seen "Functional Components"
- Functional Components: Functions that return JSX

Components can also be classed!
- Before Hooks, you had to use Classes
    - (if you wanted to work with State, or any lifecycle attribute)

Class-Based Components: Not seen very often in modern React
- Still very important to understand / useful

Starting out, let's take our code that is working, and turn it from Functional to Class-Based:

```js
// App.js
import { Component } from 'react';

export default function App() {
  return (
    <>
      <Counter startingCount={10} />
      <Counter />
    </>
  );
}

class Counter extends Component {
  constructor(props) {
      super(props);
      this.state = {
          count: props.startingCount ?? 0
      };
  }

  render() {
    return (
      <>
        <button onClick={() => {
          this.setState({
            count: this.state.count + 1
          });
        }}>
          Increment
        </button>
        <p>Count: {this.state.count}</p>
      </>

    );
  }
}

```

What we did here:

1. Turn Counter from `function` into `class`
- classes don't take any parameters, so remove that
- instead of taking parameters, extend React's `Component` class

2. Remove useState()
- Cannot use state, or any Hooks!

3. Change the return statement into a render() method
- It will call this function when we want to render 
    - Remember: Each class requires 1 method

4. Create an instance variable for our state (to define `setCount` and `count` - Once we remove the line with useState, these became undefined)
- count: this.props.startingCount ?? 0
    - "if startingCount is null/undefined, default to 0"
- setCount: 

Note: Can also do this with a constructor()

```js
class Counter extends Component {
    constructor(props) {
        super(props);
        this.state = {
            count: props.startingCount ?? 0
        };
    }

    ...

}
```

5. Have this.setState() method be called when we want to change 
- This is used for the onClick() for the button
    - Input: Entire state object

6. Have `count` come from `this.state.count`
- This needs to be changed in the return JSX for method render()


Everything should work now!

One small note:
- If you use a standard function in the onClick={} (instead of an arrow function), it will not work
    - Why? Because we used a function that created a new `this` context
        - Arrow functions do not create a new context, and still uses the context of the class

Advice for going forward:
- Arrow functions: Use them!

- If for some reason you HAVE to use a regular function: use .bind(this)
    - What it does: Binds the .this value of the class, to .this inside of the function

Example in action: 

```js
  render() {
    return (
      <>
        <button onClick={function() {
          this.setState({
            count: this.state.count + 1
          });
        }.bind(this)}>
          Increment
        </button>
        <p>Count: {this.state.count}</p>
      </>

    );
  }
```

For readability, let's go back to the arrow function before proceeding.

#### Lifecycle Methods

Next, let's look at Lifecycle Methods.
- Functional Component: useEffect() can Hook you into the React lifecycle
- Class-Based Components: Instead of that Hook, there are a variety of different methods to hook into different parts of the lifecycle:
    - componentDidMount
    - componentDidUpdate
    - componentWillUnmount
    - shouldComponentUpdate

##### Method #1: componentDidMount
- Works similar to a useEffect() that only runs on mount

```js
componentDidMount() {
    console.log('mounted');
  }
```

After running this, you will see 'mounted' logged out twice (1 for each instance of the counter)
- If you increment the counts, nothing happens!
    - it only runs on initial mounts, not every update...

##### Method #2: componentDidUpdate
- Invoked immediately after updating occurs, but is not called on the initial render.
    - Takes in 2 parameters:
        - prevProps
        - prevState

```js
componentDidUpdate(prevProps, prevState) {
    console.log(prevProps, prevState);
  }
```

What happens for this example:
- Pressing increment for 1st counter:
    - {startingCount: 10} > {count: 10}
    - {startingCount: 10} > {count: 11}
    - {startingCount: 10} > {count: 12}
    - etc.

- Pressing increment for 2nd counter:
    - {} > {count: 0}
    - {} > {count: 1}
    - {} > {count: 2}
    - etc.

##### Method #3: componentWillUnmount
- Runs when a component is about to unmount
    - 

```js
componentWillUnmount() {
    console.log('unmounting');
  }
```

You must add some state so that the component actually gets un-mounted:

```js
// App.js
export default function App() {
  const [shouldRender, setShouldRender] = useState(true);
  return (
    <>
      {/* <Counter startingCount={10} /> */}
      { shouldRender && <Counter /> }
      <button onClick={() => setShouldRender(!shouldRender)}>
        Toggle Counter
      </button>
    </>
  );
}
```

This code makes it so that the 2nd counter renders conditionally.
- Increment: Works as you'd expect
- Toggle Counter: unmounting
- Toggle Counter (again): mounted/unmounting/mounted

##### Method #4: shouldComponentUpdate
- Works very similar to React.memo() ie. whenever props/state changes, this method gets the new props/state as parameters
    - 2 params:
        - nextProps
        - nextState
    
    - IF function returns true: Re-render
    - IF NOT and returns false: do nothing (do not re-render)

```js
shouldComponentUpdate(nextProps, nextState) {
    console.log('should component update?');
    console.log(nextProps, nextState);
    return nextState.count < 3; // update will NOT happen IF nextState.count >= 3
  }
```

What happens now:
- Increment works as expected
    - Once count gets to 2, nothing will happen to the screen
        - `shouldComponentUpdate()` checks, and it returns false, so that's why it doesn't increment!

The state is still updated! but the component never gets re-rendered...

#### Refs

Next, let's look at Refs.

Creating a Ref:
- Functional component: useRef()
- Class-based component: createRef()

Full code with this.buttonRef:

```js
// App.js
import { Component, useState, createRef } from 'react';

export default function App() {
  const [shouldRender, setShouldRender] = useState(true);
  return (
    <>
      {/* <Counter startingCount={10} /> */}
      { shouldRender && <Counter /> }
      <button onClick={() => setShouldRender(!shouldRender)}>
        Toggle Counter
      </button>
    </>
  );
}

class Counter extends Component {
  constructor(props) {
      super(props);
      this.state = {
          count: props.startingCount ?? 0
      };
      this.buttonRef = createRef();
  }

  componentDidMount() {
    console.log('mounted');
    console.log(this.buttonRef);
  }

  render() {
    // console.log(this.buttonRef); 
    // (this would return null - the first time render is called, the component is not mounted on the screen - nothing to set the ref to!)
    return (
      <>
        <button ref={this.buttonRef} onClick={() => {
          this.setState({
            count: this.state.count + 1
          });
        }}>
          Increment
        </button>
        <p>Count: {this.state.count}</p>
      </>
    );
  }
}

```

#### Contexts

Next, let's define a Context at the top of our file:

```js
// App.js
const Theme = createContext({
  mode: 'dark'
});
```

What is this: A context to keep track of whether we are on dark/light mode!

Next, in the App component, add a context provider:

```js
// App.js
export default function App() {
  const [shouldRender, setShouldRender] = useState(true);
  return (
    <Theme.Provider value={{mode: 'dark'}}>
      {/* <Counter startingCount={10} /> */}
      { shouldRender && <Counter /> }
      <button onClick={() => setShouldRender(!shouldRender)}>
        Toggle Counter
      </button>
    </Theme.Provider>
  );
}
```

Make sure to add to both the opening and closing tag.

Now, if we want to use a Context with a Class component, we cannot use the useContext() hook!

We have 2 options instead:

1. Add a static variable `contextType`
- If anywhere inside this `Component` you were to log out `this.context`, it would be 
    - In this case: {mode: 'dark'}

```js
import { Component, useState, createRef, createContext } from 'react';

const Theme = createContext({
  mode: 'dark'
});

export default function App() {
  const [shouldRender, setShouldRender] = useState(true);
  return (
    <Theme.Provider value={{mode: 'dark'}}>
      { shouldRender && <Counter /> }
      <button onClick={() => setShouldRender(!shouldRender)}>
        Toggle Counter
      </button>
    </Theme.Provider>
  );
}

class Counter extends Component {
  static contextType = Theme;
  constructor(props) {
      super(props);
      this.state = {
          count: props.startingCount ?? 0
      };
      this.buttonRef = createRef();
  }

  componentDidMount() {
    console.log(this.context);
  }

  render() {
    return (
      <>
        <button ref={this.buttonRef} onClick={() => {
          this.setState({
            count: this.state.count + 1
          });
        }}>
          Increment
        </button>
        <p>Count: {this.state.count}</p>
        <p>Theme: {this.context.mode}</p> // new
      </>
    );
  }
}

```

This is fine, but we can only consume 1 Context at a time...
- What if we want multiple Contexts?

2. Add `Theme.Consumer` to the Return JSX in the render() function
- Takes a function in as the children

```js
  render() {
    // console.log(this.buttonRef); 
    // (this would return null - the first time render is called, the component is not mounted on the screen - nothing to set the ref to!)
    return (
      <>
        ...
        {/* <p>Theme: {this.context.mode}</p> */}
        <Theme.Consumer>
          {
            context => <p>Theme: {context.mode}</p>
          }
        </Theme.Consumer>
      </>
    );
  }
```

#### Takeaways

Most of the time: Functional Components
- More Modern

Some of the time: Class-based Components
-  Older
    - You can do anything in Classes, still
    - Syntax is different
    - More Verbose

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 15 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 16: Error Handling

Yes - even the Almighty React is not immune to errors.

Let's explore how to handle these unwanted fiends.

### Key Term

#### Error Boundary

A React component that catches errors in child components, preventing the entire application from crashing from a single error.
- Must be class-based components, in order to take advantage of 2 lifecycle methods:

    - `static getDerivedStateFromError(error)`: Called during the render phase and updates the current state of the component.

    - `componentDidCatch(error, errorInfo)`: Called during the commit phase for the purpose of side-effects related to the caught error

For example, this would be a compleete error boundary component:

```js
class ErrorBoundary extends Component {
    state = { hasError: false };

    static getDerivedStateFromError(error) {
        return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
        logErrorToServer(error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            return this.props.fallback;
        }

        // else...
        return this.props.children;
    }
}
```

Learn more: https://react.dev/reference/react/Component#catching-rendering-errors-with-an-error-boundary

### Notes from the video

#### Setup

Update the code for App.js:

```js
// App.js
export default function App() {
  return (
    <>
      <h1>Hello World</h1>
      <Buggy />
    </>
  );
}

function Buggy() {
  throw new Error('error');
  return <h1>Buggy</h1>;
}

```

Run the code in the Browser:

```sh
npm start
```

View the Console via Chrome > Right click > Inspect > Console.

Note: This is not going to load up right now, because due to the thrown error, that is where we go (Instead of seeing Hello World/Buggy which are both `h1`)

#### Full Tutorial

If an error is thrown anywhere in the React tree, the output is nothing!
- Commenting out the error will get what we expect, otherwise, we will get a blank screen

The issue: If we get 1 single error, React won't show anything
- In complex applications, 1 bug is pretty much inevitable

How do we handle this?

#### Error Boundary

Error Boundary: A special component that will determine what will happen if one of its children throws an error
- Uses Class-Based Components
- Extends from React's `Component`

- 2 inputs
    - children
    - fallback

- Has a render() method
    - Binary, as one of the following 2 is always true when we render:
        
        1. There is an error
        - return this.props.fallback
        - return <h1>Oh no, this is an error<h1>

        2. There is NOT an error
        - return this.props.children;
        
    - We will hold whether or not there is an error, in State

```js
// App.js
import { Component } from 'react';

export default function App() {
  return (
    <>
      <h1>Hello World</h1>
      <Buggy />
    </>
  );
}

function Buggy() {
  throw new Error('error');
  return <h1>Buggy</h1>;
}

class ErrorBoundary extends Component {
  state = { hasError: false };
  render() {
    if (this.state.hasError) {
      return this.props.fallback;
    }
    // else...
    return this.props.children;
  }
}

```

What we did here:
- Create our 1st ErrorBoundary Component
- Created state
    - hasError (false by default)


But, we need to actually know if there was an error!

In the past: Try-catch blocks
- Issue: This is Imperative
- What we need: Declarative (for React)

React has a lifecycle method we can use: `getDerivedStateFromError`
- Gets used if there is an error in the children
- Inputs: some error
- Outputs: new state

```js
static getDerivedStateFromError(error) {
    return { hasError: true }; // could return the error in this, if we want
}
```

Recap on what we have done so far in this Class:
- We have State (hasError)
    - IF there is an error in ANY of the children: Change state to hasError = true
    - Else: hasError = true

- We have a render() method, that depends on state
    - If hasError = true: return the fallback (comes from props)
    - If hasError = false: return the children 


#### Implement the ErrorBoundary Class

To use, in JSX, you will wrap any buggy component with `<ErrorBoundary>` tags
- Can be used on any component that we think MIGHT throw an error

```js
export default function App() {
  return (
    <>
      <h1>Hello World</h1>
      <ErrorBoundary fallback={<h1>There was an error...</h1>}>
        <Buggy />
      </ErrorBoundary>
    </>
  );
}
```

Now, if Buggy throws an error: We will render the fallback! (Which was passed in via ErrorBoundary tag)

Reminder: This `ErrorBoundary` only catches in components below it
- If you were to add an error to line 4 right where App() starts, you wouldn't catch it.
- The same would hold true by throwing it inside of ErrorBoundary/render() on line 27

#### componentDidCatch

Now, there is 1 more lifecycle method that we can use with these `ErrorBoundary` tags.

Remember: We have the `static getDerivedStateFromError(error)`
- This says what we do in the case of an error
- We don't want any side effects with this method, all we want to do is return the new state.
    - When there are side effects, we have another method to use

componentDidCatch(): 
- Runs during commit phase (later on down the line)
    - Difference: `getDerivedStateFromError` runs during the render phrase

- Inputs: 
    - error: error thrown
    - errorInfo: info about error thrown
- Outputs: 
    - 

Example:

```js
componentDidCatch(error, errorInfo) {
    logErrorToServer(error, errorInfo);
}
```

Note: This has not actually been implemented, just know it is mock code.

Idea for componentDidCatch: This is for side effects
- Code does not impact the render
    - Is for things that do not impact what is on the page
        - Example: Saving error messages

#### Takeaways

Key points:

1. Need to use a Class
- not a Hook method in React

2. Use `getDerivedStateFromError` to change the state (based on error/existence of error)

3. In render method, conditionally render if an error exists(based on the State)
- Can hard-code OR use props
- If no error, just return the children

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 16 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 17: Debugging React

```js
console.log('in the useEffect');
console.log('did this component render?');
console.log('why does this keep re-rendering?');
console.log('maybe VanillaJS is not so bad after all...');

```

### Key Terms

#### React.StrictMode

A React component for putting a component in strict mode.
- 2 primary benefits for assisting in debugging:
    1. It provides warnings when using depracated functions OR lifecycle methods.
    2. It double-invokes some functions (ie. functional components)
    - This helps find potential bugs related to side-effects in functions that should not have side-effects

Learn more: https://react.dev/reference/react/StrictMode

#### React.Profiler

A React component for tracking how often a component renders
- Requires 2 props:
    - `id`: A unique identifier
    - `onRender`: A callback function to run after the component renders (during the commit phase)\

For performance reasons, the Profiler is ignored in production mode.

Learn more: https://react.dev/reference/react/Profiler

#### React DevTools

An official React browser extension for debugging React.

### Notes from the video

#### Setup

Update the code for App.js and Index.js:

```js
// App.js

```

```js
// Index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

```

Run the code in the Browser:

```sh
npm start
```

View the Console via Chrome > Right click > Inspect > Console.

#### Intro

Point of video: How to debug React code
- Will be the same as standard HTML and JS
- Will also look at React-specific tools!

Summary of the code we have now:
- 2 Counters
    - 1 w/ initial value of 5
    - 1 w/ initial value null

- Counter function
    - State, which uses input of initialValue (default 0)
    - Button that Increments the count

Remember: index.js is the entry point to this App

First thing to discuss: In index.js (The main JavaScript file)
- React.StrictMode

Now, what exactly is Strict Mode?

#### Strict Mode

Strict Mode: Helps you find issues in your code
- Gives you warnings in the console if you use depracated functions
- "Double Invocation"
    - In strict mode, your functions for componenets are invoked twice
        - Purpose: Avoid side effects
            - We don't want side effects in the main function
            - By doing things twice, you can see when you did things by accident
                - Does not happen in production

Note: React is allowed to re-render the DOM whenever it wants
- It doesn't do this usually, but if anything has side effects, it is best practice to put it inside of a ``

Let's see this double invocation in action:

```js
// App.js
import { useState } from 'react';

let renderCount = 0;

export default function App() {
  renderCount++;
  console.log('rendering');
  
  return (
    <>
      <Counter initialValue={5} />
      <Counter />
      <p>Render count: {renderCount}</p>
    </>
  );
}
```

What happens:
- rendering: logged only once
- render count: 2

Essentially what is happening: When double invocation is happening, the console.log()'s will only run once
- In new React (<= 17), you won't see the console logs get double invoked!

Note: As you may expect now - if you go back to Index.js and remove the React.StrictMode, you will only see a render count of 1. (No double invocation)

Takeaway: Always have strict mode and double invocation on, when developing!

#### Profiler

Profiler: Keeps track of when a component is rendering
- You can wrap any component in one
- Inputs: 
    - id: 
    - function: onRender = {}
        - funny, this doesn't actually run on render... (on commit, so AFTER render, and AFTER React is done running the main function)

Let's try it out!

Do the following and let's see what happens to our program:
- import Profiler form React
- change the Fragments into being `Profiler`
    - add id
    - add onRender function

```js
// App.js
export default function App() {
  renderCount++;
  console.log('rendering');
  
  return (
    <Profiler id='App' onRender={() => console.log('commit')}>
      <Counter initialValue={5} />
      <Counter />
      <p>Render count: {renderCount}</p>
    </Profiler>
  );
}
```

What is going on here:
- 'rendering' is printed
- 'commit' is printed (after the render, during the commit)

Admittedly: `Profiler` is not used very often! (If you are dealing with a hard to find bug, this can help for knowing that a component is only rendering when it should be!)

Note: Just like before, you can only use `Profiler` in development mode. (It will be ignored without StrictMode)

#### React DevTools

First, head into Components via Chrome > Right Click > Inspect > Components (It may be all the way to the right)

This is now essentially the same as the elements tab, but instead of HTML elements, it shows React elements.

Components
- App
    - Profiler
        - Counter
        - Counter

There are 4 actions you can do when you click on a Component:
- Suspend the component
- Inspect the DOM Element
- Log this component's data to the console
- View source code for this data

One more thing with the Components Tab - Custom Hooks!

Start by going into App.js and replacing `useState()` with a Custom Hook:

```js
// App.js
function Counter({initialValue}) {
  const [count, setCount] = useMyState(initialValue);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
      <p>Count: {count}</p>
    </>
  );
}

function useMyState(initialValue = 0) {
    useDebugValue('hello world');
    return useState(initialValue);
}

```

What does useMyState do:
- Handles the default value

Head back to Components > Counter, you will now see the Custom Hook of `MyState` with a value of 5!
- It remove the 'use' prefix, then gives the rest of the CustomHook's name

Note: Another thing you can do to add data to the MyState is the `useDebugValue()` from React.


One last thing - the Profiler tab. (This is different than the Profiler component, they are unrelated)

What can we do with the Profiler tab?
- Record while we do something on the page
    - Examples:
        - refresh
        - click buttons
    - We do this to see what components are re-rendering.

Try it out! Refresh the page, head to the Profiler tab, and do the following:
- Hit the record button for 'Starting Profiling'
- Increment the count
- Hit the 'Stop Profiling'

You should now see that none of the components on the page rendered, except for the Counter.

Note: You can hit the refresh button to have the profiling start over, and you can see which components are causing the initial render to take _ amount of time.

(Ours is running instantly, so not the best example right now - let's change that)

Add this code to make the Counter slow:

```js
// App.js
function Counter({initialValue}) {
  const [count, setCount] = useMyState(initialValue);

  const startTime = Date.now();
  while (new Date() - startTime < 500) {}
  ...
}
```

Save this, click the reload button in Profiler to start Profiling, and you will now see that each of our Counters took 1000ms to run.
- The entire app takes 2000ms to run
    - Double invoked is causing this ie. 500ms while loop * 2counters * 2 invocations
        - We only get a single thread, so they cannot run at the same time

Ending note: Profiler is a good way to see why a certain page is running slow!

#### Takeaways

Debugging React:
- Will mostly be the same as with Vanilla JavaScript / HTML
- These are a few extra tools to help make our lives easier

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 17 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 18: Best Practices

Just because you're using React doesn't mean that your code is safe from becoming a steaming pile of spaghetti.

Follow these best practices to avoid turning your code into a delicious Italian dish!

### Key Term

#### DRY Component

Short for "don't repeat your code", a principle involving refactoring any repeated code into helper functions.
- In React: We follow DRY principles in the following ways:
    - moving shared interfaces into helper components
    - moving common hook logic into custom hooks

### Notes from the video

#### Intro

How to write clean code that is the following:
- Easy to maintain
- Easy to update
- Easy for other people to read

#### Directory Structure

Rules
- 1 exported component per file
    - filenames match their component names (makes it easy to find)
        - smaller helper functions: OK

- Consistent organization
    - His advice: Separate `src` into sub-directories:

        - `components`: all of the components
            - `base`: design system components (can be included in Bootstrap)
            - `pages`: main components of application
                - `home`
                - `product`
                - etc.
            
        - `hooks`: useful throughout the application


Biggest thing: Be consistent!!

#### DRY Components

DRY = "Don't repeat your code"
- Refactor repeated UI into helper components
- Refactor repeated hook logic into custom hooks

Good practice:
- Create custom hooks, even if you don't need to repeat the code (Makes code easier to read)
- "If I can think of a good name for a hook, it probably makes sense to re-factor the code with that custom hook"
    - Hooks tend to be difficult to read, to this is good

#### Consistent CSS

There are a number of ways to include a stylesheet in a React component:
1. import syntax

```js
// Top of module
import "component.css";
```

Note: If you don't use webpack, this may not work

2. Inline style attributes
- Do NOT recommend!! (Makes code harder to read w/ all of the CSS information, it also has worse performance at times)

3. Global / Page-level Stylesheets
- Idea: Global styles/variables, then each page has its own stylesheet

4. CSS-in-JS libraries
- They all try to tackle problems of CSS not fitting in React ecosystem. Examples:
    - Styled Components
    - CSS Modules
    - Styled JSX
- Not necessary to use if you don't want to...

Main thing: Be consistent!!! (Pick 1, stick to it)

#### Keep HTML Semantic

Semantic HTML: Still important when writing React code, since React is still feeding HTML to the browser
- Use the correct grouping tags
    - don't just use div's everywhere, when you should be using `main`, `body`, etc.

- Focus on accessibility
    - alt attributes
    - aria
    - do anything you normally would do to keep HTML accessible!

- Avoid extra divs with fragments
    - It can be easy to get in the habit of spamming these
    - Use fragments
        - Especially if the div is only there for a single return value.

#### Miscellaneous Tips

Miscellaneous Tips

- Follow a style guide for consistency
    - Many companies have their own
    - For a smaller project, use an open source guide

- Stick to either ONLY functional or ONLY class-based components
    - Recommendation: Functional!

- Minimize prop-drilling
    - We don't want a bunch of props over-complicating our code
    - Use contexts or state management libraries
        - ie. Redux

- Avoid imperative code
    - Example: useImperativeHandle
        - Use this as a last resort
    - Imperative code makes things harder, especially because React is naturally Declarative

- Write self documenting code
    - You should be able to look at the name of the component, then look at its return value, to know what it is doing
    - If you find you have a confusing component, break it up!

#### Takeaways

Be consistent, it leads to clean code!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 18 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 19: React Under The Hood

Okay, React is awesome, beautiful + magical.

But how does it work, exactly...?

### Key Terms

#### React Element

The internal object representation of a node in the React tree.
- React Elements can represent 1 of the following 2:
    - DOM nodes
    - React components

Learn more: https://legacy.reactjs.org/blog/2015/12/18/react-components-elements-and-instances.html#elements-describe-the-tree

#### Virtual DOM

A "virtual" representation of the DOM kept by React internally.
- This data structure is not tied to the actual DOM, so it is much quicker to update (than the actual DOM)

Learn more: https://legacy.reactjs.org/docs/faq-internals.html

#### Reconcilation

The algorithm used by React to determine the "diff" between 2 trees of React elements.
- After each state update, React runs the reconciliation algorithm to determine what has changed
    - Changelog is sent to the rendering function (in the case of the browser, this is the React DOM)
        - The rendering function can update the page using the information

Learn more: https://legacy.reactjs.org/docs/reconciliation.html

### Notes from the video

#### Intro

When we write some component and add it to the DOM, what is actually happening?

#### React.createElement

We know this is true:
- We write JSX
- JSX feeds into React.createElement()
- React.createElement() outputs a React element object
    - This is not a DOM node

To reiterate: JSX -> React.createElement() -> React element object

![React.createElement](./figures/react/1.png)

Most of the properties on this object look familiar:
- key: null (we did not set a key for <h1>)
- props: in this case only is taking the children, ie. "Hello World"
- ref: null (we don't have a ref)
- type: "h1"
- $$typeof: 
    - is not super important
    - idea: protect against injection attack
        - lets React know it did not come from JSON

#### ReactDOM.render

Once our JSX turns into a React element object, what do we do from there?

You call ReactDOM.render!

Function: ReactDOM.render: Traverses the React element object, turning them into DOM nodes
- Note: It is a tree, because of the props: {children: "Hello World"}

- Inputs:
    - React element object
    - Location to append DOM nodes
        - DOM nodes are appended to the 2nd argument's location

- Output: DOM nodes

![ReactDOM.render](./figures/react/2.png)

#### Virtual DOM

Now, that was the initial render. How does React keep up with Updates?

Virtual DOM.

Virtual DOM: The data structure created by nesting React Elements
- Important point: Much faster to update than the real DOM
    - Nothing needs to change on screen!
        - Standard DOM: Page has to update
        - Virtual DOM: You are just updating a JS Object

Note: Virtual DOM is a misnomer (React team is going away from this term)

#### Reconcilation

Now, if there is state update, React will need to update the real DOM as well. This is known as Reconcilation!

Reconcilation: An algorithm that React uses internally to figure out what has changed
- Takes old DOM object
- Takes new DOM object
- Figures out the difference! ("diff")

Goal: Figure out the differences, with the least/mininmum number of operations to change old into new!
- This all happens in the Virtual DOM
- Changelog is then sent to a rendering function
- Rendering function makes changes to the DOM

Note: This is where the Virtual DOM misnomer comes in, since it doesn't actually have to be the DOM
- Example: React.Native, which lets you write mobile apps with React, doesn't even have a DOM!
    - Uses reconcilation still
    - Uses different rendering function that takes changelog and creates a new output that mobile devices require

##### The algorithm

How Reconcilation calculates the "diff" of the virtual DOM after updates:

1. Check type: If root nodes are of different types: delete tree and rebuild
- least efficient type of change

2. Since type did not change, check attributes: If attributes changed, update existing nodes
- tell render-er it can update the existing nodes, just change their attributes
- example: if a class changed, the DOM node would be updated to have the new class (not replaced with a new DOM node)

3. Recurse on all children!
- repeat steps 1 and 2 for every child of the root node
    - go until leaf nodes/bottom of the tree

High level, that is it! There are other optimizations, though.

A term you may hear: Fiber

Fiber: A modern re-write of the reconciliation algorithm
- Focused on incremental rendering
- Knowing the changes is not important (very academic), but good to know at a higher level that incremental rendering is
    - "Chunk out" the rendering process
    - Break it up into multiple different steps
        - Prioritize more important things
            - Example: Slow animations

#### Keys

Final thing to look at: How the reconciliation algorithm handles keys!

![Keys](./figures/react/3.png)

When React recurses on children, it assumes the elements are in the same order.
- Keys: Lets us tell React which elements are which, so we don't need to rely on the elements being in the same order

Let's look at an example:

```html
<ol>
    <li key="first">First</li>
    <li key="second">Second</li>
</ol>
```

=> 

```html
<ol>
    <li key="zeroth">Zeroth</li>
    <li key="first">First</li>
    <li key="second">Second</li>
</ol>
```

What is going on here:
- Starting out -> First ordered list: 2 list items
- Final state -> Second ordered list: 3 list items
    - 3rd list item was added at the beginning (or prepended)

Situations:
- If we appended list item to end of list: Keys would NOT matter
    - React knows the 1st and 2nd items have not changed (still list item, still same content)
    - 3rd item would get added flawlessly 
 
- But, we prepended the list item to FRONT of list: Keys now DO matter
    - WITHOUT KEYS:
        1. React will compare 1st list item to 1st list item
            - First != Zeroth
                - Result: Update existing node

        2. React will compare 2nd list item to 2nd list item
            - Second != First
                - Result: Update existing node

        3. React will add the 3rd value (it did not exist before)
            - Second
                - Result: Create a new element

        - This is inefficient!

    - WITH KEYS:
        1. React will look at the key="zeroth" list item
            - React has not seen this key before, so
                - Result: Create a new element

        2. React will look at the key="first" list item
            - React HAS seen this key before
                - Result: No updated necessary

        3. React will look at the key="first" list item
            - React HAS seen this key before
                - Result: No updated necessary

        - This is much moreefficient!
            - React knows the 1st and 2nd items have not changed (still list item, still same content)
            - 3rd item would get added flawlessly


That is it for Keys, and why they are so important!
- Whenever you use dynamic data to create an array of children, ensure to give them all a key

 
#### Takeaways

This only scratches the surface, but should give a good idea of the following:
- Writing components
- Rendering them to the screen

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 19 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

## 20: Companion Libraries

If you are already familiar with Redux, this video covers more than just Redux!

If you are not already familiar with Redux, just watch the video!

### Key Terms

#### Redux

A JavaScript state-management library, often used with React.
- Uses reducer functions to create a global store (any component can read from it)

Learn more: https://redux.js.org/

#### Recoil

A JavaScript state-management library built for React.
- Uses Atoms, which are global pieces of state (any component can subscribe to)

Learn more: https://recoiljs.org/

#### Server-Side Rendering

A method of rendering an application where the server generates the final HTML page, rather than giving the client an empty HTML file and the scripts needed to generate the page.
- Can create significant performance improvements
- Also helps with search-engine optimization

#### Static-Site Generation

Similar to server-side rendering.

A method of rendering an application where the server generates the final HTML pages, rather than giving the clietn an empty HTML file and the scripts needed to generate the page.

Key distinction between static-site generation and server-side rendering:
- static-site generation: creates all possible HTML files at build time
- server-side rendering: creates a new HTML file for each server request

#### Next.js

A JavaScript framework built around React.
- Primary use case: Server-side rendering
- Other uses cases:
    - Variety of tools to simplify development
    - Variety of tools to improve performance

Learn more: https://nextjs.org/

#### Gatsby

A JavaScript framework with the primary use case of static-site generation.
- In addition to static-site generation, Gatsby also includes a wide variety of other features that simplify development and improve performance
    - Just like Next.js...

Learn more: https://www.gatsbyjs.com/

#### React Router

A React library for declaratively controlling page routing from the client-side.

Learn more: https://reactrouter.com/en/main

### Notes from the video

We will not be going super in-depth on these libraries and tools, but the purpose is so you can be conversational/know when to use one option over the other.

We will start with state management libraries.
- Main purpose: Global state
    - React is good at having state at component level
    - When State needs to be used across application (ie. logged in user), it is hard to do this with just React.

#### Redux

Redux: Central/Global state that uses Reducer functions
- Most popular state management library to React
    - Doesn't need to be used with React, but is its most common use case
        - Uses `React Redux` to integrate with React (this is what you use)

- Similar to `Reducer` hook
    - Difference: Instead of instance level, this is global level state

![Redux](./figures/react/4.png)

How data flows when we use Redux with React:
- Store: Global state that we want access to
    - Contains information, such as:
        - logged in user

- UI: Standard React Components
    - Depends on state
        - State comes from the Redux Store
            - Whenever State changes, the UI will know to update

But, something may happen on the UI (Example: The user logs out) and this would need to change the state in the Redux Store.

- dispatchFunction: Changes the state in the Redux Store.
    - Comes from the Store
    - Takes in an Action (similar to useReducer) with the following:
        - type
        - payload

        Example:

        ```js
        {
            type: "logout",
            payload: extraInfo
        }
        ```

When you dispatch an action, it goes to the Reducer. (Reducer is a function that takes in 2 parameters: state, action) 

- Reducer: 
    - Inputs:
        - state (from the Store)
        - action (that one that was dispatched)

    - Returns:
        - new state

    Example:
    
    ```js
    reducer (state, action) {
        // logic to make current user ID null (since we logged out!)
        return newState;
    }
    ```

Finally, the newState is sent from the Reducer, back to the Redux Store.

This updates the global state, and the loop continues!

Takeaways:
- Redux is very simple
    - More complexity with advanced features, but easy to add to your application
- Oftentimes: Using Redux is not necessary
    - Smaller projects especially should only be using State
        - Unless Context/State for some reason are not doing the job for you...

#### Recoil

Alternative Library to Redux: Recoil!

Recoil: Centralized subscription based state
- Primary component:
    - Atom: A piece of state that any component can subscribe to
        - Piece of global state that any component can choose to use
- Secondary componenet:
    - Selector: A function for transforming state
        - Works just like Atoms
        - Example: If we have 2 pieces of state, and there is a 3rd piece of state that can be derived, we do the following:
            -  Create a `Selector`
                - Functions that says "How can I convert the 2 pieces of state into a new piece of State? And the function will only run when the 2 pieces of state changes"
                - Essentially: Memoizing a function, that we can use to determine new state, based on other pieces of state

This is tough to understand without an example:

![Recoil](./figures/react/5.png)

Let's say we have 2 pieces of state:
1. State A (Atom)
2. State B (Atom)

We also have some components that rely on the combined state of A/B:
3. State A+B (Selector)
- Derived from State A and State B
    - Whenever State A OR State B changes, State A+B will also change

Let's add a Component tree:
- Root Component
    - Child Left
        - Child 1
        - Child 2
        - Child 3
    - Child Right
        - *no children*
    
Any of these components can subscribe to any of our 3 pieces of State.

Example:
- 2 Components are subscribing to State B 
    - Child Left > Child 3
    - Child Right
- 1 Component is subscribing to State A 
    - Child Left > Child 1
    - Child Right
- 2 Components are subscribing to Selector State A+B
    - Root
    - Child Right

Example: If State B is updated, then both components that share B OR shared A+B, then they would need to re-render

Most Powerful piece: Components don't need to be near each other in the React tree
- You can have any number of Atoms

Takeaways:
- Can be useful
- For smaller projects, no reason to use it
    - Good to understand at a higher level, still!

Note: There are more state management libraries, but Redux and Recoil are the 2 most popular.

#### Data Fetching

Data Fetching: Here are a few libraries that are commonly used. 
- React Query: Hooks for fetching data
    - Deep feature set, such as the following:
        - caching
        - pagination
        - data synchronzation
        - etc.
            - Makes it good for a project with a lot of API requests!

Note: The next 2 are for if you want to integrate GraphQL with React.
- GraphQL > Fetch requests

- Relay: GraphQL client focused on scalability
    - Made by Facebook and React

- Apollo: GraphQL client
    - Similar to Ruby
    - Many think it is easier to get up and running (compared to Relay)

Takeaways: Your choice for these is personal preference!

#### Server Side Rendering (SSR)

SSR's idea comes from an issue that comes in React alot:
- You create these React applications that start with an empty HTML file
- All of the JS needs to run to create the UI
    - Sometimes, in that process, a trip is made to server to download more data for the user
        - Can be inefficient/slow


Server Side Rendering (SSR)
- Render initial page on Server, and send complete HTML to client (How it works: When a user makes a request to a certain page in a React application, the server runs that JavaScript code to generate the HTML)
    - Win: If JavaScript code needs to make more trips to the server, you don't because you are already there and can look it up!
    - Results from this:
        - Better initial loading times
        - Improves SEO/Search Engine Optimziation (pages are complete when bots visit)

Next.js: "A framework for providing React-based web applications with server-side rendering and static website generation."
- Alternative to create-react-app
    - Has built in SSR support
    - Includes a variety of other tools for making applications perform better and be production ready.

#### Static Site Generation

Another alternative to Server Side Rendering: SSG (Static Site Generation)

Static Site Generation: Create static HTML pages at build time for each HTML file possibly needed
- Very similar process, but happens at build time
    - Great for static websites
        - blog
    - Remember: This only works for static pages
        - An application with infinite # of pages based on data, won't work well

- Major benefits over Server side rendering:
    - Less work on server for each request
        - Minimizes time/computation

Gatsby: React-based open source framework with performance, scalability and security built-in.
- Most popular framework for SSG
- Similar to next.js
    - Static site generation is primary use-case
- Supports hybrid models
    - Server Side Rendering + Static site generation

Note: Next.js and Gatsby are both able to do both!

#### Page Routing

Page Routing: Control what components to render based on the URL path
- Many frameworks include this functionality (next.js, gatsby, etc.)
    - If we aren't using these frameworks, we may need a library to do this on the client side in React.

React Router: Library to easily handle routing, declaratively on client-side
- Most popular option
- Adds a few React components to let us render different components based on the route
    - Declarative way
    - React way

- Supports extra features:
    - Page history
    - Reading from it

#### Component Libraries

Component Libraries: Pre-built components to use right away
- Very similar to libraries in CSS crashcourse

- Tons of Component Libraries, such as:

    - Material UI: Based on Material Design System (from CSS)
    - React Bootstrap: Wrapper around Bootstrap, implementing with React
    - Ant Design: Based on Ant Design system

Note: Not too important to know these

#### Other Tools

These are not libraries of frameworks, but are Build Tools that we use to make the development process eaiser!

Other Tools

- Bundlers: Takes lots of files and imports, "Bundles" imports into less files/imports
    - Examples: Webpack, Rollup, Browserity
        - Most support code-splitting with dynamic imports
            - Keeps bundle sizes smaller, as the application scales

- `create-react-app`: The most popular tool for creating, running & building apps 
    - Uses Webpack under the hood

- Vite: Framework agnostic alternative to `create-react-app`
    - People are starting to prefer Vite > `create-react-app`
        - Faster
        - Simpler/more barebones

    - Vite is not specific to React... can build application using Angular and others
    - Ues Rollup under the hood

#### Takeaways

We did not cover every React library, but we did get a good idea of what is out there!

#### Git

```sh
cd algoexpert.io

git status
git add .
git commit -m "Completed Lesson 20 of FrontendExpert's React Course"
git push -u origin main
git status
git log --oneline
q
```

Course is complete!

# Web Dev Fundamentals

I have already completed AlgoExpert's SystemsExpert Course, and upon watching the videos in this Web Dev Fundamentals Crash Course, th
