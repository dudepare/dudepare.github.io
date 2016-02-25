---
layout: post
title: Newbie Woes
date: 25 February 2016
---

Three months ago, I signed up for a new job here at Melbourne, Australia. This is my first ever tech job here. I can't help but feel anxious in my new work because everything is all new. I know very little. I get little help as well, it looks like I am pretty much on my own with the responsibility of maintaining an existing product without any documentation but the source.

So what do you do when you are in the same situation as I am?

# Learn to read code

I just changed technologies from C/C++ to Python and a lot of Javascript. Javascript is definitely not my comfort zone. It is stressful for me to go down that path. Python on the other hand should be easy to understand, readable, and quite straight forward. But I quickly learn that even though it is how the python language is designed, it is still up to the developer on how they use it to make it maintainable for the ones left behind. The only option and the surest way to understand code is to read it line by line. It sure does takes a lot of time.

# Write unit tests

This project does not have any kind of tests at all. They are all done manually and does not seem to be consistent with the expected output is. That's why bugs are easily filed -- because there's no record of what the software should be doing. I am protecting myself from that vicious cycle by writing up tests. I just discovered how to write unittests for the models. I am enjoying that. But soon enough, I also have to write unittests for the views. Yeah it is a python web app that I am developing. It is using pyramid and sqlalchemy.

# Write documentation

I am aware that there is doc subfolder somewhere inside the project folder. I tell you--there's a lot of room down there. I have tried to compile the documentation with Sphinx and it produced some output. Is it useful? A little bit. It doesn't cover the things I do not know yet. It will be useful for the new starts.

Right now, I just sought some help from the original author. I hope he answers all of my questions and will give me more clarity.