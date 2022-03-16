---
layout: post
title: Get started to Python GUI programming with PySimpleGUI
description: 
date: 2022-3-15 19:00 +08:00
permalink: /post/000004.html
tags: tutorial beginners python gui
read-time: 5
---

---

## Table of Contents

- [What is GUI?](#what-is-gui)


---

There are many Python GUI toolkit which let you create nice GUI applications. But I would like to use PySimpleGUI as a beginning toolkit of Python GUI programming.

The reason is in its name - **simple**. 

In this blog post, I will teach you guys to make a **pretty simple but fully functional YouTube Video downloader GUI**, with **PySimpleGUI**.


<h2><span id="what-is-gui">Wait a minute... What is GUI?</span></h2>

GUI is a acronym of **Graphical User Interface**.

A GUI application simplifies how users use their computer. Unlike CLI programmes, users won't need a good memory to remember a bunch of commands. With a few clicks, users can copy files to another directory, chat with others easily, and see nice web content. For example, menus, icons, tabs, pointers and graphs are shown to a user in GUI so that users can conveniently select one of them. 

GUI uses visual elements to represent those now hidden lines of command. Users can simply select a button or an icon to call specific function. The easy use of GUIs has made it possible for the public in general, regardless of experience or knowledge, to access all kinds of systems for everyday-use.


<h2><span id="why-pysimplegui">Why should we use PySimpleGUI?</span></h2>

Now the question comes - there are soooo many Python GUI toolkits like tkinters, pyqt, wxpython... Why should we use PySimpleGUI?

The only reason is as its name suggests - it is *very* simple to use, and beginner-friendly. 

The description of PySimpleGUI explained it.

> Transforms the tkinter, Qt, WxPython, and Remi (browser-based) GUI frameworks into a simpler interface. The window definition is simplified by using Python core data types understood by beginners (lists and dictionaries). Further simplification happens by changing event handling from a callback-based model to a message passing one.
>
> Your code is not required to have an object oriented architecture which makes the package usable by a larger audience. While the architecture is simple to understand, it does not necessarily limit you to only simple problems.
> 
> Some programs are not well-suited for PySimpleGUI however. By definition, PySimpleGUI implements a subset of the underlying GUI frameworks' capabilities. It's difficult to define exactly which programs are well suited for PySimpleGUI and which are not. It depends on the details of your program. Duplicating Excel in every detail is an example of something not well suited for PySimpleGUI.


<h2><span id="get-started">Get started!</span></h2>

