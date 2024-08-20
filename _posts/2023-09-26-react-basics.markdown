---
layout: post
title: React Basics for Beginner/Intermediate Developers
date: 2024-06-08
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: ReactCover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [React js, Javascript, Frontend]
---


React is a Javascript library that is used to create interactive User Interfaces. The main principle of React is to divide your webpage into reusable components that can interact with each other when need be.

Have a look at the image below.

![React Components Example]({{site.baseurl}}/assets/img/react-components.png)

This is an expense tracker app that I built as a part of a tutorial I did while learning React. This is a simple application that tracks your expenses but as you can see each functionality has its own component. This way if I want to display the balance at another part of my app then I can just use the Balance Component again. Components allow to think of each piece of your application in isolation.

But before we get into Components, let's have a look at what components are made of.

## React Elements & JSX

Anytime you are working on a React application there will be an HTML file with a div tag that has an id of 'root'. This is where your whole application is placed and is updated whenever there's any change.

```javascript
const element = <h1>Hello World!!</h1>

ReactDOM.render(element, document.getElementById('root'));
```

The first line of the above block is a 'React Element'. This special syntax is called JSX(Javascript Syntax Extension). JSX is used by React so we don't have to seperate out our core logic from our UI logic. JSX produces React Elements and that is what gets displayed on the screen when ReactDOM renders it. (ReactDOM is what maintains and updates the DOM so we don't have to)

To use javascript expressions we just need to wrap it inside a curly bracket.

React Elements are essentially just plain javascript objects that are referenced by the ReactDOM before creating/updating the DOM.

```javascript
// Note: this is a simplified example
const element = {
  type: 'h1',
  props: {
    children: 'Hello World!!'
  }
};
```


## Components

```javascript
const Welcome = ()  => {
    return <h1>Hello World!!</h1>
}

const element = <Welcome />
ReactDOM.render(element, document.getElementById('root'));
```

Components are just javascript functions that can be used anywhere in your application. But we don't need to call these functions explicitly. Whenever we want to use them we need to put them in a tag and React will call it for us. (One simple rule is that the first letter has to in uppercase for React to identify it as user-defined component)

## Props

Now what if you wanted to pass some data to the Welcome component? What if I wanted it to return 'Hello, <name>' instead of 'Hello World'?

For this, we use props. 
  
```javascript
const Welcome = (props)  => {
    return <h1>Hello, {props.name}</h1>
}

const element = <Welcome name="John" />
ReactDOM.render(element, document.getElementById('root'));
```
 
When React sees an attribute in any user-defined component such as the Welcome component in this case it passes an object to this component. This component is called props. 

So, we access this object with the 'props' keyword and use the 'name' key in this case to display the name.
  
## React Hooks

So far we have only been dealing with "Stateless Components" i.e components that don't have any "state". State is what React uses to update the UI whenever it notices any change in the component. We use state whenever we need to update the UI based on a certain condition and this makes our component "Stateful". We can use state in our components using the "useState" hook which is the only way you can use state in a function component. 
  
Hooks are javascript functions that let us use state and other React features without writing a class. 
  
### useState

```javascript
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

This is a simple example of a component that has a button which updates the value of the count variable by 1 when clicked. React re-renders the component everytime the state changes which in this case happens every time the button is clicked. 

First, we import the useState hook and initialize it inside our component. This hook returns a state variable and a function to update the state and hence, we use array destructuring to receive the pair. The only argument to the useState function is the initial state of our variable which in this case is 0 since our counter starts at 0. We use the "setCount" function to set the value of count. 
  
State is a critical part of any React app and is tremendously helpful when we want to update the UI based on some condition.
  
There are many hooks such as useEffect, useContext, useNavigate, etc., with each serving a unique purpose. More can be read about hook here [Hooks](https://reactjs.org/docs/hooks-intro.html)
  
  
## Conclusion

The concepts described above are crucial to understand for any developer who wants to build meaningful projects using React. Of course, there's a huge difference between understanding a topic and actually implementing it so you should aim to implement what you have learned in order to solidified your understanding of the topic.
  
## Further Resources
  
[React docs](https://reactjs.org/docs/hello-world.html) - Official documentation of React


  
