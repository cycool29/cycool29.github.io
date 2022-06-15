---
title: Home
layout: default
author: cycool29
---

<h2><a href="/post/000005" style="text-decoration: none; color: #00ff00">ConfigParser - manage user-editable settings for your Python programs</a></h2>

User-configurable settings are important for big applications. They make your application more user-friendly and improve the efficiency of your application.

But you may be curious, **where and how to store those configurations?**

Here I am gonna introduce you **[ConfigParser](https://docs.python.org/3/library/configparser)**, one of the standard libraries in Python 3, which is used to save settings for your Python applications.


 <p class="btn" style="color: #0f0; font-size: 90%; border-color: #00ff00"><a style="text-decoration: none; color: #0f0;"
                        href="/post/000005.html">Continue Reading </a></p>

<br/>

### **Latest posts**

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}


