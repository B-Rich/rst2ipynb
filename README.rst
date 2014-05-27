rst2ipynb
---------

A restructured text to IPython notebook converter.

Origins
-------

This base code was originally part of the nbconvert project before it was
merged into the IPython repository proper.

Resurrection Details
~~~~~~~~~~~~~~~~~~~~

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
