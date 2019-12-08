Using the module maker
======================

Here you'll learn how to make your first Giftcarder CA module using the included module maker

Getting Started
---------------

First things first, to start creating your own modules you'll need to launch the Module Maker, to do so, select the second option in the Select Menu screen by inputting ``2`` and pressing your ``Enter`` key

.. image:: http://japan.u.catgirlsare.sexy/yulz.png
    :align: center
    :alt: If you actually needed help with this you must be mentally thick

Choosing a Name
---------------

The first step of your module making process is to name your soon to-be module. You should see a screen like this when you first launch the module making process:

.. image:: http://japan.u.catgirlsare.sexy/QdBI.png
    :align: center
    :alt: Spirit, movin' around, just movin' around
	
This is the name that'll be displayed when a user selects your module. You can use spaces, punctuation and special characters (as long as they can be displayed by the windows CMD), **however** spaces and punctuation will be automatically removed from the module's filename.

As an example, if you name your module ``Faygo Dreams@?!!``, it'll display the name ``Faygo Dreams@?!!`` when the module is selected, but the filename of the module will automatically be set to ``FaygoDreams.py`` and by such it will only be displayed as ``FaygoDream`` in the module select menu.


Selecting a HTTP Request Method
--------------------------------

On the next step you'll be prompted to choose one of free request methods, ``GET``, ``POST`` and ``JSON``:

.. image:: http://japan.u.catgirlsare.sexy/IdAn.png
    :align: center
    :alt: 1 is for GET, 2 is for POST, 3 is for JSON

If you are not familiar with HTTP methods and Networking, when you send a request to a server, it will be setup in a certain way, usually either GET or POST, for more info on methods: https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

Now to find out what method the website is using when checking for balance, you must open the Network tool (CTRL+SHIFT+E on Firefox and Control+Shift+J on Chrome)

This should open up a tool like this (Firefox):

.. thumbnail:: https://b.catgirlsare.sexy/S_AM.png
    :align: center
    :alt: Network tool (Firefox)

Now simply try and check your card balance (usually by clicking a button after inputting a card number), and you should see some requests are being made to the website as such:

.. thumbnail:: https://b.catgirlsare.sexy/-8Ja.png
    :align: center
    :alt: Network tool (Firefox)

Here we can see that the browser is sending a **POST** request to the url https://buffalobrewpub.alohaenterprise.com/efMemberLinkLogin.do.

If you are unsure which request is the one that checks the card balance, simply head over to the "Params" tab and check if the card number you put is there or not:

.. image:: https://b.catgirlsare.sexy/wnZM.png
    :align: center
    :alt: Params tab

JSON's case
~~~~~~~~~~~

Now in the case of sending JSON data, it'll actually usually be displayed as a POST request in the Network tool. However you can find out if you're sending JSON data by heading over to the "Params" tab and looking at the type of data that is sent. If it displays the data as ``Form Data`` that means it's a regular POST request, however if it displays ``JSON`` that means it's sending JSON data, example:

.. image:: http://japan.u.catgirlsare.sexy/N4_m.png
    :align: center
    :alt: JSON data in a POST request example

Adding a valid giftcard
-----------------------

Next you'll be asked if you have a valid giftcard for your module. Like so:

.. image:: http://japan.u.catgirlsare.sexy/vbAj.png
    :align: center
    :alt: Dab <o/

Importing a valid giftcard is very important for creating a module as that's what the software will use as reference while generating other card numbers. Your valid giftcard number doesn't necessarily need to have any remaining balance or even still be active for it to work. If you do not have a valid giftcard for your module it'll automatically ask each user to input theirs when it they load your module.

Card type
---------

Next step is selecting the card type Giftcarder will generate. You'll be greeted with a menu similar to this:

.. image:: http://japan.u.catgirlsare.sexy/3YGE.png
    :align: center
    :alt: At first you'll only be greeted with "What is the module's card type?"

Numerical Card Type
~~~~~~~~~~~~~~~~~~~

The Numerical card type is the classic basic card type.

As the name implies, GiftCarder will only generates numbers from 0-9 if you select this card type. **However** this doesn't necessarily mean the card can't have any ASCII characters (without the nerd terms: letters) in it.

