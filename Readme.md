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
        <NonCitrus/>
        <Citrus/>
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
        <Fruits/>
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
You can pass **Welcome** a user property by writing:
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
To access props within a class component, you preface the code that you use to access it with **this**. 
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
            <Welcome name= {"Azrel"}/>
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


A **stateless functional component** is any function you write which accepts props and returns JSX. 

A **stateless component**, on the other hand, is a class that extends React.Component, but does not use internal state 

A **stateful component** is a class component that does maintain its own internal state


A common pattern is to try to minimize **statefulness** and to create **stateless functional components** wherever possible. 

This helps contain your state management to a specific area of your application. 

In turn, this improves **development** and **maintenance** of your app by making it easier to follow how changes to state affect its behavior


**State** consists of any data your application needs to know about, that can change over time. 
You want your apps to respond to state changes and present an updated UI when necessary. 

You create state in a React component by declaring a state property on the component class in its **constructor**. 

This initializes the component with state when it is created. 

The state property must be set to a **JavaScript object**.
Example Code:
```
  this.state = {

  }
```

You have access to the state object throughout the life of your component. 

You can update it, render it in your UI, and pass it as props to child components. 

Note that you must create a class component by extending React.Component in order to create state like this.

Example Code:
```
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {firstName: "Crow"}
  }
  render() {
    return (
      <div>
        <h1>{this.state.firstName}</h1>
      </div>
    );
  }
};
```


If a component is stateful, it will always have access to the data in state in its render() method. 

You can access the data with **this.state**

If you want to access a state value within the return of the render method, you have to enclose the value in curly braces.

State allows you to track important data in your app and render a UI in response to changes in this data. 

If your data changes, your UI will change. 

React uses what is called a **virtual DOM**, to keep track of changes behind the scenes


Note that if you make a component stateful, no other components are aware of its state. 

Its state is completely encapsulated, or local to that component, unless you pass state data to a child component as props


There is **another way** to access state in a component. 

In the render() method, before the return statement, you can write JavaScript directly. 

For example, you could declare functions, access data from **state** or **props**, perform computations on this data, and so on. 

Then, you can assign any data to variables, which you have access to in the return statement.

Example Code:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{name}</h1>
      </div>
    );
  }
};
```


React provides a method for updating component **state** called **setState**

You call the setState method within your component class like so: **this.setState()**, passing in an object with key-value pairs

The **keys** are your state **properties** and the **values** are the updated state **data**. 

For instance, if we were storing a username in state and wanted
to update it, it would look like this:

Example Code:
```
  this.setState({
    username: 'Lewis'
  });
```

Example Code:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({ name: "React Rocks!"})
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```


A class method typically needs to use the **this** keyword so it can access properties on the class (such as state and props) inside the scope of the method. 

There are a few ways to allow your class methods to access this.

One common way is to explicitly **bind this** in the constructor so **this** becomes bound to the class methods when the component is initialized.


Sometimes you might need to know the previous state when updating the state. 

However, state updates may be **asynchronous** - this means React may batch multiple setState() calls into a single update. 

This means you **can't rely** on the previous value of **this.state** or **this.props** when calculating the next value. 

Example Code: Should not use code like this
```
  this.setState({
    counter: this.state.counter + this.props.increment
  });
```

Instead, you should pass setState a **function** that allows you to access state and props. 

Using a function with setState guarantees you are working with the most **current values** of **state** and **props**

Example Code: Should be rewritten as
```
  this.setState((state, props) => ({
    counter: state.counter + props.increment
  }));
```

Example Code: if only state is need it
```
  this.setState(state => ({
    counter: state.counter + 1
  }));
```

Note that you have to wrap the object literal in parentheses, otherwise JavaScript thinks it's a block of code


