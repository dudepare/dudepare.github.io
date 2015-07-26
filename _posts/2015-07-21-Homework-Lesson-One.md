---
layout: post
title:  "Three things I learned doing the homework"
date:   2015-07-21
categories: django, python
---
The first meeting of the Melbourne Django school ended with homework. This must be completed when we return this week for the second session.

# Homework for lesson one

- [Fork this repository][gh-fork]
- Clone the repo to your own machine
- Create a virtualenv for our MelbDjango School project
- Install our requirements and use `python manage.py runserver` to test the application
- Update the view we created in class to accept a `name` GET parameter and say hello to that person.
      You'll need to access the [request.GET][dj-request-response] object.
- A step further - Add a `<form>` and `<input>` to let the user submit the name to be displayed


The first five items were fairly straight forward to implement. But the last one was the challenge. To accomplish the last one, I sought help from [The Django Book](http://www.djangobook.com/en/2.0/chapter07.html)

# 1. Forms
I needed to create a form in Django. I immediately thought I needed somekind of an external HTML to do this and have django load it and publish it for me. I created a simple HTML.

    <!DOCTYPE html>
    <html>
    <head>
        <title>Melbdjango School - Lesson one</title>
    </head>
    <body>
        <p>HOW DO <span>YOU</span> DO? <br/>
        <small>Type your name below so I could say hello.</small></p>
        <form action="/sayhello/" method="get">
            <input type="text" name="name">
            <input type="submit" value="GO">
        </form>
    </body>
    </html>

This HTML consists of a simple input text where you can enter a name and a submit button. Take note of `action="/sayhello/", this will be used in the `urls.py` later on. Saved it as name-form.html.

Now I have the HTML, I don't know how to make Django use it.

* In the views.py or urls.py for that matter, add this line where `import` section of code:

    from django.shortcuts import render

    def name_form(request):
        return render(request, 'name-form.html')

* create a new folder called `templates` in the same level as manage.py. 
* place name-form.html in this new folder.
* we must add this to the path of our project so that name-form.html can be seen by django. Edit settings.py to do this:

    TEMPLATES = [
        {
            ...
            'DIRS': [os.path.join(BASE_DIR, 'templates')],
            ...
        },
    ]
* urls.py, edit the root directory to call the name_form function:
    from timetracker import views
    
    urlpatterns = [
        ...
        # call the name_form function in views.py when you visit the site http://<whateversite.com>
        url(r'^$', views.name_form), 
        ...
    ]

# 2. Templates
Now we have a nice form where we can type in stuff and press submit. But, when you do click submit, there will be a 404 error because we haven't done that bit yet.

We'll create another HTML file again: hello.html, save it in the `templates` folder as well.

    <!DOCTYPE html>
    <html>
    <head>
        <title>Melbdjango School - Lesson one</title>
    </head>
    <body>
        <p>HELLO <span>{{name}}</span> <br/> 
        <small>pleased to finally meet you.</small>
        </p>
    </body>
    </html>

This HTML file is a bit different from the usual HTML files because it has {{name}} notation. This notation is a template notation in django. {{variable}} means that this bit will depend on a variable passed by django.

This is the main goal of templates in django. Provide a dynamic way to edit the HTML files.

Remember the `/sayhello/` a while ago? Now we'll use it to load the result when you hit submit in the form.

Create another function in the views.py :

    from django.http import HttpResponse
    ...
    def hello(request):
        if 'name' in request.GET:
            received = request.GET.get("name", "World")
            if len(received) == 0:
                received = "World"
            return render(request, 'hello.html', {'name':received})
    ...

This function will handle the event where you click submit on the form. We shall go back to `urls.py` to register a new url `/sayhello/`

    urlpatterns = [
        ...
        url(r'^sayhello/', views.hello),
        ...
    ]

When you hit submit, it will automatically send a /sayhello/ action. Now, when this happens, we want it to call the hello function to handle this request and display the outout we want.

`return render(request, 'hello.html', {'name':received})`

This bit of code uses the hello.html template and passes the dict name:value to the template. In effect, whatever we user input we received, shall be passed to the template to be rendered.

# 3. Pull request
I finished the homework pushed it to github. The final step is to create a pull request. I went to github and it was easy as clicking buttons. The only thing I missed out on was to create my own topic branch before working on the project. This is the suggested and more professional way to doing things in the open source world.

All my code can be viewed in the my [lesson-one repository](https://github.com/dudepare/lesson-one)