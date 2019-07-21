Setting Area
=============

Introduction
____________

Since modules are written in Python, they use Functions which are called "Definitions", these "defs" are functions that the software will run.
More info here: https://www.tutorialspoint.com/python/python_functions

===========
**Example**
===========
simple example::

        #====================== DEFINITON AREA =====================
        #here's where the definitions are made.
        #There's 5 "default" defs:
        #async def cardcode(): which gives the cardcode generating algorithm
        #async def pincode(): which gives the pincode generating algorithm
        #def request(): Which returns the url
        #async def scrapper(): This is used to scrap the value of the giftcards
        #                Leave it empty to save valid giftcards without their value
        #def settings(): returns the data to send in the GET request

        #====== SETTINGS AREA ======
        def request(): #URL to send the requests to
                url = "http://example.com/balance"
                return url

        async def scrapper(response): #Code that fetches the value/balance of the card
                value = "$" + response
                return (value)

        def settings(cardcode, pincode, captcha, token): #Data to send at each request
                data = {'cardNumber':cardcode} #data to send
                return (data)

        #===========================================================

Each module has 3 "basic" defs that are always there:

- def request():

- async def scrapper(response):

- def settings(cardcode, pincode, captcha, token):

These must always be present and must not be remove.

However 5 more "optional" defs exist in case you need to use tokens or cookies

==============
**For tokens**
==============

- def token_request():

- async def token_scrapper(response):

===============
**For cookies**
===============
- def cookie_request():

- async def cookie_scrapper(response):

- def cookie_settings(cookie):

As you might've noticed some functions have the keyword "async" before the "def" one. This simply just state that the function must be run asynchronously. But don't worry about it, all you need to know is that async defs **MUST** have the async tag and non-async defs **MUST NOT** have the async tag.



def request
___________
This is will return the url to send the request to.

===================
**Finding the url**
===================
The url the request is sent to might not always be the same than the url of the webpage the balance checker is on.

To find what url the request is sent to, you need to open the Network console (cf: the Method section of Setup Area)

Here we can see the Request URL

.. image:: https://b.catgirlsare.sexy/Q5r4.png
    :align: center
    :alt: Request Url
	
=====================
**Declaring the url**
=====================
Setting up the url is quite straighforward, you just set a variable to the url and return that variable like such::

        def request(): #URL to send the requests to
            url = "http://example.com/balance" #url must be in BETWEEN APOSTROPHES!
            return url #You must not forget to return the url! (and make sure indentation is correct)

==================
**Special cases**
==================
To send queries or data through a request, you must declare them in the settings() function, however if it so happens that the request's is **POST while Also** requiring queries, you must set them up directly in the url like such::

        def request(): #URL to send the requests to
            url = "http://example.com/balance?one=true&two=false" #url must be in BETWEEN APOSTROPHES!
            return url #You must not forget to return the url! (and make sure indentation is correct)


async def scrapper
__________________

The scrapper is a very important function of the module, as it is the one that's in charge of fetching whatever balance is on a valid giftcard

You can fetch the balance of a card by analysing the text response a webpage returns when a card is valid and finding where in the source code the value of a card is declared. This can be accomplished in many different ways in Python.

==============
**The basics**
==============

``async def scrapper(response):`` In here the response object corresponds to the text source code of the response webpage

You can use Python's tools to cut/slice/scrap code and find the cards value, you can also use third party libraries such as BeautifulSoup4 or lxml with XPath and such.

===========
**Example**
===========

Normal HTTP/XML response
------------------------

Let's take a simple webpage where a valid giftcard would return this reponse:


.. image:: https://b.catgirlsare.sexy/KlBK.png
    :align: center
    :alt: Example of valid response

Now we must look through the network tool in the response area (cf: Setup Area) and we'll find this:

.. image:: https://b.catgirlsare.sexy/cDDd.png
    :align: center
    :alt: Example of valid response