Example Code:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    this.toggleVisibility = this.toggleVisibility.bind(this);
  }
  toggleVisibility() {
    this.setState(state => ({
      visibility: !state.visibility
    }));
  }
  render() {
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
}
```


Example Code: Counter
```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
    this.reset = this.reset.bind(this);
  }
  increment() {
    this.setState(state => ({count: state.count + 1}))
  }
  decrement() {
    this.setState(state => ({count: state.count - 1}))
  }
  reset() {
    this.setState({count: 0})
  }
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```

**Form control elements** for text input, such as ***input*** and **textarea**, maintain their own state in the DOM as the user types. 

With React, you can move this mutable state into a React component's state. 

This applies to other form elements as well, including the regular HTML **form** element.

The **user's input** becomes part of the application state, so React controls the value of that input field

Example Code:
```
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this)
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    })
  }
  render() {
    return (
      <div>
        <input value={this.state.input} onChange={this.handleChange}></input>
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```


Example Code:
```
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    this.setState(state => ({
      submit: state.input
    }));
    event.preventDefault()
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <input value={this.state.input} onChange={this.handleChange}></input>
          <button type='submit'>Submit!</button>
        </form>
        <h1>{this.state.submit}</h1>
      </div>
    );
  }
}
```


A **common pattern** is to have a stateful component containing the **state** important to your app, that then renders child components. 

You want these components to have access to some pieces of that **state**, which are passed in as **props**.


For example, maybe you have an **App** component that renders a **Navbar**, among other components. 

In your **App**, you have **state** that contains a lot of **user information**, but the **Navbar** only needs access to the **user's username** so it can display it. 

You pass that piece of state to the **Navbar** component as a **prop**.


This pattern illustrates some important paradigms in React. 

The first is **unidirectional** data flow. 

**State** flows in one direction down the tree of your application's components, from the **stateful parent** component to **child components**. 

The child components only receive the state data they need. 

The second is that **complex stateful apps** can be broken down into just a few, or maybe a **single**, stateful component. 

The rest of your components simply receive state from the parent as **props**, and render a UI from that state. 

It begins to create a separation where **state management** is handled in one part of code and **UI rendering** in another


Example Code:
```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar name= {this.state.name}/>
       </div>
    );
  }
};
class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: {this.props.name}</h1>
    </div>
    );
  }
};
```


You can also pass **handler functions** or any method that's defined on a React component to a child component. 

This is how you allow child components to interact with their parent components. 

You pass methods to a child just like a regular **prop**. 

It's assigned a name and you have access to that method name under **this.props** in the child component.

Example Code:
```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        <GetInput input={this.state.inputValue} handleChange={this.handleChange}/>
        <RenderInput input={this.state.inputValue}/>
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```


React components have several **special methods** that provide opportunities to perform actions at specific points in the lifecycle of a component. 

These are called **lifecycle methods**, or **lifecycle hooks**, and allow you to catch components at certain points in time.

This can be **before** they are **rendered**, before they **update**, before they **receive props**, before they **unmount**, and so on

Here is a list of some of the main lifecycle methods: **componentWillMount()** 
**componentDidMount()** 
**shouldComponentUpdate()** 
**componentDidUpdate()** 
**componentWillUnmount()**


The **componentWillMount()** method is called before the **render()** method when a component is being mounted (rendered to the DOM for the first time) to the DOM


Replacement **componentDidMount()**

This method is called **after** a component is mounted to the DOM.

Any calls to setState() here will trigger a **re-rendering** of your component. 

When you call an **API** in this method, and set your state with the data that the API returns, it will automatically trigger an update once you receive the data.

Example Code:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: {this.state.activeUsers}</h1>
      </div>
    );
  }
}
```


The **componentDidMount()** method is also the best place to attach any event listeners you need to add for specific functionality. 

React provides a **synthetic event system** which wraps the native event system present in browsers. 

This means that the **synthetic event system** behaves exactly the same regardless of the user's browser - even if the native events may behave differently between different browsers.

Some of these **synthetic event** handlers such as **onClick()**

