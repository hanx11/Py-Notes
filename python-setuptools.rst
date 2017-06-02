==================================================
Building and Distributing Packages with Setuptools
==================================================

Setuptools is a collection of enhancements to the Python distutils (for Python 2.6 and up)
that allow developers to more easily build and distribute Python package, especially ones
that dependencies on other packages.

Packages built and distributed using setuptools look to the user like ordinary Python pack-
ages based on the distutils. Your users don't need to install or even know about setuptools
in order to use them, and you don't have to include the entire setuptools package in your
distributions. By including just a single bootstrap module (a 12k .py file), your package
will automatically download and install setuptools if the user is building your package
from source and doesn't have a suitable version already installed.

Feature Highlights:

  - Automatically find/download/install/upgrade dependencies at build time using the 
    EasyInstall tool, which supports downloading via HTTP,FTP, Subversion, and SourceForge,
    and automatically scans web pages linked from PyPI to to find download links. (It's the
    closest thing to CPAN currently available for Python.)

  - Create Python Eggs - a single-file import
