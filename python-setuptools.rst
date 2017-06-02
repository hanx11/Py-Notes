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

  - Create Python Eggs - a single-file importable distribution format

  - Enhanced support for accessing data files hosted in zipped packages.

  - Automatically include all packages in your source tree, without listing them individually
    in setup.py

  - Automatically include all relevant files in your source distributions, without needing to 
    create a MANIFEST.in file, and without having to force regeneration of the MANIFEST file 
    when your source tree changes.

  - Transparent Pyrex support, so that your setup.py can list .pyx files and still work even 
    when the end-user doesn’t have Pyrex installed (as long as you include the Pyrex-
    generated C in your source distribution)

  - Command aliases - create project-specific, per-user, or site-wide shortcut names for commonly 
    used commands and options

  - PyPI upload support - upload your source distributions and eggs to PyPI

  - Deploy your project in “development mode”, such that it’s available on sys.path, yet can still 
    be edited directly from its source checkout.

  - Easily extend the distutils with new commands or setup() arguments, and distribute/reuse your 
    extensions for multiple projects, without copying code.

  - Create extensible applications and frameworks that automatically discover extensions, using 
    simple “entry points” declared in a project’s setup script.

`**Learn More** <http://setuptools.readthedocs.io/en/latest/setuptools.html#installing-setuptools>`_
