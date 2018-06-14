+++
title = "Software Requirements and Installation"
author = ["Thomas S. Dye"]
lastmod = 2018-06-10T08:43:22-10:00
draft = false
weight = 40
+++

The `hm` package is open-source Common Lisp software that should run on the
free, open-source implementations offered by [SBCL](http://www.sbcl.org/) or [Clozure CL](http://ccl.clozure.com/). A working
installation of one of these implementations is required by `hm`.

The `hm` package uses [Graphviz `dot`](https://graphviz.gitlab.io/) for graph visualization and graphics output.
A working installation of [Graphviz `dot`](https://graphviz.gitlab.io/download/) software is required by `hm`.

The `hm` package is distributed from a `git` version control software
repository.  A working installation of [`git` software](https://git-scm.com/) is required.

The [Quicklisp library manager](https://www.quicklisp.org/beta/) for Common Lisp is strongly recommended. The
instructions in this manual assume a working installation of [Quicklisp](https://www.quicklisp.org/beta/).

An `hm` project is configured with an `.ini` format text file. A plain text
editor, rather than a word processor, is recommended for working with `.ini`
format files.

The `hm` software was developed using the [Superior Lisp Interaction Mode](https://common-lisp.net/project/slime/) for the
[Emacs](https://www.gnu.org/software/emacs/) text editor.


## Install `hm` {#install}

Installation with [Quicklisp](http://www.quicklisp.org) is recommended. It automatically installs the other
Common Lisp packages upon which `hm` depends, and their dependencies, etc.

The following example assumes that [Quicklisp](http://www.quicklisp.org) is installed on your computer.
These instructions will clone the `hm` package in the `local-projects/harris-matrix/`
subdirectory of your quicklisp installation.

<a id="org48f1cc3"></a>
```sh
cd <path-to>/quicklisp/local-projects/

git clone https://github.com/tsdye/harris-matrix.git
```

The `hm` software is released under the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.en.html), Version 3, a
free, copyleft license for software and other kinds of works.


## Load `hm` {#load}

A typical session with `hm` starts by using Quicklisp to load the software.

<a id="orgac74898"></a>
```lisp
(ql:quickload "hm")
```

Note that the output from your Common Lisp implementation might differ, and that
you might see additional output depending on the state of your Common Lisp
environment.

```text
To load "hm":
  Load 1 ASDF system:
    hm
; Loading "hm"

```

A successful Quicklisp `quickload` of `hm` will also install several other
packages and their dependencies in `<path-to>/quicklisp/dists/quicklisp/software/`.

<a id="org65a4377"></a>

<div class="table-caption">
  <span class="table-number">Table 1:</span>
  Common Lisp packages upon which <code>hm</code> directly depends
</div>

| Package                                                    | Description                                           | License                              |
|------------------------------------------------------------|-------------------------------------------------------|--------------------------------------|
| [graph](http://quickdocs.org/graph/)                       | simple graph data structure and algorithms            | GPL V3                               |
| [graph/matrix](http://quickdocs.org/graph/)                | matrix representation of graphs                       | GPL V3                               |
| [graph/dot](http://quickdocs.org/graph/)                   | serialize graphs to and from `dot` format             | GPL V3                               |
| [cl-csv](http://quickdocs.org/cl-csv/)                     | read and write comma-separated value text files       | BSD                                  |
| [fset](http://quickdocs.org/fset/)                         | a functional set-theoretic collections library        | LLGPL                                |
| [py-configparser](http://quickdocs.org/py-configparser/)   | Python configparser module implemented in Common Lisp | MIT                                  |
| [cl-colors](http://quickdocs.org/cl-colors/)               | simple color library for Common Lisp                  | Boost Software License - Version 1.0 |
| [fare-memoization](http://quickdocs.org/fare-memoization/) | memoization library                                   | MIT                                  |
| [inferior-shell](http://quickdocs.org/inferior-shell/)     | spawning shell commands and pipes from Common Lisp    | Copyright (c) 2011-2014 Google, Inc. |


## Use the `hm` name space {#use-the-hm-name-space}

Move into the `hm` name space for easy access to `hm` functions.

<a id="orgd082800"></a>
```lisp
(use-package :hm)
```
