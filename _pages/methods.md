---
permalink: /methods/
layout: single
author_profile: true
toc: true
---
Dreamgraphs aim is to give foreign developern a nice way to work with Telegraph. Therefore, we didn't rename anything from the API. You can have a look at Telegra.ph documentation [here](http://telegra.ph/api) and don't need to think about any differences.

## Methods

Lets dive right into it, shall we?

### NewAccount

This method creates you an account. It has three attributes, where only one of it is required:

* short_name

The required attribute. No one apart of you will know this, so you are free to choose any name you want.

* author_name

This is the name you choose to let appear as author of your posts.

* author_url

Any URL will work. You have to add http:// in the beginning though, otherwise you will get an AUTHOR_URL_INVALID error.

What you probably want from this is your access_token. You will need it for everything else, so remember it. A working code could look like this:
```
from dreamgraph import NewAccount

client = NewAccount('test', 'Pool', 't.me/poolitzer')

print(client.access_token)

```
And you would get your token, which looks like this:
`a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9`


### LogIn

Calling this attribute of your account class will return you 

['get_account_info', 'edit_account_info', 'revoke_access_token', 'create_page', 'edit_page', 'get_page', 'get_page_list', 'get_views']