---
layout: post
title: Stack Overflow
date: 2016-07-28
categories: programming
---

I wonder what would developer life be without Stack Overflow? To find out, I just have to go back 20 years.

Today, I was documenting stuff. I was documenting an installation guide for a python web app. The usual stuff, I was grabbing screen shots, trying out some commands myself, listing all the procedures down, publishing them to our documentation repository.

1. I had to setup a Linux virtual machine (Centos7)
2. Compile python3.5 from source
3. Install virtualenv, and virtualenvwrapper

No big deal. Until I was about to create a new virtual environment using python 3 as a default version.

Create virtual environment with default parameters

	$ mkvirtualenv py2
	(py2) $ python --version
	Python 2.7.5

Create a python 3 virtual environment

	$ mkvirtualenv -p python3 py3
	Traceback (most recent call last):
  	File "/usr/local/lib/python2.6/dist-packages/virtualenv.py", line 17, in <module>
    	import zlib

	ImportError: No module named zlib

A quick stack overflow search returned [this](http://stackoverflow.com/questions/6169522/no-module-named-zlib). Basically explaining, I have to install zlib-devel first then recompile python3 from source.

	$ sudo yum install zlib-devel
	$ cd Python-3.5.2
	$ ./configure && make
	$ sudo make install

Cool. I go back to:

	$ mkvirtualenv -p python3 py3
	...
	ImportError: cannot import name HTTPSHandler

And a new error occurs. Great!
Another quick stack overflow search returned [this](http://stackoverflow.com/questions/24480101/importerror-cannot-import-name-httpshandler-installing-get-pip-py). Again, I have to install openssl-devel then re-compile python3 from source.

	$ sudo yum install openssl-devel
	$ cd Python-3.5.2
	$ ./configure && make
	$ sudo make install

Cool. I go back to:

	$ mkvirtualenv -p python3 py3
	Running virtualenv with interpreter /usr/local/bin/python3
	Using base prefix '/usr/local'
	New python executable in /home/user/envs/py3/bin/python3
	Also creating executable in /home/user/envs/py3/bin/python
	Installing setuptools, pip, wheel...done.
	virtualenvwrapper.user_scripts creating /home/user/envs/py3/bin/predeactivate
	virtualenvwrapper.user_scripts creating /home/user/envs/py3/bin/postdeactivate
	virtualenvwrapper.user_scripts creating /home/user/envs/py3/bin/preactivate
	virtualenvwrapper.user_scripts creating /home/user/envs/py3/bin/postactivate
	virtualenvwrapper.user_scripts creating /home/user/envs/py3/bin/get_env_details
	(py3) $ python --version
	Python 3.5.2

Awesome. It worked!

## Wiser

Looking back, prior to compiling python3 from source, I should have done this first.

	$ sudo yum install zlib-devel openssl-devel epel-release # not too sure about the last one, but it won't hurt.

Yeah, so I appreciate Stack Overflow for providing quick answers to these kind of stuff. It just gets you jumping over hurdles faster.


