About
-----

Sesame is a Python3 package for solving the drift diffusion Poisson equations for multi-dimensional systems using finite differences.

The software computes the steady state of a semiconductor between two contacts, and subject to voltage bias and/or illumination. It was developed to study polycrystalline solar cells containing charged interfaces (grain boundaries, sample surface). Sesame handles single charged states and continuum of defect states alike.

Sesame includes modules that can be used in Python code as well as a standalone GUI (contained in app.py of the head directory of the distribution).  Example scripts and GUI input files can be found in the examples directories.  The documentation includes tutorials describing example scripts.  Online documentation can be found `here <http://sesame.readthedocs.io/en/latest/>`_ .

Support for this project comes from the U.S. National Institute of
Standards and Technology and the University of Maryland.

Installation instructions
-------------------------

Prerequisites
..............

Building Sesame requires
 * `Python <http://python.org>`_ 3.4 or above,
 * `SciPy <http://scipy.org>`_ 0.9 or newer,
 * `LAPACK <http://netlib.org/lapack/>`_ and `BLAS <http://netlib.org/blas/>`_,
   (other options are the free `OpenBLAS
   <http://xianyi.github.com/OpenBLAS/>`_ or the nonfree `MKL
   <http://software.intel.com/en-us/intel-mkl>`_.)

The following software is highly recommended though not strictly required:
 * `Matplotlib <http://matplotlib.sourceforge.net/>`_ 1.1 or newer, for Sesame's
   plotting routines. Matplotlib is required when using the graphical interface
   of Sesame.
 * `MUMPS <http://graal.ens-lyon.fr/MUMPS/>`_, a sparse linear algebra library
   that will in many cases speed up Sesame several times and reduce the memory
   footprint.  (Sesame uses only the sequential, single core version
   of MUMPS.  The advantages due to MUMPS as used by Sesame are thus independent
   of the number of CPU cores of the machine on which Sesame runs.)
 * An environment which allows to compile Python extensions written in C,
   C++ and Fortran.

The graphical user interface requires `PyQt5
<https://riverbankcomputing.com/software/pyqt/intro>`_.

For users with no python installation, a convenient standalone installation which automatically includes all of the requisiste libraries and packages is `Anaconda <https://www.anaconda.com/>`_ .

Generic instructions
.....................
Standard build and install
++++++++++++++++++++++++++
Sesame can be built  and installed following the `usual Python conventions
<http://docs.python.org/install/index.html>`_ by running the following commands
in the root directory of the Sesame distribution::

    python setup.py build
    python setup.py install

Depending on your system, you might have to run the second command with
administrator privileges. The installation
step can be done locally either by using the ``--user`` prefix::

    python setup.py install --user

or by specifying the location where to install the package files with
``--prefix=/path/of/directory``.

The tutorial examples can be found in the directory ``examples`` inside the root
directory of the Sesame source distribution.

Building the documentation
+++++++++++++++++++++++++++

To build the documentation, the `Sphinx documentation generator
<http://sphinx.pocoo.org/>`_ is required (version 1.4 or newer) with ``numpydoc``
extension (version 0.5 or newer), and Latex.

HTML documentation is built by entering the ``doc`` sub-directory of the Sesame
package and executing ``make html``. Open the file ``index.html`` in the
directory ``build/html`` with a web browser to access the documentation. PDF
documentation is generated by executing ``make latex`` followed by ``make
latexpdf``. The pdf file is generated in ``build/latex``.

Because of some quirks of how Sphinx works, it might be necessary to execute
``make clean`` between building HTML and PDF documentation.  If this is not
done, Sphinx may mistakenly use PNG files for PDF output or other problems may
appear.

As an alternative if ``make`` is not available, the HTML documentation can be built
using the command from the root directory::

    python setup.py build_sphinx

The documentation is produced in ``doc/build/html``. To build the PDF file::

    python setup.py build_sphinx -b latex
    cd doc/build/latex
    make all-pdf

The resulting PDF is produced in ``doc/build/latex``.

