This is an example for rst2ipynb
--------------------------------

This is a multiline paragraph that will be converted to an ipython notebook
markdown cell by doing a call to ``pandoc`` via ``pypandoc``.

.. code-block:: python

   import this
   print("This is a code block using the 'python' highlighting")

.. code-block:: pycon

   >>> import this
   >>> print("This is a code block using the 'pycon' highlighting")

.. code-block:: ipython

   In [1]: print("ipython code blocks are also supported, using 'ipython'")
