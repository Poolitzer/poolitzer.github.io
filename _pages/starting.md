---
permalink: /starting/
title: "Getting started"
layout: single
toc: true
---
## Install

The easiest way to install DreamGraph is via pip.

`pip install dreamgraph`

You can also clone this project from GitHub and generate your own instance, because you just can ;P
```
git clone https://github.com/JasurbekNURBOYEV/DreamGraph.git

python setup.py
```

## Get a login token

In order to post on Telegraph, you need an access_token so it knows who is posting. DreamGraph provides you an quite easy way to login. Just call * in the beginning of your code. It will create an account the first time you run it and log you in after you run it again.

```
from dreamgraph import start

start()
```

While you need to choose a short name in the beginng (No visitor of you post will see it, its just a name for you. If you manage several accounts, it may be helpful so you can distinguish them. Otherwise, you are free to choose a random sequel of letters).

If you are curious what happens here, it has an own page in this documentary, here: start-Link. How do I do this, btw?

## Next steps

You probably want to create a page. You can do this via this command:

```
from dreamgraph import create_page

client.create_page
```

