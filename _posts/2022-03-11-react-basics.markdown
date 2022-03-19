---
layout: post
title: React Basics for Beginner/Intermediate Developers
date: 2022-03-19
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
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
  
## Conclusion

The concepts described above are crucial to understand for any developer who wants to build meaningful projects using React. Of course, there's a huge difference between understanding a topic and actually implementing it so you should aim to implement what you have learned in order to solidified  your understanding of the topic.
  
## Further Resources
  
[React docs](https://reactjs.org/docs/hello-world.html) - Official documentation of React


  