**Example without letters in it:**

Let's say a valid card is ``600600000000``, well if you select the Numerical card type, GiftCarder will generate cards like ``600600000578``, ``600600000095``, ``600600007849``, etc... (depending on how many digits you decide to randomize)

**Example with letters in it:**

Let's say a valid card is ``CARD-123456789``, well if you select the Numerical card type, GiftCarder will generate cards like ``CARD-123450348``, ``CARD-123456349``, ``CARD-123783498``, etc... (depending on how many digits you decide to randomize)

Alphabetical Card Type
~~~~~~~~~~~~~~~~~~~~~~

The Alphabetical card type will generate random characters from A-Z, a-z or both.

You are given 3 choices of Alphabetical card types:

**Uppercase cards**

This will only generate characters from A-Z (ABCDEFGHIJKLMNOPQRSTUVWXYZ), as an example: if your valid card is ``AAAAFHDEJEU``, GiftCarder will generate ``AAAAFJKNCOP``, ``AAAAFHDJIOP``, etc... (depending on how many characters you decide to randomize)

**Lowercase cards**

This will only generate characters from a-z (abcdefghijklmnopqrstuvwxyz), as an example: if your valid card is ``aaaafhdejeu``, GiftCarder will generate ``aaaajberopez``, ``aaaafhdenvp``, etc... (depending on how many characters you decide to randomize)

**Mixed Cards**

This will generate characters from A-z (ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz), it will randomly choose between uppercase and lowercase (default odds are 50/50 but you can edit this manually), as an example: if your valid card is ``AaaAFhdEnvP``, GiftCarder will generate ``AaaAFYiPmNo``, ``AaaRiOpMzEe``, etc... (depending on how many characters you decide to randomize)

Alphanumerical Card Type
~~~~~~~~~~~~~~~~~~~~~~~~

The Alphanumerical card type will generate random characters from A-Z, a-z, 0-9 or all three. So basically it's just a mix of the two previous card types

You are given 3 choices of Alphanumerical card types (the same as the Alphabetical ones), but you aren't retarded so I won't write each example again

Pin Generation
--------------

Next up on the list, you'll be asked if your module requires to generate a pin number.

Pin codes (also called Security codes) are usually 3-4 digit numbers that you must enter seperately from the rest of the card. 

Example here:

.. image:: https://b.catgirlsare.sexy/5jhY.png
    :align: center
    :alt: Here the website requires a pincode
	
If your module does require a pin to be generated, the software will then ask you to specify how many digits the pin is (basically how long is it, 2-3-4-etc... Digits)

Specifications
~~~~~~~~~~~~~~

By default pin numbers are numerical and don't included a pattern, however if you would like to add a pattern to your pin number or generate pins that aren't numerical, please reference yourself to :ref:`pincode-reference-label`.

Captcha Solving
---------------

Subsequently, you'll be asked if your module requires captcha solving:

.. image:: http://japan.u.catgirlsare.sexy/XV1E.png
    :align: center
    :alt: Here the website requires a pincode

Captchas are those annoying "I'm not a robot" boxes that will ask you to solve some shitty puzzle or click on some pictures to access whatever you want to access.

.. image:: https://b.catgirlsare.sexy/pqER.png
    :align: center
    :alt: Example of a captcha

These are security measures to stop bots from bruteforcing requests. Thankfully though, captcha solving services and software exist to counter that issue.

GiftCarder CA only natively supports Recaptcha through solving services such as 2captcha, Anticaptcha, ImageTyperz as well as captcha solving software such as Capmonster and XEvil. Non Recapctha solving might be achievable through solving software such as Capmonster and XEvil but has not been tested.

Sitekeys
~~~~~~~~

If your module does require captcha solving, the software will ask you to input a Sitekey, Sitekeys are what your captcha solving service will use to identify which captcha to solve. They are usually different for each merchant.

**How to find the Sitekey?**

To find the website's Sitekey, the easiest way to do so is to open the Network console (cf the Method section for instructions) and solve the captcha manually.

You should see a bunch of requests like such:

.. thumbnail:: https://b.catgirlsare.sexy/cpxD.png
    :align: center
    :alt: Example of a captcha request

