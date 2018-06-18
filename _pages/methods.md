---
permalink: /methods/
layout: single
author_profile: true
toc: true
---
Dreamgraphs aim is to give foreign developern a nice way to work with Telegraph. Therefore, we didn't rename anything from the API. You can have a look at the documentation of Telegraph [here](http://telegra.ph/api) and don't need to think about any differences.

## Methods

Lets dive right into it, shall we?

### NewAccount

This method creates you an account. It has three attributes, where only one of it is required, and returns an [Account object](#account):

* short_name

The required attribute. No one apart of you will know this, so you are free to choose any name you want. 

* author_name

This is the name you choose to let appear as author of your posts. _Not required_

* author_url

Any URL will work. You have to add http:// in the beginning though, otherwise you will get an AUTHOR_URL_INVALID error. _Not required_

What you probably want from this is your access_token. You will need it for everything else, so remember it. A working code could look like this:
```
from dreamgraph import NewAccount

client = NewAccount('test', 'Pool', 't.me/poolitzer')

print(client.access_token)

```
And you would get your token, which looks like this:
`a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9`


### LogIn

You should use this method if you already have created an account and know its access_token. 

* access_token

It only has this attribute and it's required. A working exam:

```
from dreamgraph import NewAccount

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

```

### msg_to_node

Honestly. WTF?

Calling this attribute of your account class will return you 

['get_account_info', 'edit_account_info', 'revoke_access_token', 'create_page', 'edit_page', 'get_page', 'get_page_list', 'get_views']

## Objects

You will always get these back when you call anything from this library.

### Account

This object has normally three attributes.

* short_name

This is the you will always get. No one expect you will see this.

* author_name

Every user is able to see this right next to your post. If you set one during the account creation, you will see it here. Otherwise you get None.

* author_url

This URL is behind the author_name. You can send it without an author_name, but no one will see it. Returns None if you didn't set one.

There are two more you only get when you call getAccountInfo.

*auth_url

This is a url user can use to login into their account on any brother. It will only work once during 5 minutes.

*page_count

This integer shows the total number of pages belonging to the Telegraph account.