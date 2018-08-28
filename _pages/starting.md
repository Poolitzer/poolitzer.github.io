---
permalink: /starting/
title: "Getting started"
layout: single
author_profile: true
toc: true
---
## Install

The easiest way to install DreamGraph is via pip.

`pip install dreamgraph`

You can also clone this project from GitHub and generate your own instance, because you like things complicated ;P
```shell 
git clone https://github.com/JasurbekNURBOYEV/DreamGraph.git

cd DreamGraph

python setup.py install
```

## Get a login token

In order to post on Telegraph, you need an access_token so it knows who is posting. DreamGraph provides you quite an easy way to login. Just call start() in the beginning of your code. It will create an account the first time you run it and log you back in when you restart your script.

```python
from dreamgraph import start

start()
```

While you need to choose a short name in the beginning, the rest of the attributes can simply be skipped by pressing enter. This short name is just a name for you and Telegraph, no visitor of your posts will see it. If you manage several accounts, it may be helpful so you can distinguish them. Otherwise, you are free to choose a random sequel of letters.

If you are curious what happens here, have a look at our [methods/objects page]({{ site.baseurl }}{% link _pages/methods.md %}), where it is described.

## Create a page

You probably want to create a page. You can do this with this code:

```python
from dreamgraph import start

client = start()

new_page = client.create_page(title='Test', content=[{'tag': 'p', 'children': ['Hello world']}])

print(new_page.url)
```

Let's take a look at what we did. You can find a post created with this code [here](http://telegra.ph/Test-06-18-27):

### Import module
`from dreamgraph import start`
Well, you need to get the module you want to use from somewhere. There you go ;P

### Start your client
`client = start()`
This will log you in when you already created an account or creates you one. All of this in a variable named client so you can access it later.

### Create your first page
`new_page = client.create_page(title='Test', content=[{'tag': 'p', 'children': ['Hello world']}])`
Probably the most interesting part in our little example. Lets split it up in it's parts.

#### new_page=client.create_page()

You call `create_page` with necessary parameters from client and store it's content in a variable. Nice beginning.

#### title='Test'

This is one of the two required parameters. It will be the title of your Telegraph post. 

#### content=[{'tag': 'p', 'children': ['Hello world']}]

The second required attribute. It's a Node element, which looks a bit unhandy, we know. Hopefully we are able to add easy html and/or markdown support soon. Right now, have a look at [this page]({{ site.baseurl }}{% link _pages/node.md %}) to get a nice introduction.

### Check your page
`new_page.url`
As you can see, new_page has some attributes. One of these is the URL of your Telegraph post, which you can see in you command line now :D

## Where to go now

First of all, congrats! You managed to post your first page. Maybe thats enough for you, probably not. We would suggest you now to go to the [methods/objects page]({{ site.baseurl }}{% link _pages/methods.md %}) and check out some interesting methods like edit_page. Or have a look at our [examples]({{ site.baseurl }}{% link _pages/examples.md %}) where you see code which is actually used by some projects.