Example Code:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      message: ''
    };
    this.handleEnter = this.handleEnter.bind(this);
    this.handleKeyPress = this.handleKeyPress.bind(this);
  }
  componentDidMount() {
    document.addEventListener("keydown", this.handleKeyPress);
  }
  componentWillUnmount() {
    document.removeEventListener("keydown", this.handleKeyPress);
  }
  handleEnter() {
    this.setState((state) => ({
      message: state.message + 'You pressed the enter key! '
    }));
  }
  handleKeyPress(event) {
    if (event.keyCode === 13) {
      this.handleEnter();
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
};
```

It's good practice to use this lifecycle method to do any clean up on React components before they are unmounted and destroyed. 

Removing event listeners is an example of one such clean up action.


React provides a lifecycle method you can call when child components receive new **state** or **props**, and declare specifically if the components should update or not. 

The method is **shouldComponentUpdate()**, and it takes **nextProps** and **nextState** as parameters.

The default behavior is that your component **re-renders** when it receives new props, even if the props haven't changed. 

You can use **shouldComponentUpdate()** to prevent this by comparing the props

The method must return a boolean value that tells React whether or not to update the component. 

You can compare the current props (**this.props**) to the next props (**nextProps**) to determine if you need to update or not, and return **true** or **false** accordingly.

Example Code:
```
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log('Should I update?');
    if(nextProps.value%2===0){
      return true;
    } else {
      return false;
    }
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return <h1>{this.props.value}</h1>;
  }
}
class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState(state => ({
      value: state.value + 1
    }));
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value} />
      </div>
    );
  }
}
```


How to style those JSX elements you create in React?

You likely know that it won't be exactly the same as working with HTML because of the way you apply classes to JSX elements
**className**

If you import styles from a stylesheet, it isn't much different at all. 

You apply a class to your JSX element using the **className** attribute, and apply styles to the class in your stylesheet. 

Another option is to apply **inline styles**, which are very common in ReactJS development.

Example Code: of an inline style in HTML
```
  <div style="color: yellow; font-size: 16px">Mellow Yellow</div>
```

JSX elements use the style attribute, but because of the way JSX is transpiled, you can't set the value to a string. 

Instead, you set it equal to a **JavaScript object**

Example Code: of an inline style in JSX
```
  <div style={{color: "yellow", fontSize: 16}}>Mellow Yellow</div>
```

Example Code:
```
  class Colorful extends React.Component {
    render() {
      return (
        <div style={{color: 'red', fontSize:72}}>Big Red</div>
      );
    }
  };
```


All property value length units (like height, width, and fontSize) are assumed to be in px unless otherwise specified. 

If you want to use em, for example, you wrap the value and the units in quotes, like **{fontSize: "4em"}**

If you have a large set of styles, you can assign a **style object** to a **constant** to keep your code organized

Example Code:
```
  const styles = {color: "purple", border: "2px solid purple", fontSize: 40} 
  class Colorful extends React.Component {
    render() {
      return (
        <div style={styles}>Style Me!</div>
      );
    }
  };
```


You can also write JavaScript directly in your **render** methods, before the **return** statement, without inserting it inside of curly braces.


Example Code: Magic Eight Ball toy
```
  const inputStyle = {
    width: 235,
    margin: 5
  };

  class MagicEightBall extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        userInput: '',
        randomIndex: ''
      };
      this.ask = this.ask.bind(this);
      this.handleChange = this.handleChange.bind(this);
    }
    ask() {
      if (this.state.userInput) {
        this.setState({
          randomIndex: Math.floor(Math.random() * 20),
          userInput: ''
        });
      }
    }
    handleChange(event) {
      this.setState({
        userInput: event.target.value
      });
    }
    render() {
      const possibleAnswers = [
        'It is certain',
        'It is decidedly so',
        'Without a doubt',
        'Yes, definitely',
        'You may rely on it',
        'As I see it, yes',
        'Outlook good',
        'Yes',
        'Signs point to yes',
        'Reply hazy try again',
        'Ask again later',
        'Better not tell you now',
        'Cannot predict now',
        'Concentrate and ask again',
        "Don't count on it",
        'My reply is no',
        'My sources say no',
        'Most likely',
        'Outlook not so good',
        'Very doubtful'
      ];
      const answer = possibleAnswers[this.state.randomIndex]; 
      return (
        <div>
          <input
            type='text'
            value={this.state.userInput}
            onChange={this.handleChange}
            style={inputStyle}
          />
          <br />
          <button onClick={this.ask}>Ask the Magic Eight Ball!</button>
          <br />
          <h3>Answer:</h3>
          <p>
            {answer}
          </p>
        </div>
      );
    }
  }
