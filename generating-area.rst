Generating Area
===============

Introduction
____________

Since modules are written in Python, they use Functions which are called "Definitions", these "defs" are functions that the software will run. 
More info here: https://www.tutorialspoint.com/python/python_functions

=============
**Example**
=============
little example code::

        #====================== DEFINITON AREA =====================
        #here's where the definitions are made.
        #There's 5 "default" defs:
        #async def cardcode(): which gives the cardcode generating algorithm
        #async def pincode(): which gives the pincode generating algorithm
        #def request(): Which returns the url
        #async def scrapper(): This is used to scrap the value of the giftcards
        #                Leave it empty to save valid giftcards without their value
        #def settings(): returns the data to send in the GET request


        #====== GENERATING AREA ======
        async def cardcode(cardcode = pattern): #Code that generates the code
                for x in range(5): #length of the rest of the cardcode to be generated (here it's 5)
                    #if pattern is set to None set range to 5
                    cardcode += str(randint(0,9))
                return cardcode

        async def pincode(pincode = ""):  #pattern if there's one, else put ""
                for x in range(4): #length of the pin to be generated (here it's 4)
                    pincode += str(randint(0,9))
                return pincode

        #===========================================================

======
Basics
======

Each module has 2 "basic" defs that you must use:

- async def cardcode(cardcode = pattern):

- async def pincode(pincode = "x"):


As you might've noticed some functions have the keyword "async" before the "def" one. This simply just state that the function must be run asynchronously. But don't worry about it, all you need to know is that async defs **MUST** have the async tag and non-async defs **MUST NOT** have the async tag.



async def cardcode
__________________
This is the main "cardcode generating algorithm", this is the function that will generate the main card.

==============
**The basics**
==============

The def must start with ``async def cardcode(cardcode = pattern):`` and end with ``return cardcode``

Like so::

    async def cardcode(cardcode = pattern):
        return cardcode #Be sure to respect the Python indentation

==================
**The generating**
==================

To start off with, the ``async def cardcode`` automatically sets a variable called ``cardcode`` which just happens to be the pattern. If you set a pattern in the SETUP AREA then carcode will be equal to whatever pattern you put. However if you put pattern to ``None`` in the setup Area, then GiftCarder will automatically provide a pattern by taking the valid giftcard provided by the user **and removing the last 5 digits/characters**. This is important because if you did not provide a pattern, you must make sure to only generate 5 characters/digits as to avoid generating cards with incorrect lengths.

**Example**
-----------

Here in this example let's say you set pattern to None or that you want to generate a 5 digit code, you would use the **random** python library to generate code (cf: the Import Area) (don't forget to import it like such ``from random import randint`` and check the docs https://docs.python.org/3/library/random.html)::

    async def cardcode(cardcode = pattern): #Code that generates the code
            for x in range(5): #length of the rest of the cardcode to be generated (here it's 5)
                #if pattern is set to None set range to 5
                cardcode += str(randint(0,9))
            return cardcode

Here ``randint(0,9)`` will return a random number between 0 and 9 as an int. Since we want it as an str and not an int, we'll write it as ``str(randint(0,9))``

``for x in range(5):`` means it'll repeat the operation 5 times

``cardcode += str(randint(0,9))`` basically means ``cardcode = cardcode + {a random number between 0 and 9}`` with cardcode being equal to the pattern

Thus::

            for x in range(5):
                cardcode += str(randint(0,9))

means it'll take the pattern and add 5 random numbers to it. If we were to run this with ``pattern = "123"`` it would return something like ``12357109``

You can then combine this with the "string" librairy for alphanumerical cardcodes.

async def pincode
__________________
This is the exactly the same thing as ``async def cardcode`` but for pincodes.

===============
**The basics**
===============

The def must start with ``async def pincode(pincode =""):`` and end with ``return pincode``

Like so::

    async def pincode(pincode = ""):
        return pincode #Be sure to respect the Python indentation


==================
**The generating**
==================

To start off with, the ``async def pincode`` automatically sets a variable called ``pincode``, usually pincodes don't have any patterns and thus we set ``pincode = ""`` in the function. 

If it would happen however the pincode did have a pattern, you could simple set it by doing::

    async def pincode(pincode = "pattern here"):
        return pincode #Be sure to respect the Python indentation
