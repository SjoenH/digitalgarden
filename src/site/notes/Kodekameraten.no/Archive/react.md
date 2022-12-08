---
{"dg-publish":true,"permalink":"/kodekameraten-no/archive/react/"}
---


This is a part of the series "Henry is getting ready for Olavstoppen". You can find the other posts by following the tag "[Getting Ready 4 OT](/tags/getting-ready-4-ot/)".

To learn React I have been following [this React course by Wes Bos](https://reactforbeginners.com/). And the following is mostly my notes and ramblings trying to digest it.

React is, according to [reactjs.org](http://reactjs.org), *"A JavaScript library for building user interfaces."*

<!-- View is the same, you just change what's shown. -->

- [Creating our first Component](#creating-our-first-component)
- [Writing HTML with JSX](#writing-html-with-jsx)
- [Linking up your CSS-file](#linking-up-your-css-file)
- [Passing dynamic data with Props](#passing-dynamic-data-with-props)
- [Routing with React Router](#routing-with-react-router)
- [Helper functions](#helper-functions)
- [Events, Refs and this Binding](#events-refs-and-this-binding)
  - [Events](#events)
  - [Ref and Binding](#ref-and-binding)
- [Rule number 1: Don't touch the DOM.](#rule-number-1-dont-touch-the-dom)
- [State](#state)
  - [Sharing state](#sharing-state)
- [Looping over something (and showing it in the view)](#looping-over-something-and-showing-it-in-the-view)
- [ES6 destructuring assignment](#es6-destructuring-assignment)


# Creating our first Component
Everything is a component.

```jsx
// src/index.js
import React from 'react';

class SomeComponent extends React.Component{
    render(){
        return <p>Hello!</p>
    }
}

```

Every component needs a ``render()`` method.

If we want this to actually render, we need to add some more code
```jsx
// src/index.js
import React from 'react';
import { render } from 'react-dom'; //Since we are building a web-app

class SomeComponent extends React.Component{
    render(){
        return <p>Hello!</p>
    }
}

render(<SomeComponent />, document.querySelector('#main'));
```

Its good practice to put all components in separate files. So...
Let's move our *component* into a folder called *components*. And name it as ``SomeComponent.js``.

```jsx
// src/components/SomeComponent.js
import React from 'react';

class SomeComponent extends React.Component{
    render(){
        return <p>Hello!</p>
    }

    export default SomeComponent;
}
```

Note: We need to import React in this file as well. Worry not; This won't make your application larger when built.
We also need to export our *component* so that other *components* can use it.

And we need to import it in our ``index.js`` file.
```jsx
// src/index.js
import React from 'react';
import { render } from 'react-dom';
import SomeComponent from './components/SomeComponent'; // <- Remember to import it

render(<SomeComponent />,document.querySelector('#main'));
```

# Writing HTML with JSX
When returning HTML, you can only return one element. So you have to wrap siblings into a ``<React.Fragment>`` or a ``<div>``.
Comments need to look like this: ``{/* Comment */}``.
And the comment cannot be first (as a sibling) in a return statement... Because then you would return just the comment. Even the comments need to be wrapped.


```jsx
// src/components/SomeComponent.js
import React from 'react';

class SomeComponent extends React.Component{
    render(){
        return (
            <React.Fragment>
                {/* Comment */}
                <p>Hello!</p>
            </React.Fragment>
        );
    }
    export default SomeComponent;
}
```
> **Disclaimer**: I hope this code works. Haven't checked it since this is mostly for my own learning.

# Linking up your CSS-file
To link your CSS file you just need to import it.

```jsx
// src/index.js
import React from 'react';
import { render } from 'react-dom';
import SomeComponent from './components/SomeComponent'; 
import "./css/style.css"; // <- It's as simple as that!

render(<SomeComponent />,document.querySelector('#main'));
```

# Passing dynamic data with Props

Props is the way we get data into a component.

How do we access the data when passing it as a prop?
There are no preset props, so you can just make up your own. Like ``myRandomProp``.

```jsx
// src/index.js
import React from 'react';
import { render } from 'react-dom';
import SomeComponent from './components/SomeComponent'; 
import "./css/style.css";

render(
    <SomeComponent myRandomProp="HELLO WORLD!"/>,
    document.querySelector('#main')
);
```

Props are kind of an object of data that is sent into a component.
You can also send other types of props, like *bools*:
``myBoolProp = {true}`` or *ints*:``myIntProp = {100}``.

# Routing with React Router

The routing is not baked into react (like in angular), we have to use an external component. 
The two most popular ones are React Router and Next.js.

Let's use React Router for now.
So we make another component and call it ``Router.js`` in our components directory.

```jsx
// src/components/Router.js
import React from "react";
import {BrowserRouter, Route, Switch } from 'react-router-dom';

const Router = () => (
    <BrowserRouter>
        <Switch>
            <Route exact path = "/" component={SomeComponent} />
            <Route exact path = "/store/:storeID" component={SomeOtherComponent} />
            <Route component={NotFoundComponent} />
        </Switch>
    </BrowserRouter>
)
export default Router;
```

```jsx
// src/index.js
import React from 'react';
import { render } from 'react-dom';
import Router from "./components/Router"; // <- Import the router 
// import SomeComponent from './components/SomeComponent'; <- Remove this
import "./css/style.css";

render(
    <Router />,
    document.querySelector('#main')
);
```

# Helper functions
Not something special for React, but it's smart to put your "helper-functions" somewhere logical like a ``helpers.js`` file.

```js
// helpers.js
export default myHelperFunction(){
    return(true);
}
```

# Events, Refs and this Binding

## Events
<!-- SyntheticEvent -->
You can add events to elements by adding it inline ``onClick={this.handleClick}``

```jsx
import React from 'react';

class MyComponent extends React.Component{
    handleClick(){
        alert("Hello World!");
    }
    render(){
        return <button onClick={this.handleClick}>Click Me!</button>
    }

}
```
**Note**: We don't want to write our onClick with "()"s cause that would make the handleClick trigger when mounting the module.
```js
// The wrong way:
<button onClick={this.handleClick()}>Click Me!</button> //<- Wrong! 
// This would make the handleClick trigger on mounting the module.

// The correct way:
<button onClick={this.handleClick}>Click Me!</button> //<- Correct! Do it like this instead!
// Our button will only trigger the handleClick when pressed.
```


## Ref and Binding

The golden rule in react is: "Don't touch the DOM!", so we have to ref stuff by creating a ref in the top of your class and adding a ref-attribute to your element.
```jsx
//NB this will not work
import React from 'react';

class MyComponent extends React.Component{
    myInput = React.createRef();
  
    handleClick(){
        alert("Hello World!");
        console.log(this.myInput); //<- UNDEFINED!
    }
    render(){
        return <input ref={this.myInput} />
    }

}
```
But trying to reach ``this.myInput`` from another method in the same class would not work and just yield *undefined*.
So to circumvent this, we can rebind the ``this`` to point to the same class in the whole class.
We do this in a *Constructor function*

```jsx
import React from 'react';

class MyComponent extends React.Component{
    myInput = React.createRef();
    constructor(){
        super(); // <- We need this
        this.MyComponent = this.MyComponent.bind(this) // This binds the this-scope
    }
    handleClick(){
        alert("Hello World!");
        console.log(this.myInput);
    }
    render(){
        return <input ref={this.myInput} />
    }

}
```

Now we should be able to ref the input, but if we want to ref a lot of stuff, our class would soon be filled with a lot of ``this.MyComponent = this.MyComponent.bind(this)``. 

The solution to this problem is to use a *funky* formatting of our methods that makes the method a property of the class. 
``handleClick = (event) => {``


```jsx
import React from 'react';

class MyComponent extends React.Component{
    myInput = React.createRef();

    handleClick = (event ) => { //<- THIS IS FUNKY!
        alert("Hello World!");
        console.log(this.myInput); // <- We can still reach it!
    }
    render(){
        return <input ref={this.myInput} />
    }

}
```

# Rule number 1: Don't touch the DOM.
We don't want to touch the DOM when writing React apps.
We want to change the data, and then see the DOM react to it.

# State
State is essentially just an object that lives inside a component that stores data that itself needs and maybe also what other components needs.

## Sharing state
We can't pass data up, only down the stream.
Therefore, we need to store stuff that should be shared in a higher component like the Appcomponent.

```jsx
state = {
 fishes:{},
 order:{}
}
```

How do you use a method from Appcomponent in a child-component? The answer is Props!
So let's say we have a method called ``addFish``. Then we cas send it to ``Inventory``-component as a prop like this:

```jsx
// app.js
// Appcomponent
class App extends React.Component{
    state = {
        fishes: {},
        order:{}
    }
    addFish = fish => {
        console.log("Add some fish")
    }
    render(){
        return(
        <Inventory addFish={this.addFish} />
        )
    }
}
```

And then in our ``Inventory``-Component, we can access it through ``this.props.addFish``.

BUT: In order to update our state we want to:

```js
// Take a copy of the existing state. 
// ( We don't want to directly work on the state)
const fishes = {...this.state.fishes}
// Add our new fish to that new fishes variable
fishes[`fish${Date.now()}`]=fish;
// Update our state with the new ``fishes`` object
this.setState({fishes});
```

Note, we don't need to pass our whole state to the ``setState()``-method, only the parts we want to change.
Then ``setState()`` will update our ``state``-object in the current component.

<!-- # Loading data into state onClick -->

# Looping over something (and showing it in the view)
JSX does not have any logic like other template languages... So we need to do it with JavaScript.

```jsx
{Object.keys(this.state.fishes).map(key => <Fish key={key}/>}
```
And relevant data as a prop...
```jsx
{Object.keys(this.state.fishes).map(key => <Fish key={key} details={this.state.fishes[key]} />}
```

# ES6 destructuring assignment
This:
```js
const name = this.props.details.name;
const image = this.props.details.image;
const name = this.props.details.price;
```
Can be replaced with:
```js
const {name, image, price}= this.props.details;
```
[Read more over at MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
