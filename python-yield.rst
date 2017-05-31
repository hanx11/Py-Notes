===========================================
What does the "yield" keyword do in Python?
===========================================

To understand what *yield* does, you must understand what generators are. And
before generators come iterables.

Iterables

When you create a list, you can read its items one by one. Reading its items
one by one is called iteration:

.. code:: python

    >>>mylist = [1, 2, 3]
    >>>for i in mylist:
    ...    print(i)
    1
    2
    3

 *mylist* is iterable. When you use a list comprehension, you create a list,
 and so an iterable:

 .. code:: python

     >>>mylist = [x*x for x in range(3)]
     >>>for i in mylist:
     ...    print(i)
     0
     1
     4
Everything you can use "for...  in ..." on is an iterable; *list*, *strings*, files...


