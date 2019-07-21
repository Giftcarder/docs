Getting Started
===============

A "little" example
____________________

**To get us started with module making, let's use a theoretical example.**

Let's say we have a website https://example.com that has a giftcard balance checker at the url https://example.com/balance

Now this example website is let's say very primitive, and does not require a pin, captcha, cookie or token

Upon checking it will return a blank page with as response the card value such as: ```10.00``` if valid and ```0.00``` if invalid

Here's a commented sample module::

        # Example_module[No][No][Yes].py
        # coding: utf8

        #======================= IMPORT AREA =======================
        #here's where you import any module needed for the website
        from random import randint
        #===========================================================

        #====================== SETUP AREA ======================
        #here's where you declare the settings of the website such
        #as method, error key, success key, custom settings, etc...
        name = "Name to be displayed" #Name to show when loaded
        method = 'POST' #Method is either GET or POST (JSON should also be POST) (case insensitive)
        pattern = None #Static Pattern/valid giftcard
        #Setting the pattern to None will prompt the user to input theirs
        pin = False #Does the config has pin? True/False
        cookie = False #Does the config require Cookie Session? Trye/False
        # Cookie implemntation is still in it's experimental stages
        # and thus is for Advanced users only
        token = False #Does the config require token? True/False
        #Setting token to True will require a token_scrapper() and token_request() def
        captcha = False #Does the congif require captcha support? True/False
        captcha_key = None #Your captcha API key
        #Setting captcha_key to None will prompt the user to enter theirs
        site_key = "" #The website captcha key (see docs for help)
        error = ['0.00']
        success = None #same format as error, None means it'll accept anything that isn't an error
        retries = 0 #Max retries limit
        timeout = 8 #Max timeout limit in seconds
        headers = None #Custom headers, None will use default


        #===========================================================

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


Now you might be a bit confused at all of this, and that's totally fine, but don't worry by following the examples and guides for each area, you'll be up and making modules in no time! ;)