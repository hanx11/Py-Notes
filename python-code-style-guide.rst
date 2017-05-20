===========================
Python Code Style Guideline
===========================

Preface
-------

A style guide is about consistency. Consistency with this style guide
is important. Consistency within a project is more important. Consistency
within one module or function is the most important.

First Principle
---------------

In particular: do not break backwards compatibility just to comply with this PEP!

Some other good reasons to ignore a particular guideline:

1. When applying the guideline would make the code less readable, even for someone
   who is used to reading code that follows this PEP.

2. To be consistent with surrounding code that also breaks it (maybe for historic 
   reasons)--although this is also an opportunity to clean up someone else's mess
   (in true XP style).

3. Because the code in question predates the introduction of the guideline and 
   these is no other reason to be modifying that code.

4. When the code needs to remain compatible with older versions of Python that
   don't support the feature recommended by the style guide.