```


Another application of using JavaScript to control your rendered view is to tie the elements that are rendered to a **condition**

When the condition is **true**, one view renders. 
When it's **false**, it's a different view.

Example Code:
```
  class MyComponent extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        display: true
      }
      this.toggleDisplay = this.toggleDisplay.bind(this);
    }
    toggleDisplay() {
      this.setState((state) => ({
        display: !state.display
      }));
    }
    render() {
      if(this.state.display){
        return (
        <div>
          <button onClick={this.toggleDisplay}>Toggle Display</button>
          <h1>Displayed!</h1>
        </div>
      );
      } else {
        return (
        <div>
          <button onClick={this.toggleDisplay}>Toggle Display</button>
        </div>
      );
      }
    }
  };
```


If you write a lot of else if statements to return slightly different UIs, you may repeat code which leaves room for error

Instead, you can use the **&& logical operator** to perform conditional logic in a more concise way. 

This is possible because you want to check if a condition is true, and if it is, return some markup.

Example Code:
```
  {condition && <p>markup</p>}
```

If the condition is **true**, the markup will be returned. 

If the condition is **false**, the operation will immediately return false after evaluating the condition and return **nothing**

Example Code: && logical operator
```
  class MyComponent extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        display: true
      }
      this.toggleDisplay = this.toggleDisplay.bind(this);
    }
    toggleDisplay() {
      this.setState(state => ({
        display: !state.display
      }));
    }
    render() {
      return (
        <div>
          <button onClick={this.toggleDisplay}>Toggle Display</button>
          {this.state.display && <h1>Displayed!</h1>}
        </div>
      );
    }
  };
```


The **ternary operator** is often utilized as a shortcut for if/else statements in JavaScript.

**Ternary expressions** can be an alternative if you want to implement conditional logic **within** your JSX. 

Recall that a ternary operator has three parts, you can combine several ternary expressions together.

Example Code: basic syntax
```
  condition ? expressionIfTrue : expressionIfFalse;
```

Example Code: CheckUserAge
```
  const inputStyle = {
    width: 235,
    margin: 5
  };
  class CheckUserAge extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        input: "",
        userAge: ""
      };
      this.submit = this.submit.bind(this);
      this.handleChange = this.handleChange.bind(this);
    }
    handleChange(e) {
      this.setState({
        input: e.target.value,
        userAge: ''
      });
    }
    submit() {
      this.setState(state => ({
        userAge: state.input
      }));
    }
    render() {
      const buttonOne = <button onClick={this.submit}>Submit</button>;
      const buttonTwo = <button>You May Enter</button>;
      const buttonThree = <button>You Shall Not Pass</button>;
      return (
        <div>
          <h3>Enter Your Age to Continue</h3>
          <input
            style={inputStyle}
            type='number'
            value={this.state.input}
            onChange={this.handleChange}
          />
          <br />
          {this.state.userAge === "" ? buttonOne : this.state.userAge < 18 ? buttonThree : buttonTwo}
          </div>
      );
    }
  }
```


Example Code: 50/50 game
```
  class Results extends React.Component {
    constructor(props) {
      super(props);
    }
    render() {
      return this.props.fiftyFifty ? <h1>You Win!</h1> : <h1>You Lose!</h1>;
    }
  }
  class GameOfChance extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        counter: 1
      };
      this.handleClick = this.handleClick.bind(this);
    }
    handleClick() {
      this.setState(prevState => {
        return {
          counter: prevState.counter + 1
        }
      });
    }
    render() {
      const expression = Math.random() >= .5;
      return (
        <div>
          <button onClick={this.handleClick}>Play Again</button>
          <Results fiftyFifty= {expression}/>
          <p>{'Turn: ' + this.state.counter}</p>
        </div>
      );
    }
  }
```


You can also **render CSS conditionally** based on the state of a React component. 

To do this, you check for a condition, and if that condition is met, you modify the styles object that's assigned to the JSX elements in the render method.

Example Code: CSS with conditionals
```
  class GateKeeper extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        input: ''
      };
      this.handleChange = this.handleChange.bind(this);
    }
    handleChange(event) {
      this.setState({ input: event.target.value })
    }
    render() {
      let inputStyle = {
        border: '1px solid black'
      };
      this.state.input.length > 15 ? inputStyle = {border: '3px solid red'} : inputStyle
      return (
        <div>
          <h3>Don't Type Too Much:</h3>
          <input
            type="text"
            style={inputStyle}
            value={this.state.input}
            onChange={this.handleChange} />
        </div>
      );
    }
  };