Now what interestes you here are the **POST** requests to google.com, simply click on one of them and you should see as request url something like::

    https://www.google.com/recaptcha/api2/userverify?k=6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m

Here the site key is whatever comes after the "?k=" parts. In this case our site key would be ``6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m``

So you'll have to paste in ``6LdndBYUAAAAAIE_sQA2y29GSRaKJHKx2DodPT6m``, to do so simply copy the text through **CTRL+C** or by right clicking it, and then to paste it in the console simply **right click again**

Proxies
-------

Next you'll be asked if your module requires proxies:

.. image:: http://japan.u.catgirlsare.sexy/uy6W.png
    :align: center
    :alt: I'm so fucking tired, I don't know what to write anymore
	
Basically if your website will block you from sending requests/accessing the website from a certain IP after a few tries, that means you need to use proxies.

Inputting that your module requires proxies will not force the user to use proxies however, so it's recommend you take that information into account when listing the Invalidating keywords

Retries
-------

Next you'll be asked the amount of retries you'd like to set:

.. image:: http://Japan.u.catgirlsare.sexy/9v_r.png
    :align: center
    :alt: If you screen this and send it in DMs I'll send you a Gazillion dollars

Retries means that if the request couldn't go through properly, it'll try sending the same request again. This does not mean it'll send a new request if it receives a Timeout, Connection Issue, 404 or other valid HTTP responses.

Timeout
-------

A timeout is how long you'll allow a request to be "pending" for before it skips the request. 

.. image:: http://japan.u.catgirlsare.sexy/qJwf.png
    :align: center
    :alt: Actually I lied about the gazillion dollars
	
Some requests may sometimes take longer than others, it is important to set up timeout limits to avoid dormant threads and inactive/looping requests that will never end. Usually 8-10 seconds is in the safe range.

Custom Headers
--------------

Next up we have custom headers, GiftCarder will ask if you require custom headers to be set

.. image:: http://japan.u.catgirlsare.sexy/AkgP.png
    :align: center
    :alt: Headers selection menu

A request header is an HTTP header that can be used in an HTTP request, and that doesn't relate to the content of the message. 
More info here https://developer.mozilla.org/en-US/docs/Glossary/Request_header

While GiftCarder CA does automatically take care of headers, some websites require special headers for the request to go through.

Example of custom headers
~~~~~~~~~~~~~~~~~~~~~~~~~

Let's say you want to set the custom header ``X-Request-With`` (You can see what headers are being passed by using the inspector tool)

.. image:: http://japan.u.catgirlsare.sexy/Q_lI.png
    :align: center
    :alt: Headers on the inspector tool

You'll be greeted with a GUI table to input values in, like so:

.. image:: http://japan.u.catgirlsare.sexy/Gfd6.png
    :align: center
    :alt: Headers GUI
	
Once you're finished you can press ``Done``

If you don't set some Headers such as User Agents, GiftCarder CA will take care of setting them automatically.

Error keywords
--------------

To detect if a card is invalid or not, GiftCarder will scan the website's response source code for keywords

Here's an example of an invalid response code:

.. image:: http://japan.u.catgirlsare.sexy/XbtK.png
    :align: center
    :alt: Invalid Card example
	
You'll then be greeted with a GUI to input invalidating keywords like such:

.. image:: http://japan.u.catgirlsare.sexy/Rj3p.png
    :align: center
    :alt: Invalid Card GUI

The more keywords you put the better, because it'll reduce the risks of false positives. 

**Reminder:** You need to take into account every invalid response possibility and set a keyword for each of them in case they return different responses (Invalid captcha, Invalid cardcode, Server error, Expired card, Card with $0 balance, etc...)

Request URL
-----------

The url the request is sent to might not always be the same than the url of the webpage the balance checker is on, you'll have to paste what url you want to send the requests to:

.. image:: http://japan.u.catgirlsare.sexy/FX3c.png
    :align: center
    :alt: Invalid Card GUI


To find what url the request is sent to, you need to open the Network console (cf: the Method section of Setup Area)

Here we can see the Request URL is http://buffalobrewpub.alohaenterprise.com:8080/efMemberLinkLogin.do while the actual website url is https://buffalobrewpub.alohaenterprise.com/memberlink/GiftCards.html?companyID=bbp01

