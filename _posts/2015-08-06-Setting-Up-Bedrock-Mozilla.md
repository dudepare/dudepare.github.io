---
layout: post
---
Some of my notes while setting up Mozilla's bedrock.

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