```


Often in reactive programming, a programmer has no way to know what the state of an application is until runtime, because so much depends on a user's interaction with that program. 

Programmers need to write their code to correctly handle that unknown state ahead of time. 

Using Array.map() in React illustrates this concept.

Example Code:
```
  const textAreaStyles = {
    width: 235,
    margin: 5
  };

  class MyToDoList extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        userInput: '',
        toDoList: []
      }
      this.handleSubmit = this.handleSubmit.bind(this);
      this.handleChange = this.handleChange.bind(this);
    }
    handleSubmit() {
      const itemsArray = this.state.userInput.split(',');
      this.setState({
        toDoList: itemsArray
      });
    }
    handleChange(e) {
      this.setState({
        userInput: e.target.value
      });
    }
    render() {
      const items = this.state.toDoList.map((e,i) => <li key={i}>{e}</li>);
      return (
        <div>
          <textarea
            onChange={this.handleChange}
            value={this.state.userInput}
            style={textAreaStyles}
            placeholder='Separate Items With Commas'
          />
          <br />
          <button onClick={this.handleSubmit}>Create List</button>
          <h1>My "To Do" List:</h1>
          <ul>{items}</ul>
        </div>
      );
    }
  }
```


When you create an array of elements, each one needs a key attribute set to a unique value. 

React uses these keys to keep track of which items are added, changed, or removed. 

This helps make the re-rendering process more efficient when the list is modified in any way.

Keys only need to be unique between sibling elements, they don't need to be globally unique in your application.

Example Code:
```
  const frontEndFrameworks = [
    'React',
    'Angular',
    'Ember',
    'Knockout',
    'Backbone',
    'Vue'
  ];
  function Frameworks() {
    const renderFrameworks = frontEndFrameworks.map((e, i) => <li key={i}>{e}</li>);
    return (
      <div>
        <h1>Popular Front End JavaScript Frameworks</h1>
        <ul>
          {renderFrameworks}
        </ul>
      </div>
    );
  };
```


Another method related to map is **filter**, which filters the contents of an array based on a condition, then returns a new array. 

For example, if you have an array of users that all have a property online which can be set to true or false, you can filter only those users that are online by writing:

Example Code:
```
  let onlineUsers = users.filter(user => user.online);
```

Example Code:
```
  class MyComponent extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        users: [
          {
            username: 'Jeff',
            online: true
          },
          {
            username: 'Alan',
            online: false
          },
          {
            username: 'Mary',
            online: true
          },
          {
            username: 'Jim',
            online: false
          },
          {
            username: 'Sara',
            online: true
          },
          {
            username: 'Laura',
            online: true
          }
        ]
      };
    }
    render() {
      const usersOnline = this.state.users.filter(user => user.online); // Change this line
      const renderOnline = usersOnline.map((e,i) => <li key={i}>{e.username}</li>); // Change this line
      return (
        <div>
          <h1>Current Online Users:</h1>
          <ul>{renderOnline}</ul>
        </div>
      );
    }
  }
```


So far, you have been rendering React components on the client. 

Normally, this is what you will always do. 

However, there are some use cases where it makes sense to render a React component on the **server**. 

Since React is a JavaScript view library and you can run JavaScript on the server with **Node**, this is possible. 

In fact, React provides a **renderToString()** method you can use for this purpose.

There are **two key reasons** why rendering on the server may be used in a real world app. 

**First**, without doing this, your React apps would consist of a relatively **empty HTML file** and a large bundle of JavaScript when it's initially loaded to the browser. 

This may not be ideal for search engines that are trying to index the content of your pages so people can find you. 

If you render the initial HTML markup on the server and send this to the client, the initial page load contains all of the page's markup which can be crawled by search engines. 

**Second**, this creates a faster initial page load experience because the rendered HTML is smaller than the JavaScript code of the entire app. 

React will still be able to recognize your app and manage it after the initial load.

Example Code:
```
  class App extends React.Component {
    constructor(props) {
      super(props);
    }
    render() {
      return <div/>
    }
  };
  ReactDOMServer.renderToString(<App/>);
```

