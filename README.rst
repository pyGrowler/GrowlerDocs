Growler Documentation
=====================

This is a separate repository containing the documentation files for the `growler
<https://github.com/pyGrowler/Growler>`_ project. It is intended to be used as a submodule of
growler git repository (in :code:`/path/to/growler/docs/`).

To pull both code and docs, use

.. code:: bash

    git clone --recursive https://github.com/pyGrowler/growler.git


Building
--------

Building requires the sphinx documentation generator. Generating the html should be as simple
as running :code:`make html`. If this documentation is not located in the growler source, the
path may be specified using the :code:`GROWLER_PATH` environment variable.

.. code:: bash

  GROWLER_PATH=/path/to/growler make html

Note, :code:`GROWLER_PATH` should contain the growler source package (the folder with
:code:`setup.py`), NOT point directly at it (the folder with :code:`__init__.py`)


License
-------

A license for the documentation has not been chosen yet.
