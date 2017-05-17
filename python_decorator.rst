================
Python Decorator
================

**Decorator Basics**

**Python's functions are objects**

To understand decorators, you must first understand that functions
are objects in Python. This has important consequences. Let's see
why with a simple example:

.. code:: python
    
   def shout(word='yes'):
        return word.capitalize() + '!'

    print(shout())
    # ouputs: 'Yes!'

    # As an object, you can assign the function to a variable like any
    # other object
    scream = shout

    # Notice we don't use parentheses: we are not calling the function,
    # we are putting the function "shout" into the variable "scream".
    # It means you can then call "shout" from "scream":

    print(scream())
    # outputs: 'Yes!'

    # More than that, it means you can remove the old name 'shout',
    # and the function will still be accessible from 'scream'

    del shout
    try:
        print(shout())
    except NameError as e:
        print(e)
    # outputs: "name 'shout' is not defined"

    print(scream())
    # outputs: 'Yes!'

Keep this in mind. We'll circle back to it shortly.

Another interesting property of Python functions is they can
be definded inside another function!

.. code:: python
    
    def talk():
        # You can define a function on the fly in "talk"...
        def whisper(word='yes'):
            return word.lower() + '...'

        print(whisper())

        # You call "talk", that define "whisper" EVERY TIME you call it,
        # then "whisper" is called in "talk".

    talk()
    # outputs: 
    # "yes..."

    # But "whisper" DOES NOT EXIST outside "talk":

    try:
        print(whisper())
    except NameError as e:
        print(e)
    # outputs: "name 'whisper' is not defined"
    # Python's functions are objects