So now to properly scrap this we can use the lxml library (https://lxml.de/index.html) by importing it ``from lxml import html`` and use XPath such as such::

    async def scrapper(response): #Code that fetches the value/balance of the card
        tree = html.fromstring(response) #We use the html fromstring attribute
        value = tree.xpath("//*[@id='LBalance']")[0].text.replace('Your balance: ', '') #We're using Xpath args to fetch the balance
        return value
		
Here we are using Xpath to fetch the ``Your balance: $231.08`` code and then by using ``.replace('Your balance ','')`` we're directly the value to be returned to be ``$231.08`` without all of that "Your balance" shit.

JSON response
-------------

Let's take a simple webpage where a valid giftcard would return this response:

.. image:: https://b.catgirlsare.sexy/xRvm.png
    :align: center
    :alt: Example of valid response

Now we must look through the network tool (cf: Setup Area) and we'll find this:

.. image:: https://b.catgirlsare.sexy/Knem.png
    :align: center
    :alt: Example of valid response

Now using ujson we can easily parse this response as so::

    async def scrapper(response):
        resp = ujson.loads(str(response))
        value = "$" + str(resp['result']['I2'])
        return (value)

This will return $0.38

=============================
**Using XPath, lxml and bs4**
=============================

As we saw above with the Html case, we can use the lxml library to easily scrap data with XPath.

If you'd like to have more documentation on XPath, lxml or bs4 you can find some here:

- https://lxml.de/index.html
- https://www.crummy.com/software/BeautifulSoup/bs4/doc/
- https://www.w3schools.com/xml/xml_xpath.asp

def settings
____________

The settings function returns what you want to send as a query / data / json in your request

===========
**Basics**
===========

There is 4 arguments that are passed with the settings section:

- cardcode (the cardcode)
- pincode (the pincode)
- captcha (the captcha solution key)
- token (the token(s))

it is syntaxed as such::

    def settings(cardcode, pincode, captcha, token): #Data to send at each request
        data = {'Check':'true','authenticityToken':token, 'number':cardcode, 'g-recaptcha-response':captcha} #example data to send
        return (data) #don't forget to return it

As you can see that data must be formatted with brackets as such: ``{'argument':'value', 'argument2':'value'}``

===============================
**How to find the data/params**
===============================

Finding what data is supposed to be sent is easy, to do so simply use the network console (cf: the Method section in Setup Area) and click the Params tab

.. image:: https://b.catgirlsare.sexy/wnZM.png
    :align: center
    :alt: Params tab

Here this data would give use this::

    def settings(cardcode, pincode, captcha, token): #Data to send at each request
        data = {'campanyId':'bbp01', 'pageMode':'0', 'loginAttempts':'0', 'enteredCardNumber':'0000000000'} #data to send
        return (data)

=================
**Special cases**
=================

Tokens
-------
See the Tokens section

The empty data
--------------
When you have an empty like such:

.. image:: https://b.catgirlsare.sexy/p3yv.png
    :align: center
    :alt: Empty arg

You format your data as such::

    data = {'name':'GiftCarder', 'emptyarg':'', 'Pin':pincode, 'enteredCardNumber':cardcode}

The JSON case
--------------
In the case the server requires json data to be sent we have special things to (cf: Setup Area - Method - Headers)

You'll need encode your request like such::

    def settings(cardcode, pincode, captcha, token): #Data to send at each request
        data = {'number':cardcode, 'pin':pincode}
        json_data = ujson.dumps(data)
        return (json_data)
		
Here we're using the ujson library which would need to be imported with ``import ujson`` (cf: Import Area)


The Token case
______________

Tokens are usually small strings hidden a webpage's source to identify the validity of a request.

If the website you're trying to brute uses token, you must add a few functions to your module. First you need to set ``token = True`` in the Setup Area

Then you must add these 2 Functions:

- def token_request():

- async def token_scrapper(response):

=================
def token_request
=================

This works exactly like ``def request():`` does. Tokens aren't always hidden in the same webpage of the request.

A such you must declare what url the bot will fetch the source code from::

    def token_request():
        url = 'https://example.com/page'
        return url

==================================
async def token_scrapper(response)
==================================

Now this is the same thing as the ``async def scrapper(response)`` function. Except that instead of scrapping a card's value, we're scrapping a (or multiple) token's value.

This function works the same as the scrapper one like this::

    async def token_scrapper(response): #The response object is the source code of the url you specified earlier
        tree = html.fromstring(response)
        token = tree.xpath('//*[@name="OWASP_CSRFTOKEN"]/@value')[0] #little example using the lxml library and XPath
        return token

====================
Multiple tokens case
====================

In the case the website you're making a module for requires more than one token hidden in the source code, you must bundle your tokens together in square brackets to make a python list

Like this::

    async def token_scrapper(response): #The response object is the source code of the url you specified earlier
        tree = html.fromstring(response)
        token_one = tree.xpath('//*[@name="OWASP_CSRFTOKEN"]/@value')[0] #little example using the lxml library and XPath
        token_two = tree.xpath('//*[@name="XKCD_CSRFTOKEN"]/@value')[0]
        return [token_one, token_two] #this will return both tokens as a list

===================================
Using them in the settings function
===================================

Now once you've specified the url to fetch the tokens, and scrapped them, it is now time to use them in your request. 

You'll notice you have a ``token`` argument already present in the settings function, this is equal to what the ``token_scrapper(response)`` function returned.

To use them, do like so::

    def settings(cardcode, pincode, captcha, token): #Data to send at each request
        data = {'campanyId':'bbp01', 'pageMode':'0', 'TOKEN':token, 'enteredCardNumber':'0000000000'} #data to send
        return (data)

Now if you have returned a list of multiple tokens, you can set them up likes this::

    def settings(cardcode, pincode, captcha, token): #Data to send at each request
        data = {'campanyId':'bbp01', 'pageMode':'0', 'TOKEN1':token[0], 'TOKEN2':token[1], 'TOKEN3':token[2], 'enteredCardNumber':'0000000000'} #data to send
        return (data)

As you can see in this example, we add a number between square brackets to specify which element of a list we want. Here's an example:

Let's say we have a token_scrapper function like so::

    async def token_scrapper(response): #The response object is the source code of the url you specified earlier
        token_one = "Bot"
        token_two = "Beater"
        return [token_one, token_two] #this will return both tokens as a list

Well in this case, specifying ``token[0]`` in the settings function will return "Bot" and specifying ``token[1]`` will return "Beater"


The Cookie case
_______________

Cookies are small strings of text that are sent during a request to send information on the user. Sometimes these cookies are used as identifiers to verify the validity of a request

If the website you're trying to brute uses cookies, you must add a few functions to your module. First you need to set ``cookie = True`` in the Setup Area

Then you must add these 3 Functions:

- def cookie_request():

- async def cookie_scrapper(response):

- def cookie_settings():

==================
def cookie_request
==================

This works exactly like ``def request():`` and ``def token_request()``.

A such you must declare what url the bot will fetch the cookies from::

    def cookie_request():
        url = 'https://example.com/page'
        return url

===================================
async def cookie_scrapper(response)
===================================

This function will work a little differently than the normal scrapper function or the token scrapper.

/!\ This part is still under construction /!\