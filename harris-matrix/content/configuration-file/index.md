+++
title = "Configuration File"
author = ["Thomas S. Dye"]
date = 2018-03-18T16:12:00-10:00
lastmod = 2018-06-10T08:43:25-10:00
draft = false
weight = 120
+++

The `hm` configuration file conforms to the [informal `.ini` file standard for
configuration software](https://en.wikipedia.org/wiki/INI_file), which specifies a structure composed of sections,
options, and values.

Here are the sections in an `hm` configuration file listed in alphabetical order.

<a id="org4130e40"></a>
```lisp
(use-package :hm)
(defparameter *seq* (run-project/example :roskams-h :draw-sequence nil))
(format t "~%Sections:~%")
(show-configuration-sections *seq*)
```

```text
Read one initialization file: <path-to>/quicklisp/local-projects/harris-matrix/examples/roskams-h/roskams-h.ini.
Reading table from roskams-h-contexts.csv.
Nodes added to the sequence graph.
Reading table from roskams-h-observations.csv.
Arcs added to the sequence graph.
Chronology graph off.
Creating units classification.
Archaeological sequence configured.

Sections:
General configuration
Graph analysis configuration
Graphviz chronology edge attributes
Graphviz chronology graph attributes
Graphviz chronology node attributes
Graphviz legend node attributes
Graphviz sequence adjacent edge arrowhead
Graphviz sequence adjacent edge colors
Graphviz sequence adjacent edge fontcolor
Graphviz sequence adjacent edge fontsize
Graphviz sequence adjacent edge penwidths
Graphviz sequence adjacent edge styles
Graphviz sequence adjacent node colors
Graphviz sequence adjacent node fillcolors
Graphviz sequence adjacent node fontcolors
Graphviz sequence adjacent node penwidths
Graphviz sequence adjacent node polygon distortion
Graphviz sequence adjacent node polygon image
Graphviz sequence adjacent node polygon orientation
Graphviz sequence adjacent node polygon sides
Graphviz sequence adjacent node polygon skew
Graphviz sequence adjacent node shapes
Graphviz sequence adjacent node styles
Graphviz sequence classification
Graphviz sequence edge attributes
Graphviz sequence edge color schemes
Graphviz sequence edge font color schemes
Graphviz sequence graph attributes
Graphviz sequence node attributes
Graphviz sequence node color schemes
Graphviz sequence node fill color schemes
Graphviz sequence node font color schemes
Graphviz sequence reachability edge arrowhead
Graphviz sequence reachability edge colors
Graphviz sequence reachability edge fontcolors
Graphviz sequence reachability edge fontsize
Graphviz sequence reachability edge penwidths
Graphviz sequence reachability edge styles
Graphviz sequence reachability node colors
Graphviz sequence reachability node fillcolors
Graphviz sequence reachability node fontcolors
Graphviz sequence reachability node penwidths
Graphviz sequence reachability node polygon distortion
Graphviz sequence reachability node polygon image
Graphviz sequence reachability node polygon orientation
Graphviz sequence reachability node polygon sides
Graphviz sequence reachability node polygon skew
Graphviz sequence reachability node shapes
Graphviz sequence reachability node styles
Graphviz sequence unit edge arrowhead
Graphviz sequence unit edge color
Graphviz sequence unit edge fontcolor
Graphviz sequence unit edge fontsize
Graphviz sequence unit edge penwidth
Graphviz sequence unit edge style
Graphviz sequence unit node color
Graphviz sequence unit node fillcolor
Graphviz sequence unit node fontcolor
Graphviz sequence unit node penwidth
Graphviz sequence unit node polygon distortion
Graphviz sequence unit node polygon image
Graphviz sequence unit node polygon orientation
Graphviz sequence unit node polygon sides
Graphviz sequence unit node polygon skew
Graphviz sequence unit node shape
Graphviz sequence unit node style
Input file headers
Input files
Output file headers
Output files
```

Each section typically includes several options, as shown in the `General
 configuration` section, below.  Here, you can see that string values, such as
`project-directory` are not quoted.  Boolean options recognize several pairs of
terms: `on/off`, `yes/no`, `true/false`, or `1/0`.

```text
[General configuration]
chronology-graph-draw = off
project-directory = ~/quicklisp/local-projects/harris-matrix/examples/fig-12-chronology/
legend = off
assume-correlations = yes
fast-matrix = on
```

Another example, the `Graphviz sequence graph attributes`, below, illustrates
strings, integers, and real numbers. In this example, the `fontsize` and
`margin` options take a real number(s), and the `fontsize-subscript` is set to
an integer. Options left blank specify that the `dot` software should use a
default value.

```text
[Graphviz sequence graph attributes]
colorscheme = x11
bgcolor = white
fontname = Helvetica
fontsize = 14.0
fontcolor = black
label = Harris Figure 12 (with periods)
labelloc = t
style = filled
size =
ratio =
page =
dpi =
margin = 0.5,0.5
fontsize-subscript = 10
splines = ortho
url = http://tsdye.github.io/harris-matrix/
```
