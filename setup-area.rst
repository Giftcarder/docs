Setup Area
==========


Introduction
_____________

The Setup area is the most essential place of your module, this is where you will set the different variables and options of your configs. 

Make sure you have **ALL** the different options present when making a config and that you follow each format correctly (cf: the example module in the Getting Started section), if an option isn't formatted correctly or is lacking, the software will return an error.


Name
____

The first section is the name. This is the name that will be displayed when loading the module:

.. image:: https://b.catgirlsare.sexy/AmiC.png
    :align: center
    :alt: Displayed name

To write a name you must do so as such::

    name = "Name to be displayed"

Make sure the name is between apostrophes like such ``"Name"`` or ``'Name'``

Maker sure the name isn't over 78 characters or it will be automatically shrunk down.

Mehtod
______

================================
**How to know which one I want**
================================

If you are not familiar with HTTP methods and Networking, when you send a request to a server, it will be setup in a certain way, usually either GET or POST, for more info on methods: https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

Now to find out what method the website is using when checking for balance, you must open the Network tool (CTRL+SHIFT+E on Firefox and Control+Shift+J on Chrome)

This should open up a tool like this (Firefox):

.. image:: https://b.catgirlsare.sexy/S_AM.png
    :align: center
    :alt: Network tool (Firefox)

Now simply try and check your card balance (usually by clicking a button after inputting a card number), and you should see some requests are being made to the website as such:

.. image:: https://b.catgirlsare.sexy/-8Ja.png
    :align: center
    :alt: Network tool (Firefox)

Here we can see that the browser is sending a **POST** request to the url https://buffalobrewpub.alohaenterprise.com/efMemberLinkLogin.do.

If you are unsure which request is the one that checks the card balance, simply head over to the "Params" tab and check if the card number you put is there or not:

.. image:: https://b.catgirlsare.sexy/wnZM.png
    :align: center
    :alt: Params tab

****

===============================
**How to set it in the module**
===============================

The method must be written as such::

     method = "GET"

The method can only be either ``"GET"`` or ``"POST"`` (once again make sure it is written between apostrophes)

