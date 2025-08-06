Subject:

React: is a popular JavaScript library for building reusable, 
component-driven user interfaces for web pages or applications

React is an Open Source view library created and maintained by **Facebook**

React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript.


Because JSX is a syntactic extension of JavaScript, you can actually write JavaScript directly within JSX. 
To do this, you simply include the code you want to be treated as JavaScript within curly braces: 
```
    { 'this is treated as JavaScript code' }
```


However, because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. 
The transpiler **Babel** is a popular tool for this process.


React then uses snapshots of its own DOM to optimize updating only specific parts of the actual DOM.


When no using a **Bundler**
They're used in modern web development to prepare your code for the browser.

Example Code: index.html
```
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8" />
            <title>JSX External File</title>

            <!-- Load React and Babel -->
            <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
            <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
            <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        </head>
        <body>
            <div id="root"></div>
            <script type="text/babel" src="app.js"></script>
        </body>
    </html> 
```
Example Code: app.js
```
    const JSX = <h1>Hello JSX!</h1>;
    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(JSX);
```


One important thing to know about nested JSX is that it must return a **single element**.

This one parent element would wrap all of the other levels of nested elements.

For instance, several JSX elements written as siblings with no parent wrapper element will not transpile.

Example Code: Valid JSX
```
    const JSX =
    <div>
        <p>Paragraph One</p>
        <p>Paragraph Two</p>
        <p>Paragraph Three</p>
    </div>;
```

Example Code: Invalid JSX
```
    const JSX =
    <p>Paragraph One</p>
    <p>Paragraph Two</p>
    <p>Paragraph Three</p>;
```


To put **comments** inside JSX, you use the syntax {/* */} to wrap around the comment text.


Example Code: React 17 and earlier
```
    const JSX = (
    <div>
        <h1>Hello World</h1>
        <p>Lets render this to the DOM</p>
    </div>
    );
    ReactDOM.render(JSX, document.getElementById("challenge-node"))
```


One key **difference** in JSX to HTML is that you can no longer use the word **class** to define HTML classes. 
This is because class is a reserved word in JavaScript. 
Instead, JSX uses **className**.

The naming convention for all HTML attributes and event references in JSX become **camelCase**. 
For example, a click event in JSX is **onClick**, instead of **onclick**. 
Likewise, **onchange** becomes **onChange**


In HTML, almost all tags have both an opening and closing tag: <div></div>; 
the closing tag always has a forward slash before the tag name that you are closing. 

However, there are special instances in HTML called **void elements**, or elements that don’t require both an opening and closing tag before another element can start.

For example the line-break tag can be written 
as <br> or as <br />, but should never be written as <br></br>, since it doesn't contain any content.

Any JSX element can be written with a **self-closing tag**, and every element must be closed. 

The line-break tag, for example, 
must always be written as <br /> in order to be valid JSX that can be transpiled.

A <div>, on the other hand, can be written 
as <div /> or <div></div>. 
The difference is that in the first syntax version there is no way to include anything in the <div />


**Components** are the core of React.
Everything in React is a component


There are two ways to create a React component. 
The first way is to use a **JavaScript function**. 
Defining a component in this way creates a **stateless functional component**.

Think of a stateless component as one that can receive data and render it, but does not manage or track changes to that data


To create a component with a function, you simply write a JavaScript function that returns either **JSX** or **null**. 

One important thing to note is that React requires your function name to begin with a capital letter. 

Example Code: 
```
    const DemoComponent = function() {
        return (
            <div className='customClass' />
        );
    };
```

Example Code: 
```
    const MyComponent = function() {
        return (
            <div>Text</div>
        );
    }
```


The other way to define a React component is with the **ES6 class syntax**. 
Example Code: 
```
    class Kitten extends React.Component {
        constructor(props) {
            super(props);
        }

        render() {
            return (
                <h1>Hi</h1>
            );
        }
    }
```
This creates an ES6 class Kitten which extends the React.Component class 
So the Kitten class now has access to many useful React features, such as **local state** and **lifecycle hooks**

Notice the Kitten class has a **constructor** defined within it that calls super(). 
It uses **super()** to call the constructor of the parent class, in this case React.Component 
The **constructor** is a special method used during the initialization of objects that are created with the class keyword. 
It is best practice to call a component's constructor with super, and pass props to both


To compose components together, you could create an App parent component which renders each of the other components as children. 
To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX.

Example Code: Inside the render method
```
    return (
        <App>
        <Navbar />
        <Dashboard />
        <Footer />
        </App>
    )
```

Example Code: 
```
    const ChildComponent = () => {
        return (
            <div>
                <p>I am the child</p>
            </div>
        );
    };

    class ParentComponent extends React.Component {
        constructor(props) {
            super(props);
        }
        render() {
            return (
                <div>
                    <h1>I am the parent</h1>
                    <ChildComponent />
                </div>
            );
        }
    };
```


**Component composition** is one of React's powerful features 
When you work with React, it is important to start thinking about your user interface in terms of components like the App example. 
You break down your UI into its basic building blocks, and those pieces become the components

