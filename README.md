Table of Contents
=================

 -  [Overview](#overview)
 -  [Requirements](#requirements)
 -  [Installation](#installation)
 -  [Documentation](#documentation)
 -  [License](#license)

Overview
========

The Python script `yule.py` provides a command-line interface (CLI) for
performing simple calculations of speciation rate, tree height, and tree length
under a Yule (pure-birth) process. It was written by [Jamie
Oaks](http://www.phyletica.com).

Requirements
============

Python is the only requirement. The script has only been tested in version 2.7
of Python.

Installation
============

Open a terminal window and navigate to where you would like to keep the `pyule`
repository. Then, use `git` to clone the repository:

    git clone https://github.com/joaks1/pyule.git

Move into the `pyule` directory:
    
    cd pyule

Call up the `yule.py` help menu:

    python yule.py -h

Documentation
=============

The `yule.py` script expects three positional arguments. The first argument can
be one of 'rate', 'height', or 'length', and the second argument is a number
associated with the first argument. In other words, you must give the script a
numeric value for the birth 'rate' of the Yule process, the expected 'height'
of the tree generated by a Yule process, or the expected total 'length' of the
tree generated by a Yule process. The third and final argument is the number of
tips of the tree.

Provided this information, the script will calculate the other two values
(i.e., if provided the expected height, it will calculate the expected length
and birth rate of the Yule process).

For example, let us say we have a know the expected height of a tree with 100
tips is 65 million years, and we want to know the expected length of the tree
under a Yule process and the rate of the process. We would use:

    python yule.py height 65 100

And the out put would be:

    ntips = 100
    rate = 0.0644211925791
    height = 65.0
    length = 1536.76136744

Thus, the rate of a Yule process with an expected tree height of 65 million
years is 0.064 species per million years, and the expected tree length under
that process is 1536.76 million years.

Alternatively, if we new the birth rate and wanted the expected tree
characteristics, we could do:

    python yule.py rate 0.5 75

    ntips = 75
    rate = 0.5
    height = 7.80271126111
    length = 148.0

This tells us that a Yule process with a rate of 0.5 species per million years
will generate a tree with 75 tips with an expected height and length of 7.8 and
148.0 million years, respectively.
    
This script can be useful when specifying a hyperprior for a birth rate of a
Yule (or birth-death) process prior on phylogenetic trees. In such a case, we
often have some rough prior expectation for the tree height. For example, we
might expect the greatest divergence between sequences is around 0.2
substitutions per site, and so we expect the height of the tree to be around
0.1. So, if we have 50 sequences we can use:

    python yule.py height 0.1 50

    ntips = 50
    rate = 34.9920533833
    height = 0.1
    length = 1.40031793685

If we are using a Yule or birth-death prior on trees, we now have some idea of
prior expectations for the birth rate (around 35 species per substitutions per
site).

Acknowledgements
================

This software benefited from funding provided to [Jamie
Oaks](http://www.phyletica.com) from the National Science Foundation (DEB
1011423 and DBI 1308885).

License
=======

Copyright (C) 2013 [Jamie Oaks](http://www.phyletica.com)

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License along
with this program. If not, see <http://www.gnu.org/licenses/>.

See "LICENSE.txt" for full terms and conditions of usage.

