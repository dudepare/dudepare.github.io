---
layout: post
---
Sublime text snippets are a great way to save time typing the same thing over and over again.

# Snippets

In Sublime text you can assign an alias to a huge chunk of text. Whatever text it is. Let say I really really love the song Climb Every Mountain from the Sound of Music.

I would love to type it the first time around. But when I just want to recall the lyrics of the song: I could just type a word(an alias) then have Sublime text expand it to the full lyrics of the song. It's just like sublime text [have  ESPN or something](https://www.google.com.au/search?q=i+think+i+have+espn+or+something).

## Steps

1. Tools Menu > New Snippet ...

This will open up a new file that looks like this

    <snippet>
        <content><![CDATA[
    Hello, ${1:this} is a ${2:snippet}.
    ]]></content>
        <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
        <!-- <tabTrigger>hello</tabTrigger> -->
        <!-- Optional: Set a scope to limit where the snippet will trigger -->
        <!-- <scope>source.python</scope> -->
    </snippet>

2. We have to replace the line `Hello, ${1:this} is a ${2:snippet}.` with our Climb Every Mountain lyrics.

3. Uncomment this line `<!-- <tabTrigger>hello</tabTrigger> -->` to assign an alias to our new snippet.

4. Think up a meaningful alias and replace `hello`. I pick `climb` as my alias for this snippet. So the line is updated to this:

`<tabTrigger>climb</tabTrigger>`

5. The final snippet looks like [this](/assets/climb.sublime-snippet). Save it.

# Use it!

Type in `climb` and press tab! 

Then start singing...

## Climb Every Mountain
    Climb every mountain
    Search, high and low
    Follow every byway
    Every path you know

    Climb every mountain
    Ford every stream
    Follow every rainbow
    'Till you find your dream

    A dream that will need
    All the love you can give
    Every day of your life
    For as long as you live

    Climb every mountain
    Ford every stream
    Follow every rainbow
    'Till you find your dream

    A dream that will need
    All the love you can give
    Every day of your life
    For as long as you live

    Climb every mountain
    Ford every stream
    Follow every rainbow
    'Till you find, your dre-e-e-e-e-e-e-eam!
