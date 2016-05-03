---
layout: post
title:  HTML Forms
date:   2016-05-03
categories: programming
---

*You won't see this in tutorials.*

I encountered an issue where I have two HTML forms. On a bright sunny day, they work perfectly fine. On some random gloomy and cold day, one of the forms don't work as expected.

## Let's see some code

### Form 1

	<form data-form-id="deform" method="POST" id="deform" class="form-horizontal alert alert-warning" autocomplete="off" action="/incident/5543/escalate?level=0&amp;_=1462175483602" role="form" accept-charset="utf-8" enctype="application/x-www-form-urlencoded">
	...
	</form>

### Form 2

	<form data-form-id="deform" method="POST" id="deform" class="form-horizontal deform" autocomplete="off" action="/incident/5543/secure?_=1462175483601" role="form" accept-charset="utf-8" enctype="application/x-www-form-urlencoded">
	...
	</form>

## Sunny day
These forms live in one page, only one is active at a given time. As you might think and expect--these forms create the following HTML requests on a perfect sunny day.

### Form 1

	GET /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1
	POST /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1

### Form 2

	GET /incident/5543/secure?_=1462175483597 HTTP/1.1
	POST /incident/5543/secure?_=1462175483597 HTTP/1.1

## Rainy day
You can see Form 2 two decides to join Form 1's umbrella.

### Form 1

	GET /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1
	POST /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1

### Form 2

	GET /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1
	POST /incident/5543/escalate?level=1&_=1462175483595 HTTP/1.1

## Dusk

I did not know how to fix this. I asked for help after investigating the shit out of this issue. I just had to know why the two forms mixes things up when its time to send out the data to a url. It was quite clear that Form 1 should send to URL 1 and Form 2 should send to URL 2. It says right there in the HTML code!

## Dawn

Good thing I asked the right person -- a front end man. He immediately pointed out that I'm using the same formid in both HTML forms which ultimately confuses the form which URL to send it to.

For the fix, I just differentiated the formid properties of both forms so that there will be no confusion.

### Form 1

	<form data-form-id="deform-escalate" method="POST" id="deform-escalate" class="form-horizontal alert alert-warning" autocomplete="off" action="/incident/5543/escalate?level=0&amp;_=1462175483602" role="form" accept-charset="utf-8" enctype="application/x-www-form-urlencoded">
	...
	</form>

### Form 2

	<form data-form-id="deform-secure" method="POST" id="deform-secure" class="form-horizontal deform" autocomplete="off" action="/incident/5543/secure?_=1462175483601" role="form" accept-charset="utf-8" enctype="application/x-www-form-urlencoded">
	...
	</form>

## Take aways
+ That's why you should have to work in a diverse team. You don't have ALL the skills you need to finish a task. You have to learn from eachother.
+ Front end stuff is hard to debug--specially when you're much more of a backend person.
+ Don't be afraid to ask what you do not know. There's a caveat to this, you should have exhausted all the avenues first so that you could explain the issue clearly.
+ There are more avenues where you can ask for help. IRC is the best one. Depending on the programming language you're using, for sure there is one channel for that. I hang out on these channels: #ruby #rubyonrails #python 
