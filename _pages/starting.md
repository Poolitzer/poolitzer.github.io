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

You can also clone this project from GitHub and generate your own instance, because you just can ;P
```
git clone https://github.com/JasurbekNURBOYEV/DreamGraph.git

cd DreamGraph

python setup.py
```

## Get a login token

In order to post on Telegraph, you need an access_token so it knows who is posting. DreamGraph provides you an quite easy way to login. Just call * in the beginning of your code. It will create an account the first time you run it and log you in after you run it again.

```
from dreamgraph import start

start()
```

While you need to choose a short name in the beginning (no visitor of your posts will see it, its just a name for you. If you manage several accounts, it may be helpful so you can distinguish them. Otherwise, you are free to choose a random sequel of letters), the rest of the attributes can simply be skipped when you press enter. 

If you are curious what happens here, it has an own page in this documentary, here: start-Link. If you don't want to dive in that deep: If you want to make your project open source, don't include the ***.txt and no one can use your account.

## Create a page

You probably want to create a page. You can do this via this command:

```
from dreamgraph import start

client = start()

new_page = client.create_page(title='Test', content=[{'tag': 'p', 'children': ['Hello world']}])

print(new_page.url)
```

Let's take a look at what we did here, a post created with this code is [here](http://telegra.ph/Test-06-18-27):

### Import module
`from dreamgraph import start`
Well, you need to get the modules you want to use from somewhere. There you go ;P

### Start your client
`client = start()`
client gets all necessary informations from start() to let you work with Telegraph, which is at least the access_token and additional attributes you provided during the account creation.

### Create your first page
`new_page = client.create_page(title='Test', content=[{'tag': 'p', 'children': ['Hello world']}])`
Probably the most interesting part in our little example. Lets split it up in it's parts.

#### client.create_page()

You call the method `create_page` with necessary parameters from client and store it's content in a variable. Nice beginning.

#### title='Test'

This is one of the two required parameters. It will be the title of your Telegra.ph post. 

#### content=[{'tag': 'p', 'children': ['Hello world']}]

The second required attribute. It is a Node element, which is explained here. We hope to add easy html and/or markdown support soon.

### Check your page
`new_page.url`
As you can see, new_page has some attributes. One of these is the URL of your Telegra.ph post, which you can see in you command line now :D If you want to see more attributes, go here.

## Where to go now

First of all, congrats!
