---
layout: post
title: Introducing Dash-Admin
---

I have been working on a tool for creating new [Dash](https://plot.ly/dash/) applications.  Here's a brief introduction and the roadmap from the project.  And here's a basic example in action:

![Dash Admin Demo]({{ "/images/dash-admin-demo.gif" | absolute_url }})

### Intro
#### Dash-Admin is an extension for [Dash](https://github.com/plotly/dash) to help start new Dash projects.

Dash-Admin is modelled after the ```django-admin``` command in the popular Python web framework [Django](https://github.com/django/django).  The goal of dash-admin is to provide a simple, easy-to-use CLI tool for starting projects in Dash.  

### Documentation

Getting a working Dash application is as simple as:

```dash-admin startproject myproject```

This will give you a working Dash application, complete with user authentication, user management (both online and through the CLI), and a main page with an interactive Plotly chart.  To start the application ```cd``` to the 'myproject' folder which was just created and enter:

```python run.py```

then visit [localhost:8050/myproject/app1](http://localhost:8050/myproject/app1).

You can log in with username ```admin``` and password ```admin```.

### Installation

Dash-Admin can be installed via ```pip install dash-admin``` or by cloning this repo and running ```python setup.py install```.

#### Note:
You will also need to run ```pip install https://github.com/gaw89/dash-auth/archive/v0.1.0.zip``` in order to provide user authentication.

# Dash-Admin Roadmap

## Background
This project was born out of the experience of creating my first Dash application.  I was very impressed with Dash - the clean API, the incredible functionality and integration with the Python Data Science stack, and how quickly I was able to get up and running with it (~2 weeks) - but as I created the application, I found myself thinking several times, "I will probably be doing this exact same thing next time I build a Dash app and every time thereafter."  While I suppose that's pretty typical in application development regardless of what tool you're using, I thought there should be a better way.  With such a flexible, easy-to-use tool, why would I spend time writing *boilerplate*, or worse, **copying and pasting a bunch of code files**? <img class="emoji" title=":unamused:" alt=":unamused:" src="https://camo.githubusercontent.com/bd6395fa1b3f8e9f914e8a7be0abb5c29ebb3d70/68747470733a2f2f6173736574732d63646e2e6769746875622e636f6d2f696d616765732f69636f6e732f656d6f6a692f756e69636f64652f31663631322e706e67" height="20" width="20" align="absmiddle" data-canonical-src="https://assets-cdn.github.com/images/icons/emoji/unicode/1f612.png"> I want to get straight to the creating part (which Dash makes so easy). 

I worked with Django a little bit earlier this year and thought it would be cool to have something similar to the ```django-admin startproject``` command to take care of all the boilerplate/initial setup that is necessary each time.  Furthermore, I wanted the output of the command to be as straightforward and easy-to-use as the rest of Dash.  The project is still in its infancy, but I wanted to make it available to the Dash/Plotly community to get feedback and see if there's interest from others.  

Below are some of my current thoughts about where I see the project going.

## Current Version: v0.1.14-alpha
The current version of Dash-Admin simply generates a few boilerplate files that allow starting a Dash app in a single-user environment with log-in/out functionality provided by my version of [dash-auth](https://github.com/gaw89/dash-auth/releases/tag/v0.1.0).  

## Next Version: v0.2.0
The next version to be released will include simple user management through the CLI and through an admin page on the web.  

### Future goals:
* responsive CSS boilerplate for page layout to be used via themes
* simple API for theme development
* detailed documentation for the above elements
* routing for static files
* customization via CLI (i.e. accept defaults or choose which elements to include)
* support for other databases through SQLAlchemy
