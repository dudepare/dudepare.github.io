---
layout: post
---
This article shows you how to add applications to run on startup on Ubuntu.

I recently setup my jekyll blog at github. I am so happy with it. I decided to create a local blog too. It shall be my local notebook. I wanted it to run on startup in my machine. Set it as my homepage.

# Fire up Startup Applications
In the desktop--press the super button. This triggers the find menu of Ubuntu. Key in `Startup Applications`. Click on the icon to run the software.

![Find Startup Applications](/images/01.startup.applications.png)

# Add Startup Program

![Add Startup Program](/images/02.startup.command.png)

Click on the Add button. Fill in the details:

* Name:

`Run local blog`

* Command:

`sh -c "cd /path/to/application; jekyll serve"`

* Comment:

`This will run my local blog on http://localhost:4000`

*Finally click the Add button*

> The trick here is to call sh -c "commandline" to run the application properly
