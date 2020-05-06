# LNT Tutorial - Learning the Basics of React With A Basic Clock!

### A little about React
React is a JavaScript front-end library, originally created by Facebook. React is used for creating dynamic user interfaces that allow for interaction between various parts of the UI without having to reload the page. While it is not a full-fledged framework like Laravel, React is a very powerful tool and can be used to (relatively) simply make a UI that would otherwise be very complex. By using "components", React allows for the UI to be built into building blocks for easy abstraction. It's lightweight, fast and runs on Node so it can easily integrate into a larger JavaScript environment.

## Some Basics

### 1. Introducing JSX
JSX is an extension of JavaScript that allows us to use HTML like code in our components. 
An example of JSX looks like this 
`<h1> Hello, {name}</h1>`
You can see we have what looks like HTML, but there is also a JavaScript variable inside. 

### 2. Rendering Components
Most React apps have one root DOM node (the thing that is visible in browser source). Everything is then managed by React DOM (the virtual DOM). The React DOM then manages what shows up on the screen.

Example: 
```
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```

### 3. Components and Props
The UI can be split into individual components where they can act as building blocks for an interface. Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. Props (properties) is the data that a component passes or has passed to it. Components may never modify their own props. Components can be functions or class based (functional components/class components). 

Example of a class based component:
```
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

### 4. State and Lifecycle
State allows for a component to be completely encapsulated and it allows the component to be able to manage its own state/props (local state). Lifecycle allows for the virtual DOM to manage resources when a component is created (mounted) and destroyed (unmounted).

## Building our app

### Getting Started
1. Download NodeJS if it is not already installed on your computer. 
2. Once Node is installed, open the command line/terminal. 
3. To create a new react-project, run `npx create-react-app appName`. appName can be anything you would like.
4. `cd appName` and then `npm start`, this will start up the basic react app. 
5. Open up the apps code in your favorite IDE


### Cleaning Up Our App
In src/App.js, delete all of the boiler code so you're left with this:
```
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
      
    </div>
  );
}

export default App;
```

### Creating the Clock Component
1. Create a new file in the src folder called Clock.js
2. Import React so it can be used `import React from 'react';`
3. Create the class component. Refer to the example above. 
4. Add a constructor method. This will allow us to use state and props.
```
constructor(props) {
      super(props);
      this.state = {date: new Date()};
    }
```
5. Add our lifecycle methods, `componentDidMount()` and `componentWillUnmount()`
Since we are making a clock, we need to update every second. We can use the built in JavaScript method `setInteraval` in our mount method
```
this.timerID = setInterval(
        () => this.tick(),
        1000
      );
```
6. Create the `tick()` function. This is where we modify our state. We can get a new JavaScript `date()` every time this method is called and set it to the state variable `date`. Notice we use `this.setState` instead of something like `state = date`. Using `this.setState` is the proper way to update state in React. They make a big deal about it but don't get into much detail as to why...
```
this.setState({
        date: new Date()
      });
```
7. Let's render our component! You can use a variety of HTML tags to make your component all pretty such as `<h1>` or `<p>` or whatever you would like. The important thing is we just need to display our state `{this.state.date.toLocaleTimeString()}` with JSX. Doesn't this look familiar to what we saw in "Introducing JSX"?
Here's the barebones of our `render()` function if you need help
```
render() {
      return (
        <div>
          //Put some code here
        </div>
      );
    }
```
8. Add `export default Clock;` at the bottom of the file to export the class. 

### Using the Clock component the App
1. In src/App.js, import the Clock component `import Clock from '.../Clock.js';`
2. In the App's render function, use JSX to add a component `<Clock />`