Example Code: 
```
    const TypesOfFruit = () => {
        return (
            <div>
                <h2>Fruits:</h2>
                <ul>
                    <li>Apples</li>
                    <li>Blueberries</li>
                    <li>Strawberries</li>
                    <li>Bananas</li>
                </ul>
            </div>
        );
    };
    const Fruits = () => {
        return (
            <div>
                <TypesOfFruit />
            </div>
        );
    };
    class TypesOfFood extends React.Component {
        constructor(props) {
            super(props);
        }
        render() {
            return (
                <div>
                    <h1>Types of Food:</h1>
                    <Fruits />
                </div>
            );
        }
    };
```




React components are passed into root.render() a little differently than JSX elements. 
For JSX elements, you pass in the name of the element that you want to render. 
However, for React components, you need to use the same syntax as if you were rendering a nested component

Example Code: 
```
    const root = ReactDOM.createRoot(targetNode);
    root.render(<ComponentToRender />); 
```
You use this syntax for both ES6 class components and functional components.


Modify the code to run:

class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Fruits:</h2>
        { /* Change code below this line */ }
        <NonCitrus/>
        <Citrus/>

        { /* Change code above this line */ }
      </div>
    );
  }
};

class TypesOfFood extends React.Component {
  constructor(props) {
     super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        { /* Change code below this line */ }
        <Fruits/>
        { /* Change code above this line */ }
        <Vegetables />
      </div>
    );
  }
};
const root = ReactDOM.createRoot(document.getElementById("challenge-node"));
root.render(<TypesOfFood/>);

Output:

Types of Food:
    Fruits:
        Non-Citrus:
            Apples
            Blueberries
            Strawberries
            Bananas
        Citrus:
            Lemon
            Lime
            Orange
            Grapefruit
    Vegetables:
            Brussel Sprouts
            Broccoli
            Squash


In React, you can pass **props**, or properties, to child components. 
Say you have an **App** component which renders a child component called **Welcome** which is a stateless functional component. 
You can pass Welcome a user property by writing:
Example Code:
```
    <App>
        <Welcome user='Mark' />
    </App>
```
The created property user is passed to the component **Welcome**.
Since Welcome is a stateless functional component, it has access to this value 
Example Code:
```
    const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```
It is standard to call this value **props** and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX

Example Code:
```
    const CurrentDate = (props) => {
        return (
            <div>
            <p>The current date is: {props.date}</p>
            </div>
        );
    };
    class Calendar extends React.Component {
        constructor(props) {
            super(props);
        }
        render() {
            return (
            <div>
                <h3>What date is it?</h3>
                <CurrentDate date={Date()}/>
            </div>
            );
        }
    };
```


To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.
Example Code:
```
    <ParentComponent>
        <ChildComponent colors={["green", "blue", "red"]} />
    </ParentComponent>
```

The child component then has access to the array property colors. 
Array methods such as join() can be used when accessing the property.
Example Code:
```
    const ChildComponent = (props) => <p>{props.colors.join(', ')}</p>
```
This will join all colors array items into a comma separated string and produce: 
Example Code:
```
    <p>green, blue, red</p>
```


Example Code:
```
const List = (props) => {
  return <p>{props.tasks.join(", ")}</p>
};
class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        <List tasks={["walk dog", "workout"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["walk dog", "workout", "hike"]}/>
      </div>
    );
  }
};
```


React also has an option to set **default props** 
You can assign default props to a component as a property on the component itself and React assigns the default prop if necessary. 
This allows you to specify what a prop value should be if no value is explicitly provided
Example Code:
```
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};
ShoppingCart.defaultProps = { items: 0 }
```


The way to override the default props is to explicitly set the prop values for a component.
            
Example Code:
```
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={10}/>
  }
};
```


React provides useful type-checking features to verify that components receive props of the correct type.

Here's an example to require the type function for a prop called **handleClick**
Example Code:
```
    MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
```

In the example above, the **PropTypes.func** part checks that handleClick is a function. 

Adding **isRequired** tells React that handleClick is a required property for that component. 

You will see a warning if that prop isn't provided. 

Also notice that **func** represents **function**. 

Among the seven JavaScript primitive types, **function** and **boolean** (written as **bool**) are the only two that use unusual spelling.


**PropTypes** is imported independently from React
Example Code: To Install a dependency
```
npm install prop-types
```
Example Code:
```
    import PropTypes from 'prop-types';
```

Example Code:
```
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};
Items.propTypes = {quantity: PropTypes.number.isRequired}

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```


Anytime you refer to a class component within itself, you use the **this** keyword. 
To access props within a class component, you preface the code that you use to access it with this. 
For example, if an ES6 class component has a **prop** called **data**, you write 
Example Code:
```
    {this.props.data} 
```
in JSX.

Example Code:
```
class App extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
        <div>
            <Welcome name= {"Azarot"}/>
        </div>
    );
  }
};
class Welcome extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
        <div>
          <p>Hello, <strong>{this.props.name}</strong>!</p>
        </div>
    );
  }
};
```

Step 20


















