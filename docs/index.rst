libsass-python: Sass_/SCSS for Python
=====================================

This package provides a simple Python extension module :mod:`sass` which is
binding LibSass_ (written in C/C++ by Hampton Catlin and Aaron Leung).
It's very straightforward and there isn't any headache related Python
distribution/deployment.  That means you can add just ``libsass`` into
your :file:`setup.py`'s ``install_requires`` list or :file:`requirements.txt`
file.

It currently supports CPython 2.6, 2.7, 3.5--3.7, and PyPy 2.3+!

.. _Sass: https://sass-lang.com/
.. _LibSass: https://github.com/sass/libsass


Features
--------

- You don't need any Ruby/Node.js stack at all, for development or deployment
  either.
- Fast. (LibSass_ is written in C++.)
- Simple API.  See :ref:`example code <example>` for details.
- Custom functions.
- ``@import`` callbacks.
- Support both tabbed (Sass) and braces (SCSS) syntax.
- WSGI middleware for ease of development.
  It automatically compiles Sass/SCSS files for each request.
  See also :mod:`sassutils.wsgi` for details.
- :mod:`setuptools`/:mod:`distutils` integration.
  You can build all Sass/SCSS files using
  :program:`setup.py build_sass` command.
  See also :mod:`sassutils.distutils` for details.
- Works also on PyPy.
- Provides prebuilt wheel (:pep:`427`) binaries for Windows and Mac.


Install
-------

It's available on PyPI_, so you can install it using :program:`pip`:

.. code-block:: console

   $ pip install libsass

.. note::

   libsass requires some features introduced by the recent C++ standard.
   You need a C++ compiler that support those features.
   See also libsass project's README_ file.

.. _PyPI: https://pypi.org/pypi/libsass/
.. _README: https://github.com/sass/libsass#readme


.. _example:

Examples
--------

Compile a String of Sass to CSS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

>>> import sass
>>> sass.compile(string='a { b { color: blue; } }')
'a b {\n  color: blue; }\n'

Compile a Directory of Sass Files to CSS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

>>> import sass
>>> import os
>>> os.mkdir('css')
>>> os.mkdir('sass')
>>> scss = """\
... $theme_color: #cc0000;
... body {
...     background-color: $theme_color;
... }
... """
>>> with open('sass/example.scss', 'w') as example_scss:
...      example_scss.write(scss)
...
>>> sass.compile(dirname=('sass', 'css'), output_style='compressed')
>>> with open('css/example.css') as example_css:
...     print(example_css.read())
...
body{background-color:#c00}


User's Guide
------------

.. toctree::
   :maxdepth: 2

   frameworks/flask
   changes


References
----------

.. toctree::
   :maxdepth: 2

   sassc
   sass
   sassutils


Credit
------

Hong Minhee wrote this Python binding of LibSass_.

Hampton Catlin and Aaron Leung wrote LibSass_, which is portable C/C++
implementation of Sass_.

Hampton Catlin originally designed Sass_ language and wrote the first
reference implementation of it in Ruby.

The above three softwares are all distributed under `MIT license`_.

.. _MIT license: https://mit-license.org/


Open source
-----------

GitHub (Git repository + issues)
   https://github.com/sass/libsass-python

Travis CI
   https://travis-ci.org/sass/libsass-python

   .. image:: https://travis-ci.org/sass/libsass-python.svg
      :target: https://travis-ci.org/sass/libsass-python
      :alt: Build Status

AppVeyor (CI for Windows)
   https://ci.appveyor.com/project/asottile/libsass-python

   .. image:: https://ci.appveyor.com/api/projects/status/asgquaxlffnuryoq/branch/master?svg=true
      :target: https://ci.appveyor.com/project/asottile/libsass-python
      :alt: Build Status (Windows)

Coveralls (Test coverage)
   https://coveralls.io/r/sass/libsass-python

   .. image:: https://coveralls.io/repos/github/sass/libsass-python/badge.svg?branch=master
      :target: https://coveralls.io/r/sass/libsass-python
      :alt: Coverage Status

PyPI
   https://pypi.org/pypi/libsass/

   .. image:: https://badge.fury.io/py/libsass.svg
      :alt: PyPI
      :target: https://pypi.org/pypi/libsass/

Changelog
   :doc:`changes`


Indices and tables
------------------

- :ref:`genindex`
- :ref:`modindex`
- :ref:`search`
