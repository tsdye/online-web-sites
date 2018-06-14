+++
title = "Data Tables"
author = ["Thomas S. Dye"]
lastmod = 2018-06-10T08:43:25-10:00
draft = false
weight = 140
+++

There are seven data tables potentially used as input to `hm`.  A project
requires a table for units of stratification and for observed stratigraphic
relations, but the other five tables are optional.


## Units of Stratification, or Contexts {#units-of-stratification}

This input file describes units of stratification, or contexts, identified by the
archaeologist.

label
: context identifier (primary key)

unit-type
: one of `interface` or `deposit`

position
: one of `surface`, `basal`, or `other`

period
: period identifier (foreign key)

phase
: phase identifier (foreign key)

url
: node link (svg output only)

The file `roskams-h-contexts.csv` is an example.  As this example shows, columns
may be empty, as the `period`, `phase`, and `url` columns are in this example.
Note however that each line of the file has five commas so the `hm` software can
determine that there are indeed six columns in the table.

```text
label,unit-type,position,period,phase,url
1,deposit,surface,,,
2,deposit,surface,,,
3,deposit,other,,,
4,deposit,other,,,
5,deposit,basal,,,
```


## Observed Stratigraphic Relations {#observed-stratigraphic-relations}

This table includes observations of stratigraphic superposition. Its
first two columns refer to values from the `label` column of the
contexts table.

younger
: stratigraphically superior context label (foreign key)

older
: stratigraphically inferior context label (foreign key)

url
: arc link (svg output only)

The file `roskams-h-observations.csv` is an example.  Note that the third column
is empty save for the column head, `url`.

```text
younger,older,url
1,3,
1,4,
1,5,
2,3,
2,5,
3,5,
4,5,
```


## Inferences of once-whole contexts {#inferred-parity-relations}

This table contains inferences of parity between pairs of discontiguous
contexts.

first
: context label (foreign key)

second
: context label (foreign key)

The file `inference-eg.csv` in the `fig-12-chronology` example is shown below.

```text
first,second
7,8
15,16
11,14
```


## Periods {#periods}

This table describes periods, which are groups of interfacial contexts
believed to have been in use at the same time.

id
: a unique integer to identify the period (primary key)

label
: name of the period used in the legend

attribute
: zero-based integer scale for a
    [Brewer color](http://www.graphviz.org/doc/info/colors.html#brewer)

description
: optional field not used by `hm`

An example is the file `bldg-1-5-periods.csv`.

```text
id,label,attribute,description
1,Building 1,5,
2,Outside,6,
3,Building 5,7,
```


## Phases {#phases}

This table describes phases, which are groups of depositional contexts
believed to have been deposited pene-contemporaneously, typically
because they share diagnostic artifactual content.

id
: a unique integer to identify the phase (primary key)

label
: name of the phase used in the legend

color
: zero-based integer scale for a
    [Brewer color](http://www.graphviz.org/doc/info/colors.html#brewer)

description
: optional field not used by `hm`

The file `phases-eg.csv` is shown below.  As this file indicates, the `hm`
software does not pay attention to the column headers, which you are free to
label in any pleasing way.

```text
id,label,attribute,url
1,Phase I,5,http://www.tsdye.com
2,Phase II,6,http://www.tsdye.com
```


## Events {#events}

This table associates events and contexts and specifies the nature of
the association using terms introduced to archaeology by Jeffrey S. Dean in an
essay entitled "Independent dating in archaeological analysis" published in
_Advances in Archaeological Method and Theory_ in 1978.

theta
: unique label (primary key)

context
: context identifier (foreign key)

lab
: dating laboratory identifier

association
: one of `disjunct`, `direct`, `disparate`

An example is the file `bldg-1-5-dates.csv`.  As this example shows, the `hm`
software does not care if you add extra columns to the table.  The software
works with columns by position, so do not be tempted to switch columns around.

```text
theta,context,lab,association,original context
1,3810+,OxA-11046,disjunct,3810
8,1297+,OxA-11045,disjunct,3036
10,3030+,OxA-11044,disjunct,3030
5,2165+,PL-972424A,disjunct,2198
4,2165+,PL-980558A,disjunct,2181
2,2165+,OxA-11043,disjunct,2166
3,2165+,OxA-11042,disjunct,2165
28,1951+,OxA-16800,associated,1960
27,1940+,OxA-16799,associated,1959
```


## Event Order {#event-order}

This optional table contains information on the temporal order of events
from the same context.

older
: theta label of older event (foreign key)

younger
: theta label of younger event (foreign key)

The example file `date-order.csv` is shown below.

```text
older,younger
3,4
```
