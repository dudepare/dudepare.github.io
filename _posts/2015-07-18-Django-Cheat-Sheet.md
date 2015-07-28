---
layout: post
title:  "Python Django Cheat Sheet"
date:   2015-07-18 00:47:00
categories: django, python
---
This is a collection of commands I had to run during my python/django class.

# Get python version
`$ python --version`

# Installing python3 on Ubuntu
`$ sudo apt-get install python3.4`

# Install pip
The python package manager.

    $ curl https://bootstrap.pypa.io/get-pip.py > get-pip.py
    $ sudo python3 get-pip.py

# Pip commands

* Install packages with pip
`$ pip install -U <package-name>`

* Install a list of packages
`$ pip install -r <requirements-file>`

* Update pip
`$ pip install -U pip`

This is a perfect example of eating your own dog food. If the pip command doesn't work right off the bat:

* try prefixing the commands with `sudo` + `pip install <the rest of the command>`
* instead of using `pip`, use `pip3`

# Install virtualenv
`$ [sudo] pip3 install -U virtualenv`

# Create a virtualenv
    $ cd <project-name>
    $ virtualenv -p python3 <project-name>
    $ source <project-name>/bin/activate

# Install Django
Make sure your virtualenv is activated
`$ pip install -U Django`

# Create a new project in Django
`$ django-admin startproject <project-name>`

# Run django project
`$ python manage.py runserver`

# Create a Django App
`$ ./manage.py startapp <appname>`



#### Note to self
Update this cheat sheet as the course progresses. This is an investment that will pay dividends in the long haul.