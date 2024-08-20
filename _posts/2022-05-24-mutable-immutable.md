---
layout: post
title: Mutable and Immutable Objects in Python
date: 2024-08-15
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: changing.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python]
---

Python is an object-oriented programming language, and in Python, everything is an object.

It is necessary to understand what the above statements mean before we dive into the mutability and immutability of objects. So, let's begin.

## Everything in Python is an object

Let's take a variable x and initialize with a number 2.

![first image]({{site.baseurl}}/assets/img/jupyter1.jpg)

Now in most languages, variables are viewed as containers or buckets that contain all the data but in Python, it helps if we view them as pointers. Here, a pointer x points to some container in the memory that holds the number 2. Hence, we are not just creating a variable x but we are also creating an object with the value 2. This object contains its own attributes, methods, type and a unique id to identify it.

Similarly, we can create a list and an object of this list will get created along with some metadata(attributes), and associated functionality(methods).

![third image]({{site.baseurl}}/assets/img/jupyter3.jpg)

Thus, in languages like Python, every object is an entity and every entity will contain the data along with some metadata and some associated functionality.

## Immutable Objects

Immutable objects are those that can't be changed once they've been created. Consider the following scenario.

I create a variable **x** and assign it with the number 2. I create a variable **y** and assign it with the same variable **x**. 

![fourth image]({{site.baseurl}}/assets/img/jupyter4.jpg)

Both **x** and **y** have the same id which means they are pointing to the same object in memory. But if I increase the value of **x** by 5 will I see a similar result in **y**?

![fifth image]({{site.baseurl}}/assets/img/jupyter5.jpg)

Nope. This is because in Python any object of type "int" is immutable and so when we increased the value of **x** by 5 we didn't increase the value of the object **2**, rather we created a new object in memory with the value "7" and made **x** point to this newly created object. The variable **y** is still pointing to the object with value "2". And **x**'s id has also changed which indicates that **x** is now pointing to another object in memory while **y**'s hasn't. Remember, variables in python should be best viewed as pointers.

Objects of built-in types like (int, float, bool, str, tuple, unicode) are immutable.

## Mutable Objects

Mutable objects are those that can be changed once they've been created. Consider the following scenario.

I create a variable **list1** and assign it with a list "[1,2,3]". I then create a variable **list2** and assign list1 to it.

![sixth image]({{site.baseurl}}/assets/img/jupyter6.jpg)

Similar to variables **x** and **y**, both **list1** and **list2** have the same id. Now, if I push a number to list1, will I see the same in list2?

![seventh image]({{site.baseurl}}/assets/img/jupyter7.jpg)

We do see the change in **list2** and that's because any object of type "list" is mutable. Hence, when we pushed 4 in **list1** the change took place in the list object itself, unlike what happened with the object of type "int" where a new object got created. And we see a change in **list2** since it's also pointing to the same object. To check if a new object has been created or not always check its id. Here, even after the addition of 4, both the lists' ids haven't changed which indicates that they are still pointing to the original object.

Objects of built-in types like (list, set, dict) are mutable.

## Conclusion

The knowledge about mutability and immutability of objects comes in handy when we have to pass objects to functions. As in Python, **Objects references are passed as values** how do you determine whether the variable that you are passing to a function will get altered or not? We can follow this general rule:

- If the variable is immutable, i.e., of type int, str, etc., then the function won't be able to alter its value.
- If the variable is mutable, i.e., of type list, dict, etc., then the function can alter its value.
