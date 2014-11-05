~~~~
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
micropython-lib is a highly experimental community project.

Please help to drive it to just "experimental" state by testing
provided packages with MicroPython.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
~~~~

micropython-lib
===============
micropython-lib is a project to develop a non-monolothic standard library
for MicroPython. Each module or package is available as a separate
distribution package from PyPI. Each module is either written from scratch or
ported from CPython. 

Note that the main target of micropython-lib is a "Unix" port of MicroPython
(additional ports to support are to be determined). Actual system requirements
vary per module. Though if a module is not related to I/O, the module should
work without problem on bare-metal ports too (e.g. pyboard).


Usage
-----
micropython-lib packages are published on PyPI (Python Package Index),
the standard Python community package repository: http://pypi.python.org/ .
On PyPi, you can search for MicroPython related packages and read
additional package information.

To install packages from PyPI for usage on your local system, use the
`pip-micropython` tool, which is a simple wrapper around the standard
`pip` tool, which is used to install packages for CPython.
The `pip-micropython` tool can be found in `tools` subdirectory 
of the main MicroPython repository (https://github.com/micropython/micropython).
Just install the `pip-micropython` script somewhere on your `PATH`.

Afterwards, just use `pip-micropython` in a way similar to `pip`:

~~~~
$ pip-micropython install micropython-copy
$ micropython
>>> import copy
>>> copy.copy([1, 2, 3])
[1, 2, 3]
~~~~

Review the `pip-micropython` source code for more info.


Development
-----------
To install modules during development, use `make install`. By default, all
available packages will be installed. To install a specific module, add the 
`MOD=<module>` parameter to the end of the `make install` command.

Note on OSX
-
By default OSX uses the BSD versions of basic core utilities. The
micropython-lib `Makefile` make use of certain GNU-specific options
for some of these utilities (`find`, `xargs`, and `cp`)
This is being tracked at https://github.com/micropython/micropython-lib/issues/10
Until the Makefile is revised to work on both GNU and BSD based
systems, the following workaround is available for OSX users:
 * Use Macports to install the GNU coreutils:
`sudo port install coreutils`
 * Make a copy of `Makefile`, naming it something like `Makefile-osx`,
and modify this copy of the Makefile to use the GNU versions of the
utilities you just installed: change `find` to `gfind`, `xargs` to
`gxargs`, and `cp` to `gcp`
 * Now run `gmake --makefile=Makefile-osx install` to install
micropython-lib to its default location (`~/.micropython/lib`) 


Links
-----
More information is on GitHub and in the MicroPython forums:

 * https://github.com/micropython/micropython/issues/405
 * http://forum.micropython.org/viewtopic.php?f=5&t=70

Guidelines for packaging MicroPython modules for PyPI:

 * https://github.com/micropython/micropython/issues/413
