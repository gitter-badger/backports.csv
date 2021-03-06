================================================
backports.csv: Backport of Python 3's csv module
================================================

The API of the csv module in Python 2 is drastically different from
the csv module in Python 3. This is due, for the most part, to the
difference between str in Python 2 and Python 3.

The semantics of Python 3's version are more useful because they support
unicode natively, while Python 2's csv does not.

Installation
============

.. code-block:: sh

    pip install backports.csv

Usage
=====

First make sure you're starting your file off right:

.. code-block:: python

    from backports import csv


Then be careful with your files to handle the encoding.
I suggest using ``io.TextIOWrapper``,
opening your file in binary mode,
and declaring your desired encoding when constructing
your ``TextIOWrapper``.

.. code-block:: python

    from backports import csv
    from io import TextIOWrapper

    def read_csv(filename):
        with TextIOWrapper(open(filename, 'rb'), encoding='utf-8') as f:
            reader = csv.reader(f)
            for row in reader:
                yield row

    def write_csv(filename, rows):
        with TextIOWrapper(open(filename, 'wb'), encoding='utf-8') as f:
            for row in rows:
                writer.writerow(row)
