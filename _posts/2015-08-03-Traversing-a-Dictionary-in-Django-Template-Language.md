---
layout: post
---
Iterating through a dictionary is straight forward in python as it is in Django Template Language (DTL).

I was doing my homework this morning for [MelbDjango - Lesson Three](https://github.com/MelbDjango/lesson-three). I was finished with the basic stuff and I was on to the last few stages of the homework. As they say almost done is NOT done. It's always 90% finished in software projects. I am at this point and not about ready to give up. 

During the lecture, object lists are always returned by the models. Easy enough to iterate through.

    clients = Client.objects.all()
    for client in clients:
        print(client.name)

To traverse a dictionary in python3, it will be as trivial as:

    for k, v in dictionary.items():
        print(k, v)

Here's an interesting [article](http://stackoverflow.com/questions/10458437/what-is-the-difference-between-dict-items-and-dict-iteritems) in Stack Overflow on the method items() and it's history. 

The thing is, I didn't know how should I go through iterating through a dictionary using DTL.

# Django Template Language

Iterating through an object list is almost as straight forward in python.

    {% raw %}
    {% for item in object_list %}
        <li> {{ item.name }} </li>
    {% endfor %}
    {% endraw %} 


While iterating through a dictionary is somewhat the same. The absence of the parenthesis "()" at the end of the dictionary is very important. That took me a while to figure out.

    {% raw %}
    {% for k, v in object_list.items %}
        <li> {{ k }} - {{ v}} </li>
    {% endfor %}
    {% endraw %}

> Knowing how to iterate through a dictionary in Django Template Language was very vital information for me to finish my homework in lesson three.

# Best practices
Later on, I found out dictionaries are not recommended to be used in templates because they are unordered. It is better to use list of lists with two elements. The first one being the key and the second one being the value.

*e.g.*
`[[[key1], [value1, value2, value3]], [[key2], [value1, value2, value3]] ]`
