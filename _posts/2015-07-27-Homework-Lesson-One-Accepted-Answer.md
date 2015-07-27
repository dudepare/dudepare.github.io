---
layout: post
---
After all the effort I put in--Forms, Templates, Views, HTML, CSS, Web Fonts. The most valuable lesson I learned after this exercise is to keep it simple. 

Here is the accepted answer that eventually got merged into the codebase. 

    def hello_world(request):
         if name:
             return HttpResponse('Hello %s' % name)
         else:
             return HttpResponse('<form><input name="name"></form>')
     

I can't believe that it. It's a measely four-liner. My solution was a novel compared to this one. Anyway, lesson one learned: K.I.S.S. The correct thinking is it should **meet all the requirements first**. Keep in mind that other developers will maintain this in the future. It is important to have easily **understandable, readable and maintanable code**. 

I shall try again in my next homework due this week. The goal is to have my pull request merged this time. Yes, I set my goals like that. Aim high!