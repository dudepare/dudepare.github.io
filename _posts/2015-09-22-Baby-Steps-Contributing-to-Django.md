---
layout: post
---

I want to contribute to open source software using python. I picked Django project to work on.

Here are my notes on the first exercise: [Contributing to Django](https://docs.djangoproject.com/en/dev/intro/contributing/)

I am running python3 on Ubuntu 14.04 64-bit. 

# Errors encountered 

## Missing Python.h
    fatal error: Python.h: No such file or directory
    #include <Python.h>  

*Download*

    sudo apt-get install python3-dev

## Missing ffi.h

    fatal error: ffi.h: No such file or directory
    #include <ffi.h>

*Download*

    sudo apt-get install libffi-dev


