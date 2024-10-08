---
layout: post
title: Pass By Value and Pass By Reference
date: 2024-07-14
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: passingby.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, Java, Software Engineering, Pass By Value, Pass By Reference]
---

 When a variable is passed in a function sometimes its value is changed after the function ends but sometimes it doesn't. Why is that? This confusion is cleared by understanding the two terms that are used to determine the nature of the arguments passed to a function. *Pass by value and pass by reference*. 

## Pass by value
Pass by value means passing only the value, and not the address, of the variable as an argument to a function. It's best understood through an example.

```java
// callee function
void addOne(int num) {
    num = num + 1;
}

// caller function
void main() {
    int n = 10;
    print(n);  // 10
    addOne(n);
    print(n); // 10
}
```

In the above example the variable 'n' is passed as an argument to the 'addOne' function. This function receives the value of that variable and assigns it to a new variable called 'num'. Thus, we have two independent variables with the same value of 10. The value of n won't change regardless of the operation that's performed by function. This is called passing the argument by value. 

So, in this case, the callee and the caller use different variables and if the callee function modifies the parameter variable then the effect is not seen in caller's variable.

## Pass by reference
Pass by reference means passing the reference(value and the address) of the variable as an argument to a function.

```java
// callee function
void addOne(int& num) {
    num = num + 1;
}

// caller function
void main() {
    int n = 10;
    print(n);  // 10
    addOne(n);
    print(n); // 11
}
```

In the above example the reference of the variable 'n' is passed as an argument. This enables the callee function to directly access the variable at passed address in memory and modify its value in place without creating any new variable.

So, in this case, the callee and the caller use the same variable and if the callee function modifies the parameter variable then the effect is seen in caller's variable.

The '&' sign in the parameter of addOne function is used in c++ when one wants to call a function by reference. 

## Pass by value and pass by reference in different languages

Some languages such as c++ and pascal allow users to utilize pass by reference while majority of other mainstream languages such as Java, Python, Javascript, etc, do something a bit more complicated. **They pass primitive types by value and class types by reference**.

So, if you pass a variable of type 'integer' then you are passing by value but if you pass an array or an object then you are passing by reference. But here *pass by reference* means 'Object references are passed by value'. Hence, these languages are said to be exclusively pass by value.

The statement 'Object references are passed by value' has the potential to make you slam your computer and throw it out the window but it can be understood if we look at it in terms of pointers. Pointers in programming are what stores memory addresses and point to the objects/variables in memory. So, when we call a function and pass an object in Java or Python, we are essentially passing an pointer to that object. You can access its value inside the function, manipulate it i.e append or change a value in case of an array, but you can't change its address because it is a pointer/reference and not the actual address itself.

Have a look at this piece of code

```python
mylist = [1,2]

def add(mylist):
    mylist.append(3)

add(mylist)

mylist /// [1,2,3]
```

Here the function will receive the same object as the caller but it will not receive the variable. Instead, it will provide its own variable and store the value in it. Both the function and the caller point to the same object in memory and so when a change is made inside the function it is reflected in caller too. Both posses the same object but with different variable names, just like it was in *pass by value* and that's the reason these languages are called strictly *pass by value*.

In *pass by reference* the same variable is passed into the function and when the variable inside the function is reassigned the same can be observed in the caller's variable.

It helps to visualize a variable as a box and the object as a value that's situated inside the box. In Java and Python where *object references are passed as value*, the function creates its own box and places the parameter value in it. Thus, we have two seperate boxes but both of them contain the same object.  

## Conclusion

- Pass by value: Function and caller possess and act on seperate variables

- Pass by reference: Function and caller both possess and act on the same variable.

- Object references passed by value: Function and caller possess different variables but act on the same objects.


## Useful Links

- [For Java](https://www.javadude.com/articles/passbyvalue.html)
- [For Python](https://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/)
- [A follow up on Stack Overflow](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value)
