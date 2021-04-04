# Python Installation

## Install Python

Your computer probably automatically has Python on it. We're going to run some installation stuff to make sure it's got the latest and greatest that Python has to offer.

### Python 2 vs. Python 3

Note: there are two versions of Python. There's Python 2 and Python 3. Python 3 was released in 2008 and included breaking changes. Breaking changes means that an upgrade changes the way some code works and old code won't always work with the way new code wants it to be written.

Why did Python 3 introduce breaking changes? Well, it turns out there were some things in Python 2 that could have been designed better. Guido, and the Python community decided that it would be worth it, in the long haul, to fix those mistakes and get the language back on track for where they want it to be in the future. Upgrading to Python 3 is a good thing!

Wait, so if upgrading to Python 3 is a good thing, why are some people still using Python 2?

It turns out that converting some code from Python 2 to Python 3 is hard and requires lots of work. It's easy to convert small projects from Python 2 to Python 3, but it's hard to convert large, complex projects. In an ideal world everyone would be able to convert their projects and Python 2 would be laid down to rest. In reality, lots of large, popular projects started being written in Python 2 and they just don't have the resources \(or incentives\) to upgrade to Python 3.

To us, the differences between Python 2 and Python 3 are minimal. They're very much still the same language. Anyone that knows either Python 2 or Python 3 is able to switch to using the other easily.

Perhaps the most notable difference is how you print things.

```python
# python 2 doesn't use parenthesis in print statements
print "hello world!"

# python 3 makes print use parenthesis, just like every other function.
# this is a great change!
print("hello world!")
```

See? Switching between the two isn't that big of a deal. For what we do. If you're curious, take a look at this long list of actual differences between Python 2 and Python 3:

[http://sebastianraschka.com/Articles/2014\_python\_2\_3\_key\_diff.html](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html)

It's good that Python made the breaking changes. In this class we're going to use Python 3, always. This requires us to be extra sure that we never "accidentally" use Python 2. Be aware!

## Actual Installation

Here's the tools we're snaggin:

* **Python 3** - the latest and greatest version of Python
* **IPython**  - an enhanced Python shell that provides excellent features

  beyond the normal Python shell. For example:

  * syntax highlighting
  * auto-completion
  * when you press the up arrow it lets you edit entire functions and blocks

    of code.

* **Django** - a larger Python web framework

Use `brew` to install Python 3!

```text
brew install python3
```

Use `pip`, a Python package installer, much like `npm` to `node`. `pip` stands for "Pip Installs Packages." Programmers love recursive acronyms.

Notice, there's two versions of `pip`. One installs things for Python 2 another installs things for Python 3. Use `pip3` to be explicit. If you're lucky, maybe your system uses `pip` for Python 3 by default. Let's assume we're not lucky and always use `pip3`, to be explicit.

You can verify what version of Python `pip` and `pip3` use:

```text
pip --version
pip3 --version
```

We want to use the one that says:

```text
pip 20.1.1 from /usr/local/lib/python3.6/site-packages (python 3.6)
```

Ok. let's install stuff:

```text
pip3 install ipython
pip3 install Django
```

Notice that `python` refers to the default system installation of Python 2, and `python3` refers to the latest and greatest install of Python 3.

Always use `python3`. Always.

```text
python  --version         2.7.16
python3 --version         3.8.5
ipython --version         7.18.1
django-admin.py version   # 3.1.1
```

Start `ipython` and verify it uses Python 3 by default. We're looking for something like **Python 3.8.5** at the beginning of the first line here when IPython starts up:

```text
Python 3.8.5 (default, Jul 21 2020, 10:42:08)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.18.1 -- An enhanced Interactive Python. Type '?' for help.
```

Make sure that you're version numbers are _in the ballpark_ of what you see above.

Great. Python3 and the enhanced IPython shell are all installed. Let's hop into the IPython shell and check to see if Django was installed properly.

```python
import django
print("Django version:", django.__version__)
```

```text
Django version: 3.1.1
```

Also, while youre in the IPython shell, let's go ahead and check out one of it's awesome features: auto-completion!

The IPython shell doesn't leave you hanging when you don't remember something. You can press TAB while you're in the middle of something and it detects what variables, data types, and functions you have available and it offers suggestions.

Let's make a variable equal to a string, then type `s.` and press the TAB key to see what IPython suggests. We'll see that it creates a pop-up menu that shows all the methods available to us for strings.

It all looks something like below. How cool is that? Here we are knowing nothing about Python and our shell helps us out by showing what sort of things we can do. Use the up and down arrow keys to flip through this list and pick a function. I chose `upper`.

Also, it came back and showed me `<function str.upp>` so I added parenthesis so the function was actually called.

```text
In [3]: s='python is awesome'

In [4]: s.
           capitalize()   format()       isidentifier() ljust()        rjust()        swapcase()
           casefold()     format_map()   islower()      lower()        rpartition()   title()
           center()       index()        isnumeric()    lstrip()       rsplit()       translate()
           count()        isalnum()      isprintable()  maketrans()    rstrip()       upper()
           encode()       isalpha()      isspace()      partition()    split()        zfill()
           endswith()     isascii()      istitle()      replace()      splitlines()
           expandtabs()   isdecimal()    isupper()      rfind()        startswith()
           find()         isdigit()      join()         rindex()       strip()
           
In [5]: s.upper
Out[6]: <function str.upper>

In [7]: s.upper()
Out[8]: 'PYTHON IS AWESOME'
```

OK! Those are our tools. Now you're ready to get a proper crash-course introduction to Python.

