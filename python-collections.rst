========================================================
8.3. collections -- High-performance container datatypes
========================================================

New in version 2.4

Source code: `Lib/collections.py <https://github.com/python/cpython/blob/2.7/Lib/collections.py>`_ and `Lib/_abcoll.py <https://github.com/python/cpython/blob/2.7/Lib/_abcoll.py>`_

This module implements specialized container datatypes providing alternatives
to Python's general purpose built-in containers, dist, list, set, and tuple.

+-------------+---------------------------------------------------------------------+-------------------+
|namedtuple() |factory function for creating tuple subclasses with named fields     |New in version 2.6 |
|             |                                                                     |                   |
+-------------+---------------------------------------------------------------------+-------------------+
|deque        |list-like container with fast appends and pops on either end         |New in version 2.4 |
|             |                                                                     |                   |
+-------------+---------------------------------------------------------------------+-------------------+
|Counter      |dict subclass for counting hashable objects                          |New in version 2.7 |
|             |                                                                     |                   |
+-------------+---------------------------------------------------------------------+-------------------+
|OrderedDict  |dict subclass that remembers the order entries were added            |New in version 2.7 |
|             |                                                                     |                   |
+-------------+---------------------------------------------------------------------+-------------------+
|defaultDict  |dict subclass that calls a factory function to supply missing values |New in version 2.5 |
|             |                                                                     |                   |
+-------------+---------------------------------------------------------------------+-------------------+

In addition to the concrete container classes, the collections module provides 
abstract base classes that can be used to test whether a class provides a 
particular interface, for example, whether it is hashable or a mapping.

