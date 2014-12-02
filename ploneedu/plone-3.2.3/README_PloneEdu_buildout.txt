Introduction
============

This is a bootstrap buildout for PloneEdu K-12 and higher ed
institutions.  It contains all the products listed at

https://weblion.psu.edu/ploneedu/community/projects/buildout/buildout/

(except for collective.lineage and collective.xdv) and is derived from
a buildout running in production at the University of Wisconsin
Oshkosh.

It creates a minimal ZEO installation of Plone, ie. a ZEO server and
one ZEO client (client1), as opposed to a standalone (single process)
instance.

To start and stop the "cluster", use the bin/startcluster.sh and
bin/shutdowncluster.sh scripts.

The default port that client1 listens on is 11080 but you can change
that in buildout.cfg.

--
T. Kim Nguyen
nguyen@uwosh.edu


Dependencies
------------

You may have to install virtualenv.  As per the instructions at 

http://pypi.python.org/pypi/virtualenv

"You can install it with easy_install virtualenv, or from the hg
repository or from a tarball easy_install virtualenv==tip."

I usually use "easy_install virtualenv".

Make sure you are using Python 2.4 since that is what Plone 3.2.3 requires.

You can tell which python version you have by simply invoking Python:

$ python
Python 2.6.1 (r261:67515, Feb 11 2010, 00:51:29) 
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> ^D

Oops.  OK, to find a Python 2.4 on your system, try

$ python2.4
bash: python2.4: command not found
$

Oops again.  OK, you will have to install Python 2.4 from 

http://python.org/download/releases/2.4.6/

I usually try from source, ie. the gzip-compressed source code:
python-2.4.6.tgz, but it gets hairy on Mac OS X 10.6 (Snow Leopard).

An easy way to get Python 2.4 is to use the Plone unified installer or
the Windows or Mac installer, as they all install Python 2.4 and you
invoke that python2.4 executable.



How To (with virtualenv)
------------------------

>>> svn co https://svn.it.uwosh.edu/svn/plone/buildouts/ploneedu/plone-3.2.3
>>> cd plone-3.2.3
>>> virtualenv --no-site-packages ./
>>> bin/python bootstrap.py
>>> bin/buildout

And then wait :)


Platforms
---------

This buildout has been tested successfully on the following platforms:

* RedHat Enterprise Linux 5.5

* Mac OS X 10.5.8 (Leopard)

* Mac OS X 10.6.4 (Snow Leopard): if you encounter the error 'cc1: error:
  unrecognized command line option "-Wno-long-double"' it is likely
  because of a GCC version issue.  For a workaround, see
  http://www.uwosh.edu/ploneprojects/documentation/how-tos/buildout-error-on-mac-os-x-10.6-snow-leopard
  which essentially tells you to change the symlink for gcc to point
  to gcc-4.0 instead of gcc-4.2 and then rerun bin/buildout.
  
  PIL fails to install on some OS X systems that have setuptools 0.6c11. In that case, after you run 
  bootstrap.py you will need to install setuptools 0.6c9 before doing the buildout.
  >>> easy_install setuptools==0.6c9


History
-------

1.0.6 (2010-12-13)
----------------

* Uses uwosh.timeslot 1.4.8 to correct a bug in which permissions for
  Contributor, Manager, and Owner roles were being cleared out


1.0.5 (2010-11-06)
----------------

* Tested on OS X 10.5.8. Altered warning re: potential OS X &
  setuptools version issue.


1.0.4 (2010-09-12)
----------------

* Added Products.Ploneboard and collective.fancyzoomview


1.0.3 (2010-09-10)
------------------

* Added products that are useful in development environments

* Removed collective.lineage and collective.xdv (temporarily) since
  they were causing errors


1.0.2 (2010-09-10)
------------------

* Renamed version.txt to version_PloneEdu_buildout.txt

* Added remaining products taken from
  https://weblion.psu.edu/ploneedu/community/projects/buildout

* Added buildout.dumppickedversions extension so we always see the egg
  versions (good for version pinning!)


1.0.1 (2010-09-10)
------------------

* Commented out extraneous uwosh.* products

* Renamed README.txt so it would not get overwritten by the buildout
  process


1.0 (2010-09-10)
----------------

* Initial release.  
