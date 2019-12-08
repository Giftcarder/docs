How to use GiftCarder CA
========================

.. |br| raw:: html

   <br />

Is it your first time using GiftCarder CA, or a checker in general?

Here you'll learn how to properly take advantage of GiftCarder's many features.



First Launch
-------------

Once you've downloaded GiftCarder CA for the first time from https://giftcarder.ca/download

We recommend you set up the executable file (.exe) in an empty folder, like so:

.. image:: http://japan.u.catgirlsare.sexy/L4C3.png
    :align: center
    :alt: Set it up in an empty folder

When you run it for the first time, it should create 2 folders and a file like so:

.. image:: http://japan.u.catgirlsare.sexy/d39u.png
    :align: center
    :alt: New folders are made when you launch the soft for the first time

Here it'll create a folder called ``modules`` where you can put your own custom modules

As well as a folder called ``results`` where it'll save your various giftcard hits.

And finally, a file called ``debug.log`` which will log any crashes or issues the software may experience so that the staff team may help you resolve the issues.



Logging in
----------

Once you've launched GiftCarder CA for the first time, you'll be greeted with this logging screen asking for a key

.. image:: http://japan.u.catgirlsare.sexy/OcKJ.png
    :align: center
    :alt: Logging screen

Here you have to paste the license key you received from your shoppy.gg order (which can be found in the email shoppy sent you after your purchase)

To paste your key in the command prompt simply right click after copying it.

On your first run you should be greeted to the following messages:

.. image:: http://Japan.u.catgirlsare.sexy/PV2z.png
    :align: center
    :alt: Don't wory this is totally normal

Don't worry, this is totally normal, after a few seconds it should change to this:

.. image:: http://japan.u.catgirlsare.sexy/95Xy.png
    :align: center
    :alt: This means the key has been registered

Now you're all set to go! The software will automatically save your key to a ``key.key`` file in the same folder as the .exe, so that you don't have to rewrite your key each time you launch the software

If you happen to have an issue such as your key returning invalid even though it's not, feel free to open a ticket on our discord: https://giftcarder.ca/invite

Select Menu
-----------

After logging in, you should be met with a select screen

.. image:: http://Japan.u.catgirlsare.sexy/1fMm.png
    :align: center
    :alt: Select Menu

From there you can either decided to check and generate giftcards by inputting ``1`` or decide to make your own module through the module maker by inputting ``2`` (check module making section of these docs for help)


Selecting a Module
------------------

Once you've chosen to check and generate modules, you should be greeted to a menu like so:

.. image:: http://japan.u.catgirlsare.sexy/p4Mm.png
    :align: center
    :alt: Module Select Menu

Here you'll see a list of all the current modules you can choose from. The software will automatically tell you what modules require captcha solving, a valid giftcard or proxies:

.. image:: http://japan.u.catgirlsare.sexy/AqSQ.png
    :align: center
    :alt: Module Select 

For a nicer list of the modules, you can check https://giftcarder.ca/modules

Now to select what module you'd like to load you need to input the module's ``id`` which is the number on the left of the module's name, so if you wanted to load ``ZiosItalianKitchen`` you'd input ``2680``


Options Menu
-------------

Once you've selected a module you'd like to use by inputting their id, you'll be greeted to a menu like this:

.. image:: http://japan.u.catgirlsare.sexy/Wbux.png
    :align: center
    :alt: Options Menu
	
Here you are given 3 options of giftcard checking modes


Random Mode
~~~~~~~~~~~

Random Mode is the classic giftcard checking mode, it'll generate giftcards by randomizing a few digits of a valid giftcard that's either pre-included or that you'll have to input yourself.


Range Mode
~~~~~~~~~~

Range mode works by checking every giftcard between two numbers.

Example, if you use range mode to check between the giftcard code ``60060000500`` and the giftcard code ``60060001400``, it'll generate and check 900 giftcards starting with 60060000501, 60060000502, 60060000503, etc... Up to 60060001400


Combolist Mode
~~~~~~~~~~~~~~

Like a normal checker, GiftCarder CA also supports importing your own pre-generated giftcard numbers to be checked by the software, to do so simply select combolist mode and import your card codes from a .txt file



Random Mode options
-------------------

Once you've selected the random mode, you'll be prompted to a few more settings before you can check your giftcard numbers


1) First, you'll be asked how many giftcards you'd like to generate (this is straight-forward, simply input a number like 1000 or 10000)


2) If the module is numerical, it'll ask you if you want to use the luhn algorithm, what is the luhn algorithm? The luhn algorithm is a simple mod 10 checksum algorithm usually used to check the validity of credit cards numbers before even having to check if the credit card exists or not. |br| 
For more info on what the luhn algorithm is and how it works, you can go here: https://www.geeksforgeeks.org/luhn-algorithm/ |br|  |br| 
Now how do I know if I should activate the luhn algorithm when checking or not? If you have a valid giftcard, you can check if it's luhn valid here: https://www.dcode.fr/luhn-algorithm |br|  |br| 
If you don't have a valid card, you can gamble between activating it or not, the more digits you're randomizing the more I would recommend using the luhn algorithm. But in general if you truly don't know if the website's card uses luhn or not, I would recommend simply going the safe route and not activating it.


3) Next you'll be asked if you'd like to use proxies, if the module requires proxies simply input ``1``. **Reminder:** GiftCarder CA only works with HTTP/S proxies, and HQ proxies are recommended. (If you forgot to check if the module requires proxies in the module select menu, you can still check here: https://giftcarder.ca/modules)


4) You'll then be asked how many concurrent workers you'd like to set, use this as threads. More Workers = More simultaneous requests, basically how many cards you want to allow the software to check at the same time, **but** too many may make the software slower and make the website block your requests (I'd recommend between 20 and 30 workers)


5) Then you'll be asked to set how many concurrent connections you'd like to set up, if you don't know what this is simply put the same as the amount of workers.


6) Then you'll be asked if you want to activate the real time log, this will show you what cards are being checked and what cards are valid and invalid in real time


7) If you do activate the real time log, you'll be asked if you want to show the errors or not. If you activate this feature, errors such as Timeouts, Connection Issues, Scrapping issues, etc... Will show up on the real time log (this is good for debugging a module you made for example), if you don't activate it, it will simply just count errors as an invalid card


8) If your module requires captcha solving, it'll ask you what captcha solving service you'd like to use, these are paid services you need to purchase an api key for (unless you bought a captcha solving software like Capmonster or XEvil)


9) If you selected a captcha solving service, you'll be asked to input the api key you bought when purchasing one of the captcha solving services. (It will not ask for a license key if you bought Capmonster or XEvil)


10) If the module has a valid giftcard pre-included, it'll ask you if you'd like to use that giftcard as a pattern or if you'd rather add your own. If it doesn't have a valid giftcard it'll automatically ask you to input your own.


11) Once the valid giftcard has been set, it'll ask you how many digits you'd like to randomize (example: inputting ``4``, will randomize the last 4 digits of the valid card)

Tadaa! You are now generating and checking giftcards.


Once finished
-------------

Once finished the software will display how many cards were checked, and how many valid and invalid cards you got. The software will then pause, pressing any key will return to the Select Menu. 

You can find your hits in the results folder next to the .exe file.
