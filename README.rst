rst2ipynb
---------

A restructured text to IPython notebook converter.

Origins
-------

This base code was originally part of the nbconvert project before it was
merged into the IPython repository proper sometime during the summer of 2013.
At the time I was working on improving the ``rst2ipynb.py`` script in order to
auto-translate teaching material from http://scipy-lectures.github.io/ in order
to give a numpy tutorial at Scipy2013:
http://conference.scipy.org/scipy2013/tutorial_detail.php?id=100 and
https://github.com/esc/scipy2013-tutorial-numpy-ipython. It didn't work
perfectly, and I had to tweak and post-process the material, but I did get the
bulk translated successfully. In Summer 2014 I wasn't able to find a suitable
alternative and thus decided to work some git-magic to extract the history from
the nbconvert repository and augment it with the improvements from my github
fork to provided a basis for further development. Importantly, all the original
commits and their metadata and thus all attributions were retained.

Why would I want this?
----------------------

In my humble opinion |--| as the phrase goes |--| reading and executing IPython
notebooks is great BUT: authoring IPython notebooks is rather cumbersome and
tricky.  This is perhaps due to my personal preferences of using the Vim editor
and the corresponding plugin for firefox: Vimperator. I actually prefer
creating presentations and blog-posts (soon to come) using my familiar tools in
a familiar markup language. Writing text into HTML text windows is just such a
pain and switching around between cells is so cumbersome. Also I still have
issues with copy and pasting stuff from the notebooks. Anyway, it's just my
personal preference and you are by no means obliged to agree with me; but if
you do, please feel free to use the code.

Features
--------

Currently I can convert headings to markdown headings, paragraphs to markdown
paragraphs (using pypandoc) and code-blocks to code-cells. See the file
``example.rst`` for details.

But where is...?
----------------

... documentation, dependency specification, packaging, working unit-tests,
continuous-integration, PyPi availability, Debian package? Yeah... um... sure,
just send a Pull-Request?

Usage
-----

.. code-block::

   $ ./rst2ipynb.py input.rst > output.ipynb
   $ ipython notebook


Resurrection Details
--------------------

So, the repository was crafted from:

https://github.com/esc/nbconvert

Using the branch:

https://github.com/esc/nbconvert/tree/improve_rst2ipynb

And the ``git filter-branch`` incantation:

.. code-block:: console

    $ git filter-branch --prune-empty -f --index-filter 'git ls-tree -r --name-only --full-tree $GIT_COMMIT | grep -v -f $HOME/files | xargs git rm -r'

and ``files`` being::

    rst2ipynb.py
    rst2ipynblib/__init__.py
    tests/test_rst2ipynb.py
    tests/tutorial.ipynb.ref
    tests/tutorial.rst.ref

Then, to remove the empty merge commits:

.. code-block:: console

    $ git rebase 84b2dd132646d5b80ee6d1d121c2452bc3bfce86

Where ``84b2dd132646d5b80ee6d1d121c2452bc3bfce86`` is the root commit of the repo.

Originally it was 723 commits -- only 38 remained.

Licence
-------

The original code was released under the same licence as IPython and as such
this project inherits that licence.
