The growler_ext Namespace Package
=================================

As a convenience to developers, Growler defines a standard package `growler_ext` as a place to
define multiple extension packages.
The intent is to twofold: a cleaner (single) import statement for those who prefer to avoid
dozens of `from something import extension` statements, and to allow the possibility of
different implementations sharing the same name, so backend may be changed with no difference
in the code (assuming the interfaces are the same, which they should be).


Writing Your Own Extension
--------------------------

It is very easy to write packages that are included in the growler_ext namespace; simply create
a `growler_ext` folder in your project, and place whatever module files in this folder.
It is recommended to only include one or maybe two files in this namespace package.
This module should import your 'real' package and

.. Note::

  Do NOT place an \__init__.py file in the growler_ext folder - this will

Being a *namespace package*, growler_ext allows multiple packages to declare the
