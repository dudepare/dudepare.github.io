---
layout: post
---
The topic for last week is all about testing. 

The [homework](https://github.com/MelbDjango/lesson-six) included a super bonus round where we have to use factory_boy to make our tests easier.

I have to say this topic is very open ended. There are simply no hard rules how to test your code. The possibilities that your tests cover all cases are endless. I wrote more test code than the actual code in django.

Using factory_boy was very straight forward. It's as easy as using the django forms.ModelForm class. Although I encountered one problem along the way.

# Sample model and factory using factory_boy

Here is an example of a simple django model:

    # models.py
    class Client(models.Model):
        name = models.CharField(max_length=200)

        def __str__(self):
            return self.name

In factory_boy, the equivalent class for this would be:

    #factories.py
    class ClientFactory(factory.django.DjangoModelFactory):
        class Meta:
            model = Client

        name = "Monolith Co."

Fairly straight forward right?
- Inherit from `factory.django.DjangoModelFactory`
- define a `class Meta:` and specify the model you want to use, in this case Client model.
- write the fields of the model and give it a value to test

The ClientFactory class can now be used for instantiating test objects in your unittests.

# How can I use local variables inside a Factory class?

What if I want to use temporary local variables to store some intermediate stuff within the factory class?

Short answer: use the class Meta: property `exclude`. 

`start_time` and `stop_time` variables here do not belong to the Entry model. You need to tell this explicitly to factory_boy, otherwise it will try to match start_time and stop_time to the django model.

    class EntryFactory(factory.django.DjangoModelFactory):
        class Meta:
            model = Entry
            exclude = ('start_time', 'stop_time')

        start_time = timezone.now()
        stop_time = start_time + timedelta(hours=1)
        start = timezone.now()
        stop = start + timedelta(hours=1)
        project = factory.SubFactory(ProjectFactory)
        description = "changed line endings"

Entry model code below

    class Entry(models.Model):
        start = models.DateTimeField(default=timezone.now)
        stop = models.DateTimeField(blank=True, null=True)
        project = models.ForeignKey('Project')
        description = models.CharField(max_length=200)

        class Meta:
            verbose_name_plural = 'entries'

        def __str__(self):
            return '[{} - {}] ({}) {}'.format(self.start, self.stop, self.project.name, self.description)

        def is_finished(self):
            return self.stop is not None
