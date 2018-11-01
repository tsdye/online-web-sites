+++
title = "ArchaeoPhases"
author = ["Thomas S. Dye"]
date = 2018-11-01T08:46:00-10:00
draft = false
+++

In Spring 2016 I took up the opportunity to participate in a two-day conference
on Bayesian statistics in archaeology in Nantes, France. Hosted jointly by
Philippe Lanos of the Universit&eacute; de Rennes and Anne Philippe at the Universit&eacute;
de Nantes, it was a chance to meet and talk with scholars actively working with
Bayesian statistics, mostly as archaeologists apply those statistics to dating
problems. I was able to catch up with two long-time friends, Caitlin Buck and Bo
Meson from Sheffield, and had especially interesting conversations with Andrew
Millard from Durham and Frances Healy from Cardiff, whose archaeological work
I'd read with interest and admiration.

Philippe and Anne had recently released a Bayesian calibration application,
[`ChronoModel`](https://chronomodel.com/), that implements a slightly different model than the one Caitlin
implemented in [`BCal`](https://bcal.shef.ac.uk/) and also used by [`OxCal`](https://c14.arch.ox.ac.uk/oxcal.html). Listening to Anne, Philippe, and
Caitlin discuss the pros and cons of their design decisions helped me make sense
of the high-level statistical papers that describe the decisions. The main
difference is how the models estimate phase boundaries. [`BCal`](https://bcal.shef.ac.uk/) and [`OxCal`](https://c14.arch.ox.ac.uk/oxcal.html) model the
phase boundaries based on an assumption about the distribution of samples within
the phases; [`ChronoModel`](https://chronomodel.com/) doesn't make the assumption needed to model the phase
boundaries, so it uses the earliest and latest estimates from samples assigned
to the phase. The upshot: don't expect [`ChronoModel`](https://chronomodel.com/) to agree with [`BCal`](https://bcal.shef.ac.uk/) or [`OxCal`](https://c14.arch.ox.ac.uk/oxcal.html)
on phase boundary estimates---if they do agree, then it is simply a matter of
chance.  Also, if the chronological model you are building uses phase boundaries
as target events, then do take the time to understand exactly what the phase
boundary estimates are giving you.

I learned about [`ArchaeoPhases`](http://www.math.sciences.univ-nantes.fr/~philippe/ArchaeoPhases.html) during the conference dinner when the discussion
turned to the open-source statistical software application, [`R`](https://www.r-project.org/). Anne was excited
by [`Shiny`](https://shiny.rstudio.com/), an [`R`](https://www.r-project.org/) package for designing interactive web applications. I agreed with
her that applications created with it might help archaeologists gain access to
the statistical power of [`R`](https://www.r-project.org/).

More exciting for me was learning that [`ArchaeoPhases`](http://www.math.sciences.univ-nantes.fr/~philippe/ArchaeoPhases.html) included an improved
version of the Tempo plot, which I had recently developed as an open-source
software project. My version of the Tempo plot assumed a normal approximation
throughout, which made it easy to implement in [`R`](https://www.r-project.org/) and didn't tax my limited grasp
of mathematics. Anne used her considerable mathematics skills to put the Tempo
plot on a firmer Bayesian footing. The [`ArchaeoPhases`](http://www.math.sciences.univ-nantes.fr/~philippe/ArchaeoPhases.html) user can now choose between
the normal approximation and the full Bayesian treatment when calling the
`TempoPlot` function. Check it out!

<a id="org861f48e"></a>

{{< figure src="/graphs/lkfs-tempo-calendar.jpg" caption="Figure 1: Example of a Tempo plot with the full Bayesian treatment." >}}
