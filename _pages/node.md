---
permalink: /node/
title: "NODE elements"
layout: single
author_profile: true
toc: true
---
So, you want to create content with DOM nodes? Well, good for you that we prepared a little tutorial, because otherwise you will probably give up at this point. At least, thats what I did. Almost. 

Every DOM element has two attributes: Tags and children. Tags help you to style things, as you may know from HTML and CSS. Children are attributes of these tags. They can either contain new tags or just the content. Attributes to the tags exist as well, I will explain them once we arrive there.

Lets give you a quick example how you will build the content of your page:

```python
content=[{'tag': 'h3', 'children': ['Look at this header. Its wondeful, hmm?']}, 
{'tag': 'p', 'children': ['This will be a great text. Maybe. Someday.']}, 
{'tag': 'a', 'attrs' : {'href': 'https://t.me/DreamGraph'}, 'children': ['Join our group.']}
{'tag': 'p', 'children': ['To begin with, there is this big question:'] {'tag': 'em', 'children': ['Are you able to code']}
```

As you can see, it's always the same: The tag, followed by a child. 