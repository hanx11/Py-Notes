================
Python Decorator
================

**Decorator Basics**

**Python's functions are objects**

`How To Make A Chain Of Function Decorators <http://stackoverflow.com/questions/739654/how-to-make-a-chain-of-function-decorators/1594484#1594484>`_

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

**Functions references**

Okay, still here? Now the fun part...

You've seen that functions are objects. Therefore, functions:

  * can be assigned to a variable
  * can be defined in another function

That means that a function can return another function.

.. code:: python

    def getTalk(kind="shout"):
    
        # We define functions on the fly
        def shout(word="yes"):
            return word.capitalize() + "!"

        def whisper(word="yes"):
            return word.lower() + "..."

        # Then we return one of them
        if kind == "shout":
            # We don't use "()", we are not calling the function
            # we are returning the function object
            return shout
        else:
            return whisper

    # How do you use this strange beast?

    # Get the function and assign it to a variable
    talk = getTalk()
    
    # You can see that "talk" is here a function object:
    print(talk)
    # outputs:  <function shout at 0xb7ea817c>

    # The object is the one returned by the function:
    print(talk())
    # outputs: Yes!

    # And you can even use it directly if you feel wild:
    print(getTalk('whisper')())
    # outputs: yes...

There's more!

If you can return a function, you can pass one as a parameter:

.. code:: python

    def doSomethingBefore(func):
        print("I do something before then I call the function you gave me")
        print(func())


