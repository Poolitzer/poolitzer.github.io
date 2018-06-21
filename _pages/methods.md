---
permalink: /methods/
layout: single
author_profile: true
toc: true
---
Dreamgraphs aim is to give foreign developern a nice way to work with Telegraph. Therefore, we didn't rename anything from the API. You can have a look at the documentation of Telegraph [here](http://telegra.ph/api) and don't need to think about any differences.

We split all the methods up in some nice categorys. That resulted in only 4 real methods, all other "methods" are attributes to different classes. May sound complicate, but will speed up your developing, believe us.

## Methods

Lets dive right into it, shall we?

### NewAccount

This method creates you an account. It has three attributes, where only one of it is required, and returns an [Account object](#account):

* short_name

The required attribute. No one apart of you will know this, so you are free to choose any name you want. 

* author_name

This is the name you choose to let appear as author of your posts. _Not required_

* author_url

Any URL will work. You have to add http:// at the beginning though, otherwise you will get an AUTHOR_URL_INVALID error. _Not required_

What you probably want from this is your access_token. You will need it for everything else, so remember it. A working code could look like this:
```
from dreamgraph import NewAccount

client = NewAccount('test', 'Pool', 't.me/poolitzer')

print(client.access_token)

```
And you would get your token, which looks like this:
`a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9`


### LogIn

You should use this method if you already have created an account and know its access_token. It returns an [Account object](#account).

* access_token

It only has this attribute and it's required. A working example:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

```

### msg_to_node

Honestly. WTF?

## Account-Attributes

### get_account_info

Useful if you want to get informations about your account. It needs the access_token as attribute.

**Insert Shit**

### edit_account_info

With this attribute, you can edit your account informations. We got your back, Legolas1337. It can have the following attributes:

* short_name

_Not required_ Your account name. No one will see it, it's for you in case you have to manage several acoounts. Otherwise, you are free to choose any garbage.

* author_name

_Not required_ The name which will appear next to your posts. It's visible, so choose wise.

* author_url

_Not required_ The URL which will open when you click on the author name. You can pass it without a name, but it won't be shown to the visitors.

A working example could look like this:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

client.edit_account_info(

```



###

Calling this attribute of your account class will return you 

'revoke_access_token', 'create_page', 'edit_page', 'get_page', 'get_page_list', 'get_views']


## Objects

You will always get these back when you call anything from this library.

### Account

This object has normally three attributes.

* short_name

This is the attribute you will always get. No one except you will see this.

* author_name

Every user is able to see this right next to your post. If you set one during the account creation, you will see it here. Otherwise you get None.

* author_url

This URL is behind the author_name. You can send it without an author_name, but no one will see it. Returns None if you didn't set one.

There are two more you only get when you call getAccountInfo.

*auth_url

This is a url user can use to login into their account on any brother. It will only work once during 5 minutes.

*page_count

This integer shows the total number of pages belonging to the Telegraph account.