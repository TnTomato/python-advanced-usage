Ellipsis
========

Ellipsis, means something omitted.

Let's see the official explanation:

    **The Ellipsis Object**

    This object is commonly used by slicing (see `Slicings`_). It supports no
    special operations. There is exactly one ellipsis object, named `Ellipsis`_
    (a built-in name). ``type(Ellipsis)()`` produces the `Ellipsis`_ singleton.

    It is written as ``Ellipsis`` or ``...``.

.. _Slicings: https://docs.python.org/3/library/stdtypes.html#the-ellipsis-object
.. _Ellipsis: https://docs.python.org/3/library/constants.html#Ellipsis

It's a little bit hart to understand. See some interesting code:

.. code-block:: python

    numbers = [1, 2, 3]
    numbers.append(numbers)
    print(numbers)

Output:

.. code-block:: text

    [1, 2, 3, [...]]

Take a look at the last element in ``numbers``. It's ``[...]``, which means an
ellipsis. ``numbers[-1]`` is ``numbers`` itself. They share the same memory
address. The new appended element points to the object itself:

.. code-block:: python

    print(id(numbers))  # 1798884778632
    print(id(numbers[-1]))  # 1798884778632

We see the object ``...``, it's a singleton. So what is it used for? Actually it's
useless. It is just a common object. We can see in the documentation that it is
commonly used by slicing but so ambiguous. I can hardly see this in use.

``...`` is the same as a Python's keyword ``pass``. They are totally the same.

But in our daily code life, we usually use if for some to-be-completed code
blocks. For example:

.. code-block:: python

    class Animal(object):
        pass


    class Dog(Animal):
        pass

We use a ``pass`` as a placeholder when we don't want to finish the code for
the moment. That runs with nothing happening. So you can try:

.. code-block:: python

    try:
        1 / 0
    except ZeroDivisionError:
        ...

That probably means you are very speechless with the exception(lol).
