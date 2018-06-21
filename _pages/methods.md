---
permalink: /methods/
layout: single
author_profile: true
toc: true
---
Dreamgraphs aim is to give foreign developern a nice way to work with Telegraph. Therefore, we didn't rename anything from the API. You can have a look at the documentation of Telegraph [here](http://telegra.ph/api) and don't need to think about any differences.

We split all the methods up in some nice categorys. That resulted in only 4 real methods, all other "methods" which would otherwise require the access token are attributes to the account class. These attributes often have attributes for themself. All of them return one of the listed objects. May sound complicated, but will speed up your developing, believe us.

## Methods

Lets dive right into it, shall we?

### NewAccount

This method creates you an account. It has three attributes, where only one of it is required, and returns an [Account object](#account):

* short_name

_Required_ No one apart of you will know this, so you are free to choose any name you want. 

* author_name

_Not required_ This is the name you choose to let appear as author of your posts.

* author_url

_Not required_ Any URL will work. You have to add http:// at the beginning though, otherwise you will get an AUTHOR_URL_INVALID error.

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

## Attributes

### get_account_info

FUCKING TODOD!!!!!!!

Useful if you want to get informations about your account. Doesn't have any attributes. Returns an [Account object](#account).

A working example:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

print(client.get_account_info.
```


### edit_account_info

With this attribute, you can edit your account informations. We got your back, Legolas1337. Returns an [Account object](#account). It can have the following attributes:

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

new_informations = client.edit_account_info('ThisIsAStupidShortName', 'AWayBetterAuthorName', 'https://telegram.org')

print(new_informations.author_name)
```

### revoke_access_token

In case you want to revoke you access token. You will get an [Account object](#account), but only the new access_token and the auth_url of it. It doesn't take any attributes, so a working example could look like this:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

my_token = client.revoke_access_token

print(my_token.access_token)
```

If you used start() before, you can't do this anymore. Go to the [LogIn](#login) section of this documentation to see how you can login now.

### create_page

This attribute has five attributes, two are required. It returns a [Page object](#page)


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

There are two more you only get when you call getAccountInfo with these as attributes.

* auth_url

This is a url user can use to login into their account on any brother. It will only work once during 5 minutes.

* page_count

This integer shows the total number of pages belonging to the Telegraph account.

### Page

This object does always have four attributes, and there are six more it can have.

* path

This is the part of the URL after https://telegra.ph/. It comes in handy because when you use some attributes, you don't have to type the whole URL.

* url