In the case your method is a JSON request, set the method as POST (we'll get to that later)

Pattern
_______

Often giftcard numbers aren't fully random but actually follow a pattern.

Here's an example of 5 valid giftcards for a merchant website::

     12645000021259 --- Value: $25.00
     12645000071777 --- Value: $25.00
     12645000020927 --- Value: $1.46
     12645000054130 --- Value: $0.02

As you might've noticed, here only the last 5 digits actually change with ``126450000`` being the pattern

When setting up a pattern you must only set the parts of the giftcard you do **NOT** want to change, and you will declare what parts you want to generate later on.

To set up a pattern you must do so by writing the following::

     pattern = "126450000" #Always remember the apostrophes

Patterns can also be set to use Alphanumerical characters (letters and numbers) and can be set through regex with the re python librairy

**In the case you're making a module WITHOUT having a valid giftcard before hand/knowing the pattern**

When making modules, you have the option to let the user provide his own valid giftcard for generation instead of providing a pattern. To do so simply set the pattern to None as such::

     pattern = None #None must be written with an uppercase 'N' and **NO** apostrophes this time

This will request the user to input his own valid giftcard upon loading your module.

Pin
___

This will set wether the card has a pin code or not. 

Pin codes (also called Security codes) are usually 3-4 digit numbers that you must enter seperately from the rest of the card. 

Example here:

.. image:: https://b.catgirlsare.sexy/5jhY.png
    :align: center
    :alt: Here the website requires a pincode

You must set the pin argument to either ``True`` or ``False`` (**WITHOUT** apostrophes) as such::

    pin = False

Cookie
______

Cookies can sometimes be passed through requests to set up sessions and can be used as identification. 
While most websites don't usually require you to set up cookies in your requests, some more advanced websites might be using them.

You must set the cookie argument to either ``True`` or ``False`` (**WITHOUT** apostrophes) as such::

    cookie = False

Token
_____

Tokens similarly to cookies are usually used to identify the legitimacy of a request.

They are usually a bunch of generated strings hidden in the page source code that is then sent as arguments in a request. 

These tokens will be different for each request and thus must be fetched before hand to be sent as a query/data/json argument

You must set the token argument to either ``True`` or ``False`` (**WITHOUT** apostrophes) as such::

    token = False

Captcha
_______

Captchas are those annoying "I'm not a robot" boxes that will ask you to solve some shitty puzzle or click on some pictures to access whatever you want to access.

.. image:: https://b.catgirlsare.sexy/pqER.png
    :align: center
    :alt: Example of a captcha

These are security measures to stop bots from bruteforcing requests. Thankfully though, captcha solving services and software exist to counter that issue.

GiftCarder CA only natively supports Recaptcha through solving services such as 2captcha, Anticaptcha, ImageTyperz as well as captcha solving software such as Capmonster and XEvil. Non Recapctha solving might be achievable through solving software such as Capmonster and XEvil but has not been tested.

You must set the captcha argument to either ``True`` or ``False`` (**WITHOUT** apostrophes) as such::

    captcha = False

Site key
________

Site keys are what your captcha solving service will use to identify which captcha to solve. They are usually different for each merchant.

============================
**How to find the site key**
============================

To find the websites site key, the easiest way to do so is to open the Network console (cf the Method section for instructions) and solve the captcha manually.

You should see a bunch of requests like such:

.. image:: https://b.catgirlsare.sexy/cpxD.png
    :align: center
    :alt: Example of a captcha request

Now what interestes you here are the **POST** requests to google.com, simply click on one of them and you should see as request url something like::

    https://www.google.com/recaptcha/api2/userverify?k=6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m

Here the site key is whatever comes after the "?k=" parts. In this case our site key would be ``6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m``

===============================
**How to set it in the module**
===============================

Once the site key has been found, you must declare it as such::

    site_key = "6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m" #MUST BE BETWEEN APOSTROPHES

================================
**What if I don't use Captcha?**
================================

If you set captcha to False, then you must **NOT** remove the site_key argument. You must simply remove whatever is between apostrophes as such::

    site_key = "" #MUST HAVE APOSTROPHES! MUST NOT BE BLANK


Error
_____

GiftCarder CA has an easy and automatic way of handling invalid giftcards, to do so you must simply declare whatever error message the websites returns when a card is invalid

.. image:: https://b.catgirlsare.sexy/vo6C.png
    :align: center
    :alt: Example of an invalid card number

Using this example you can set the errors as such::

    error = ['Invalid card number']

In this example, GiftCarder CA will scan the response of a request and if it finds the keyword "Invalid card number" anywhere it will count the card as invalid.

The errors are declared as Python lists, and must be put in between [square brackets]. The errors in brackets do not need to contain the full error message, and thus you can use multiple keywords (be careful not to be too broad in case a keyword appears somewhere else in the page source which will lead to false negatives)::

    error = ['Invalid card', 'Invalid', 'Invalid pin', 'Error', 'Invalid Captcha']

**Note: If the website has capctha, it is HIGHLY recommended to set the error for an invalid captcha with the others errors, captcha solving technology is not perfect and timeouts + Invalid solving could lead to false positives** 

Retries
_______

If something goes wrong during a request you can set GiftCarder CA to resend the same request in the hopes of a valid response.

Retries does not mean it will retry the request if the website returned a keyword from the error list, but only if the request times out or does not send a valid response

Here you can set the maximum amount of retries (I usually set it to 0)::

    retries = 0 #Max retries limit (Must NOT be in between apostrophes)

Timeout
_______

Some requests may sometimes take longer than others, it is important to set up timeout limits to avoid dormant threads and inactive/looping requests that will never end.

You can set the maximum timeout limit in seconds as such::

    timeout = 8 #Max timeout limit in seconds (Must NOT be in between apostrophes)

It is recommended to not put the limit to low either as this may lead to errors and false negatives with slower internet connections

Headers
_______

A request header is an HTTP header that can be used in an HTTP request, and that doesn't relate to the content of the message. 
More info here https://developer.mozilla.org/en-US/docs/Glossary/Request_header

While GiftCarder CA does automatically take care of headers, some websites require special headers for the request to go through.

**If you do not wish to set custom headers, simply set the following**::

   headers = None #Custom headers, None will use default


==============================
**Example of a custom header**
==============================

In the case where JSON data must be sent, you must set the HTTP Method to **POST** and set custom headers to let the server know the data your sending is encoding in JSON as such::

    headers = {'Content-Type':'application/json; charset=utf-8'}

==================================
**The dynamic headers speciality**
==================================

When a custom header is set, it'll set that header for a Session which controls each request. 

However this may be an issue when dealing with custom proprietary headers, those are thos "X-Something" headers you may sometimes see.

There is a way to set additional custom headers that won't be set to the Session, but actually each individual request.

This option is still in it's infancy, to use it you must do like so::

    def dynamic_header(token, cookie): #It takes as arguments the response to a token request and a cookie request
        header = {'X-Requested-With':'XMLHttpRequest', 'X-XSRF-TOKEN':token} #Here the XSRF token header is the same as the token fetched in token scrapper
        return header
