Import Area
===========


What is it?
___________

In the programming language Python, you can "import" bundled code to make your tasks easier. 

These bundles of code come in what's called a library, using the import statement, you can easily load the library's code without having to rewrite it yourself.

Some libraries can be native to Python such as the "random" library, but some others can be made by third-parties.

How do I use it?
________________

To import a library in your module, simply type the following in the import area::

        import example

This will import the library called "example". Now if the library example has a function "do_stuff()", you can now use it by typing::

        example.do_stuff()

****

To facilitate importing, you can also simply import a function from a library on it's own as such::

        from example import do_stuff
        #And now you can easily run the do_stuff function with specifying the example library by typing:
        do_stuff()

You may also import multiple functions from a same library::

        from example import do_stuff, do_things, do_something

What libraries can I import?
____________________________

The software comes pre-included with every Python 3 native library, and thus you can import any one of them following your needs (more info here: https://docs.python.org/3/library/) (The most useful library you'll probably have to import is the "random" library)

But GiftCarder CA also includes 3 third party libraries to make your module making experience easier.
These modules are essentially for the scrapping of tokens and value:

- The lxml library (for XML and html scrapping with XPath) (docs: https://lxml.de/index.html)

- The BeautifulSoup4 library (for html scrapping) (docs: https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

- The ujson library (for fast json scrapping) (docs: https://pypi.org/project/ujson/) (this might replaced by rapidjson in the future)
 
 
Since GiftCarder CA's module processor is based on Python, any other third party python library you'd like to use can be included by sending me a request on Discord/Telegram/Email
