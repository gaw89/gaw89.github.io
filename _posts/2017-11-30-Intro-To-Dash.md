---
layout: post
title: Intro to Plotly Dash
---

Over the last couple of weeks, I've been getting acquainted with a new(-ish) package for creating analytical web apps in Python called [Dash](https://plot.ly/products/dash/). Dash comes from the talented folks over at [Plot.ly](https://plot.ly/).  So far, I have been very impressed with the simplicity and ease of use with Dash.  You can get some pretty incredible interactivity with very little code, and, best of all, it only requires Python!  The basic Dash example with interactivity from the Dash User Guide is simply:

```python
import dash
from dash.dependencies import Input, Output
import dash_core_components as dcc
import dash_html_components as html

app = dash.Dash()

app.layout = html.Div([
    dcc.Input(id='my-id', value='initial value', type="text"),
    html.Div(id='my-div')
])

@app.callback(
    Output(component_id='my-div', component_property='children'),
    [Input(component_id='my-id', component_property='value')]
)
def update_output_div(input_value):
    return 'You\'ve entered "{}"'.format(input_value)

if __name__ == '__main__':
    app.run_server()
```
    
This example gets you a web page that looks like this:

![Dash Interactivity Example]({{ "/images/dash_interactivity_demo.gif" | absolute_url }})

As you can imagine, the possibilities here (especially for a Python programmer who doesn't want to be bothered with a lot of front-end programming...) are huge.  Another great feature of Dash is that it's built on top of [Flask](http://flask.pocoo.org/).  As such, it's relatively easy to integrate Flask features and extensions into a Dash app.  For example, you can use [Flask-Login](https://flask-login.readthedocs.io/en/latest/) to implement user management in Dash.  Currently, this requires a bit of hacking, but I'm working on an update to the [dash-auth](https://github.com/plotly/dash-auth/pull/17) extension that will allow user management with Flask-Login in a single line of code.  

Dash is also (somewhat obviously) integrated with Plotly.  One can use the Plotly Python API to build a huge range of interactive data visualizations that are coupled to Dash via callbacks.  Rather than go into detail here, I'll refer the reader to the [official Dash docs](https://plot.ly/dash/).  It takes less than an hour to make it through the Dash Tutorial, and once finished, you'll be off to the races.

As an example of how easy to use Dash really is, I recently completed my first web dashboard using Dash.  From having never written a single line of Dash code to completing an application which included user management/authorization, several Plotly graphs, a couple tables, and raw download links, it took about two weeks.  Obviously, now that I'm much more familiar with Dash (and Flask, which I'd only experimented with a little before), the time to get similar projects up and running will be much shorter.  I will also be working on a tool to provide simple starter code for a Dash app similar to ```django-admin startproject mysite``` for those who have used Django.  I'll post a guide here when it's up and running.

It's also important to keep in mind that Dash is very new.  The [official announcement](https://medium.com/@plotlygraphs/introducing-dash-5ecf7191b503) was just published on June 21, 2017.  The amount of functionality and maturity of the API, to me, is impressive for such a young piece of software.  I'm very excited to see how the application continues to grow and develop, and I know I'll be getting a lot of mileage out of it in the future.
