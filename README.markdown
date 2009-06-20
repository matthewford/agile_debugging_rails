Agile Debugging Rails
=====================

A troubleshooting solution "book" for common Ruby on Rails problems 
and tips for refactoring your code. Viewable at [deubg.bitzesty.com][]

format adapted from the [sinatra-book][]

Layout
------

    book/   - Text of the book.  In maruku's markdown format.
    images/ - Images, Diagrams
    source/ - Any source examples to be included into the book

Contributors
------------
* [Matthew Ford](http://bitzesty.com)

Github Repo:
[http://github.com/matthewford/agile\_debugging\_rails/tree](http://github.com/matthewford/agile_debugging_rails/tree)

Legal
-----

The content of this book is licensed under the [Creative Commons Attribution-Noncommercial-Share Alike 3.0 license][]

[debug.bitzesty.com]:http://debug.bitzesty.com
[sinatra-book]:http://github.com/sinatra/sinatra-book/tree
[Creative Commons Attribution-Noncommercial-Share Alike 3.0 license]: http://creativecommons.org/licenses/by-nc-sa/3.0/us/

How to build the Book
---------------------

You need following gems to build the book:

    sudo gem install thor maruku

In the root directory, launch the following Thor task:

    thor book:build
        
General guidelines for patches:

* Keep lines to approximately 80 characters or less.  This is to allow git to do patches at the line level.
* No embedded HTML.  We need to render to LaTeX (and then PDF), which won't support it.


Submitting Patches

* Fork this repo on GitHub and send pull requests
