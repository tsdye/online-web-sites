+++
title = "The hm Package"
author = ["Thomas S. Dye"]
lastmod = 2018-06-10T08:43:21-10:00
draft = false
weight = 20
+++

The `hm` package is an open-source Common Lisp package for investigating the
chronological structure of archaeological stratigraphy.

With `hm` you can:

-   represent the [Harris matrix](http://harrismatrix.com/) as a stratigraphic acyclic directed graph (DAG)
    as described by [Dye and Buck (2015)](https://www.sciencedirect.com/science/article/pii/S0305440315002459)
-   investigate and analyze the structure of the [Harris matrix](http://harrismatrix.com/) using graph
    theoretic functions and characteristics of the archaeological data
-   generate a chronological DAG that can guide data input for Bayesian
    calibration software such as [BCal](http://bcal.shef.ac.uk/), [OxCal](https://c14.arch.ox.ac.uk/oxcal.html), or [Chronomodel](https://chronomodel.com/)
-   create a graphic visualization of a stratigraphic DAG or a chronological DAG
    in any one of the graphics formats supported by the open-source [Graphviz dot](https://graphviz.gitlab.io/)
    software

A central organizing principle of the `hm` software is the self-contained
_project._ An `hm` project has its own file directory that includes:

-   two or more input files with information on
    -   units of archaeological stratification, or contexts
    -   observations of stratigraphic superposition
    -   inferences of once-whole contexts
    -   periods
    -   phases
    -   dated events
    -   event order
-   one or more initialization files that specify
    -   input files
    -   classifiers that are mathematical functions on the stratigraphic DAG or
        archaeological constructs specified by the excavator
    -   output files
    -   parameters to configure the  [Graphviz dot](https://graphviz.gitlab.io/) software
-   zero or more output files generated during investigation and analysis

The `hm` software is designed to be collaborative:

-   input files are comma-separated value text files that can be produced by
    -   most spreadsheet applications
    -   most database software
    -   any text editor
-   initialization files are the widely-used `.ini` file format
-   the text file output from `hm` is processed by the  [Graphviz dot](https://graphviz.gitlab.io/) software
-   compressed `hm` project archives can be sent via email to colleagues, who
    will then have the information needed to replicate a stratigraphic
    investigation and analysis
-   planning is underway to design an interface from `hm` to Bayesian calibration
    software
