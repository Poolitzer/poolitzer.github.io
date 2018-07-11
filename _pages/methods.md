---
permalink: /methods/
layout: single
author_profile: true
toc: true
---
Dreamgraphs aim is to give foreign developern a nice way to work with Telegraph. Therefore, we didn't rename anything from the API. You can have a look at the documentation of Telegraph [here](http://telegra.ph/api) and don't need to think about any differences.

I will give you a quick introduction to this side (and in some extend to the API) now so you are able to navigate and find anything you want quickly.

You will work with Dreamgraph in this easy way: You call a method. Dreamgraph returns you an object. We build the documentation in the same way: First, you will find all the methods. After that, we explain the objects.

## Account

Everything related to your account.

### NewAccount

This method creates you an account. It has three attributes, where only one of it is required, and returns an [Account object](#account-1):

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

You should use this method if you already have created an account and know its access_token. It returns an [Account object](#account-1).

* access_token

It only has this attribute and it's required. A working example:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

```


### get_account_info

FUCKING TODOD!!!!!!!

Useful if you want to get informations about your account. Doesn't have any attributes. BUT SHOULD, FUTURE!. Returns an [Account object](#account-1).

A working example:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

print(client.get_account_info.
```


### edit_account_info

With this method, you can edit your account informations. We got your back, Legolas1337. Returns an [Account object](#account-1). It can have the following attributes:

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

In case you want to revoke you access token. You will get an [Account object](#account-1), but only the new access_token and the auth_url of it. It doesn't take any attributes, so a working example could look like this:

```
from dreamgraph import LogIn

client = LogIn('a00bdbbbca7e11829119c405907feca8fe9151e5e1400084998cec3039c9')

my_token = client.revoke_access_token

print(my_token.access_token)
```

If you used start() before, you can't do this anymore. Go to the [LogIn](#login) section of this documentation to see how you can login now.

## pages

Everything around pages \O/

### create_page

This method has five attributes, two are required. It returns a [Page object](#page):

* title

_Required_ This big black string your post starts with...

* content

_Required_  Pass it as a node list. Find out about nodes [here]({{ site.baseurl }}{% link _pages/node.md %})

* author_name

_Not required_ only pass this if you want to change it, otherwise you can ignore that.

* auth_url

_Not required_ you can pass it here, if you already have one in your account, you don't need to.

* return_content

__Not required_ Boolean. Default is true. If you don't need to work with content in your skript, you can set this to false and take a bit load off the Telegram Servers. But keep in mind that they are used to handle a lot more traffic then your little API call does, so no need to change that as well.


### edit_page

You can edit a post with this method. If you want to make sure that you don't run into a denied error, you can either call [get_page](#get_page) and check if can_edit is true or you take the path from [get_page_list](#get_page_list)



### get_page

### get_page_list

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

_There are two more you only get when you call getAccountInfo with these as attributes._

* auth_url

This is a url user can use to login into their account on any brother. It will only work once during 5 minutes.

* page_count

This integer shows the total number of pages belonging to the Telegraph account.

### Page

This object describes a telegraph post.

* path

This is the part of the URL after https://telegra.ph/. It comes in handy because when you use some attributes, you don't have to type the whole URL. Expect something like _Test-06-18-27_

* url

It's the whole URL, surprise. Will look like _https://telegra.ph/Test-06-18-27_.

* title

This is the title of the page, the big black one before the post content starts. In our example it's *Test*.

* imge_url

This can be passed if a cover image is given. A cover image is a image in the beginning of a post. No text befor it.

* description

Basically the first about 500 characters of a post.

* content

The content of the post. It's an array of node elemets, you can find out about them [here]({{ site.baseurl }}{% link _pages/node.md %}).

* views

The view counter, returned in an integer.

* can_edit

Either true or false (_boolean_), depends if it's your page or isn't. OR ALWAYS FALSE BECAUSE FUTURE CAN'T FIX HIS FUCKING CODE! still love you mate, good job ;P

* author_name

If the page has an author name, it will be returned. Otherwise, its None.

* author_url

If the author has a URL, you can get it like this. Otherwise, its None,