.. image:: https://b.catgirlsare.sexy/Q5r4.png
    :align: center
    :alt: Request Url

Tokens
------

Tokens are usually small strings hidden a webpage's source to identify the validity of a request.

If the website you're trying to brute uses token, you must scrap and pass them in the request. That's why the software will ask you if your module uses token:

.. image:: http://japan.u.catgirlsare.sexy/YyV6.png
    :align: center
    :alt: Tokens or something idk

How to know if you need to scrap tokens
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Generally, if there's a query/form data with a random string of characters that changes each request, there's a high probability that it's a token.

Example here:

.. image:: http://japan.u.catgirlsare.sexy/OJVR.png
    :align: center
    :alt: Comm'on guess which one is the token

What url do I scrap it from
~~~~~~~~~~~~~~~~~~~~~~~~~~~

If your website does require a token, you need to scrap it from an url's source code, you can usually find it on the actual webpage you're on (which is not necessarily the same as the request url).

You can confirm this by right clicking the page you're on, clicking ``View Page Source`` and looking for the token (CTRL+F)

Here's an example :

.. image:: http://japan.u.catgirlsare.sexy/q5Zr.png
    :align: center
    :alt: Authenticity Tokens

**Disclaimer:** This is just an example, the token isn't always going to be called "AuthenticityToken", it might very well be called "_" or "NE0Z5IU4JH6CIU4HZEF" or "HoesMad"

Then you can input the **full** url (that includes the https://):

.. image:: http://japan.u.catgirlsare.sexy/zmTl.png
    :align: center
    :alt: Hoes are truly mad
	
Scrapping the token
~~~~~~~~~~~~~~~~~~~

Once you input the url, GiftCarder CA will automatically send a GET request to that URL and record the response's source code, it will then prompt you to select a scrapping method between Regex and XPath (I recommend XPath for tokens as it's especially made for scrapping html source codes)

.. image:: http://japan.u.catgirlsare.sexy/3rO6.png
    :align: center
    :alt: Choose your own scrapping method

You can find tutorials for XPath and Regex here:

