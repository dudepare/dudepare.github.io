---
layout: post
---
Some of my notes while setting up Mozilla's bedrock.

# Errors
It always begins with errors. Here are the errors I encountered while setting up Mozilla - bedrock. 

This is the command I ran:

`$ bin/peep.py install -r requirements/dev.txt  # installs dependencies`

    nose: expected one of R3KrUYkik5LRbHC6e4u2a108GAdmlMVTR6-5jJULKDw
                          9h4JCadD7tN7Egfjio57Si_gqCGF428r4lLvGz-QF1g
                      got 4ZtPiklWgcNnq1bDwE-L7zDd15B939m-5mOj8yhnYrY
    Pygments: expected one of CjoiZeHvsN76ci0fQpcw3J35da3DxgrH0rQyvfA8BB0
                              cyCRkITm2sj0VAY4pGRHo71zD8oXKvwX0sA-7SLPT1E
                          got Xe0vqQlP19_rPakmNkCf1wKg0H1gYoNQTX7gRAHO5cs
    docutils: expected x9txeBCraWX2bIzwOYqYydjfmC2jm0zX8WKRHriVlvo
                   got 3OvUkoESYxYm9MTQ31l4fHSEBOZt2pUhEAMOqIPTuM0

requirements/base.txt:nose==1.3.6
requirements/dev.txt:Pygments==2.0.2
requirements/dev.txt:docutils==0.12

manually downloaded

nose-1.3.6.tar.gz 
# sha256: 9h4JCadD7tN7Egfjio57Si_gqCGF428r4lLvGz-QF1g

docutils-0.12.tar.gz 
# sha256: x9txeBCraWX2bIzwOYqYydjfmC2jm0zX8WKRHriVlvo

Pygments-2.0.2.tar.gz 
# sha256: cyCRkITm2sj0VAY4pGRHo71zD8oXKvwX0sA-7SLPT1E


# Create the right virtual environment

This is how it appears on the documentation:

    $ pip install virtualenv     # installs virtualenv, skip if already have it
    $ virtualenv venv            # create a virtual env in the folder `venv`
    $ source venv/bin/activate   # activate the virtual env
    $ bin/peep.py install -r requirements/dev.txt  # installs dependencies

This is how should it appear:

    ...
    $ virtualenv -p python2.7 venv
    ...

The bedrock project does not use the latest pip nor python version. When you do $ virtualenv venv it defaults to a python3 environment. This causes problems when you do the last command using bin/peep.py.

So you have to make sure the virtual env you create is based on python2.7.

# Keep asking questions

I am logged in the Mozilla's IRC #www channel where the people who work on bedrock hangout. They are a helpful and responsive bunch. In my experience--I get an answer to my question straight away. 

# Make the tests run

Finally, I get to download and install all the pre-requisites--I ran the tests and six test failures. All I need to do was get the locales from svn. Re-ran the unittests and everything worked. Thanks to flod @ the #www IRC channel for pointing it out to me.

[Locales](http://bedrock.readthedocs.org/en/latest/install.html#localization)

# Conclusion
I got the thing working. The critical part here is to install the right virtual environment for bedrock to avoid running into problems.