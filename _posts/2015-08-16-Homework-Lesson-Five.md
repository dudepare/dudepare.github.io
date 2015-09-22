---
layout: post
---
# Q: How does django know that the field awesome should be boolean?

    class HelloWorldForm(forms.ModelForm):
        class Meta:
            model = Person
            fields = ('name', 'awesome')
            labels = {
                'awesome': 'Are they awesome?'
            }

        name = forms.CharField(label="Say Hello")

        def save(self, commit=True):
            """
            This method is unique to ModelForms

            Override the default save method to ensure that people are only
            saved as awesome if their name starts with b
            """
            person = super(HelloWorldForm, self).save(commit=False)

            if not person.name.lower().startswith('b'):
                person.awesome = False

            if commit:
                person.save()

            return person

# A: It is defined in the Person model

    from django.db import models

    class Person(models.Model):
        class Meta:
            verbose_name_plural = 'People'
            
        name = models.CharField(max_length=30)
        awesome = models.BooleanField()

        def __str__(self):
            return '{} ({})'.format(self.name, 'Totally Awesome' if self.awesome else 'Lame')

# Q: What does permanent mean here?

    class RootRedirectView(RedirectView):
        permanent = False

        def get_redirect_url(self):
            return reverse('django_form')

# A: This determines the HTTP status code to be used in the reponse.
permanent = True
http status
301 Moved Permanently
https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#3xx_Redirection

permanent = False
302 Found
or Moved Temporarily

# Forms vs. ModelForms

In form classes: 
* you define the fields you want to appear in the form.
* you define the validation rules for those fields.

In model form classes:
* you bind the form to the associated model
* list down the fields to inlude in the form
* define validation routines too

# Class based view

* Create a class based on the view you want
* Depending on the requirements of the view, assign the properties, models, templates, forms, object (optional)
* override the methods you want