- XPath (https://www.w3schools.com/xml/xpath_intro.asp)

- Regex (https://regexone.com/lesson/introduction_abcs)

Once you select the desired scrapping method, it'll load an interractive testing GUI where you can write your regex or XPath expression and test it against the automatically scrapped source code of the website you input previously.

Like so here with XPath:

.. image:: http://japan.u.catgirlsare.sexy/3np3.png
    :align: center
    :alt: XPath GUI

Once you've verified your regex or XPath expression works properly, you can press the ``Done`` button

Cookies
-------

Cookies can sometimes be passed through requests to set up sessions and can be used as identification or tracking. 

While most websites don't usually require you to set up cookies in your requests, some more advanced websites might be using them.

That's why the software will prompt you to decide if the module requires cookies or not:

.. image:: http://japan.u.catgirlsare.sexy/E9uR.png
    :align: center
    :alt: Hmmm chocolate cookies 


How to know if you need to scrap cookies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The best way is through testing, by sending valid requests with a valid giftcard with and without cookies. But some cookie names may tip you off

Example:

.. image:: http://japan.u.catgirlsare.sexy/nPmd.png
    :align: center
    :alt: Stop fiddling kids u nonce
	
Here you can see a specific cookie that isn't your generic trackers / generic cookies, that's being set every session. Removing said cookie will return ``403``, there you can be fairly certain the cookie is necessary

What url do I scrap it/them from
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Most cookies will be set the first time you visit a website, you can test this by clearing your cookies for the website and revisiting the website with the Network tool on, just check each request to the said website on the Network Tool and look when the cookies are set for the first time. You'll see this in the ``Response Cookie`` section, like so:

.. image:: http://japan.u.catgirlsare.sexy/FSgI.png
    :align: center
    :alt: Nice blur

Then you can input the **full** url (that includes the https://):

.. image:: http://japan.u.catgirlsare.sexy/oHwU.png
    :align: center
    :alt: Hey that's my website!

Selecting the cookies
~~~~~~~~~~~~~~~~~~~~~

Once you input the url, GiftCarder CA will automatically send a request to that url and return the cookies that are set, like so:

.. image:: http://japan.u.catgirlsare.sexy/AURm.png
    :align: center
    :alt: Hey that's my website!

You can then select the cookie(s) you want by typing it's/their id(s) (if you want to select multiple cookies, you must seperate them by a comma like in the example above)

Params/Data to be sent
----------------------

Next up is the params/data to be sent in your request. You'll have a GUI similar to the Headers GUI where you can input the params' name and value.

Finding what params/data is supposed to be sent is easy, to do so simply use the network console (cf: the Method section in Setup Area) and click the Params tab

.. image:: https://b.catgirlsare.sexy/wnZM.png
    :align: center
    :alt: Params tab

Here this data would give use this:

.. image:: http://japan.u.catgirlsare.sexy/XvX3.png
    :align: center
    :alt: Params tab
	
As you can see the cardcode value is replace by the ``%cardcode%`` variable. You can set 4 variables as either the name or value of any param/data. These include:

- ``%cardcode%`` which will return the generated giftcard
- ``%pincode%`` which will return the generated pin number (if there is one)
- ``%token%`` which will return the token (if there is one) that we scrapped as explained previously
- ``%captcha%`` which will return the captcha solution code used to validate the request if it has a reCaptcha challenge

**Reminder:** You don't have to add all of them if they aren't being used, as seen in the example.

And press ``Done`` once you're finished

Value Scrapping
---------------

This is the final step, in exact same way you scrap a token, you'll be greeted to a choice between XPath and Regex to scrap the value of your card, like so:

.. image:: http://japan.u.catgirlsare.sexy/KaRH.png
    :align: center
    :alt: You probably get it by now

Now once you make up your mind, you'll be asked if you want to set a currency symbol (and if you do which one)

.. image:: http://japan.u.catgirlsare.sexy/sHMq.png
    :align: center
    :alt: You probably get it by now

This is because sometimes GiftCard balances may on return the value as ``20.0`` or ``5.00`` and not specify if it's $20, 20€, etc... So you have the option to add a currency in front of each and any value your scrapper will fetch. (Simply press ``enter`` without actually entering anything if the website automatically displays the currency and your scrapper automatically fetches it).

Now you'll be greeted to the same Interactive GUI you got for token scrapping (this time I took Regex)

For the sake of testing and accuracy, you'll have to paste the response code with the value yourself (to avoid the software from messing up when sending the request automatically and receiving a response that doesn't include the card's value). To do so simply copy the source code of the webpage where the value is displayed.

Here's an example with regex:

.. image:: http://japan.u.catgirlsare.sexy/9Oqx.png
    :align: center
    :alt: I ran out of dumb things to say

Again, you can find tutorials for XPath and Regex here:

- XPath (https://www.w3schools.com/xml/xpath_intro.asp)

- Regex (https://regexone.com/lesson/introduction_abcs)

Once you're satisfied with your Regular Expression, click on ``Done``

The Recap
---------

Once you've finally finished each and every step, you'll be prompted a recap of all your module settings, like such:

.. image:: http://japan.u.catgirlsare.sexy/Xyep.png
    :align: center
    :alt: You probably get it by now

You can now confirm that all the data is correct, and if it is not simply input ``2`` to say it isn't, and you'll have the choice to re-edit and redo any of the steps you took previously (you can repeat the process as many times as you want until you're satisfied with the settings of your module)

Once everything is confirmed, you'll finally receive the glorious message that is:

.. image:: http://japan.u.catgirlsare.sexy/ZC4U.png
    :align: center
    :alt: I can finally fuck off now
	
The End
-------

Once the Module is generated, it'll be automatically placed in your ``modules`` folder next to the software's .exe file

Like such:

.. image:: http://japan.u.catgirlsare.sexy/mtwn.png
    :align: center
    :alt: I can finally fuck off now

You'll be able to load it by going in the Module Selection Menu. Your module (as well as any other custom module in your ``modules`` folder) will show up in a purple to be differentiated, like so:

.. image:: http://japan.u.catgirlsare.sexy/e-4i.png
    :align: center
    :alt: I can finally fuck off now

You can now test and debug your module.





