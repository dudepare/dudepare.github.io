---
layout: post
---
Both are valid ways to make a query in Django's models (i.e. Database) but they are fundamentally different. 

These commands differ in the number of results they return.

# Get
The get() method is used when you expect one item to be returned. If the method did not find and item or found several instances that match, it will scream at you.

    client = Entry.objects.get(pk=2)

*This example obviously will return 1 item because we explicitly asked for the item which has a primary key of 2.*

# Filter
The filter() method is used when you expect an output of serveral rows.

    clients = Entry.objects.order_by('projects').filter(project__client__name = 'clientXYZ')

*This sample query returns all the entries that belong to clientXYZ. We expect a lot of rows returned for this query. Calling the filter() method is appropriate to such multiple row queries.*

My problem, I was using get() while I was really expecting a lot of rows to be returned. After some more research and carefully reading the documents. I figured out that all I need to use is the filter() method.

All worked well when I used that instead.