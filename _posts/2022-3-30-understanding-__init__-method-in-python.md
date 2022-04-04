---
layout: post
title: Understanding __init__ Method in Python
description: Whenever we have Object-Oriented Programming in Python, we mostly come across `__init__` method which we usually don’t fully understand. Today, programmers are bound to come across Object-Oriented Programming (OOP) during their career. As a modern and popular programming language, Python provides all the means to implement the object-oriented philosophy. The `__init__` method is at the core of Object-Oriented Programming and is one of the essential parts to create objects.
date: 2022-3-30 08:00 +08:00
permalink: /post/000004.html
tags: python programming init beginners
read-time: 2
medium-link: https://medium.com/@cycool29/understanding-init-method-in-python-df07f18eddaf
dev-link: https://dev.to/cycool29/understanding-init-method-in-python-3fko
---

___

## Table of Contents

- [What is Object-Oriented Programming?](#what-is-oop)
- [What is `__init__` method?](#what-is-init)
- [Example usecase of `__init__` method](#example-usecase)

___

Whenever we have Object-Oriented Programming in Python, we mostly come across `__init__` method which we usually don’t fully understand. 

Today, programmers are bound to come across Object-Oriented Programming (OOP) during their career. As a modern and popular programming language, Python provides all the means to implement the object-oriented philosophy. The `__init__` method is at the core of Object-Oriented Programming and is one of the essential parts to create objects.


<h2><span id="what-is-oop">What is Object-Oriented Programming? 🧐</span></h2>

Before looking at `__init__`, it's very helpful if we have the idea of what is **Object-Oriented Programming (OOP)**.

Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.

An object is a collection of complex variables and functions and can be used to represent real entities like a button, an airplane, or a person.
To declare, initialize, and manipulate objects in Python, we use classes. They serve as templates from which objects are created. 


<h2><span id="what-is-init">Now the point comes... What is `__init__` method? 🤔</span></h2>

The `__init__` method is a reseved method in Python classes. It is the Python equivalent of the C++ constructor in an object-oriented approach. When you create a new object of a class, Python automatically pass your arguments to the `__init__` method and call it to **initialize** the object’s attributes.
The `__init__` method lets the class initialize the object’s attributes and serves no other purpose. It is **only used within classes**. 


<h2><span id="example-usecase">Example usecase of `__init__` method 💡</span></h2>

Let's see how we can use `__init__` method.

First, we create a `Book` class, with a simple `__init__` method to initialize informations of the book and a function to print the book info.

```python
class Book:
    def __init__(self, title, author, language):
        # Initialize book informations
        self.title = title
        self.author = author
        self.language = language
    def print_book_info(self):
        print(f'Title: {self.title}')
        print(f'Author: {self.author}')
        print(f'Language: {self.language}')
```

Now, we will create an object of the class.

```python
book1 = Book(title='Harry Potter and the Sorcerer Stone', author='JK. Rowling', language='English')
```

When you create the object above, `__init__` method was called and initialized the book infos.
To prove that, let's print the book info.

```python
book1.print_book_info()
```

The output should be:

```
Title: Harry Potter and the Sorcerer Stone
Author: JK. Rowling
Language: English
```

Thanks for reading! 😎