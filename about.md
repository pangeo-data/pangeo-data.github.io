---
layout: page
title: About Pangeo
description: "What is Pangeo?"
---

Overview
========

Pangeo is a community effort for big data in the geosciences.

## Motivation

There are several building crises facing the geoscientific community:

- Big Data: datasets are growing too rapidly and legacy software tools for scientific analysis can't handle them. This is a major obstacle to scientific progress.
- Technology Gap:  a growing gap between the technological sophistication of industry solutions (high) and scientific software (low).
- Reproducibility: a fragmentation of software tools and environments renders most geoscientific research effectively unreproducible and prone to failure.

We believe these challenges can all be addressed through a unified effort.

## Mission Statement

Our mission is to cultivate an ecosystem in which the next generation of open-source analysis tools for the geosciences can be developed, distributed, and sustained. These tools must be scalable in order to meet the current and future challenges of big data, and these solutions should leverage the existing expertise outside of the geoscientific community.

## Vision

We envision a collection of related but independent open-source packages that meet specific scientific needs within the geoscience fields. These packages will follow modern best practices for software development, including:

- hosting on GitHub,
- testing,
- coverage,
- continuous integration,
- comprehensive documentation, and
- a welcoming and inclusive development culture.

At the core of the Pangeo concept is a collection of tools that are already widely used throughout and beyond the geoscientific community. Tn recent years, the open-source scientific software stack in Python has grown to become rich and full featured.

![The State of the Stack](../img/scientific-python-28-638.jpg "The State of the Stack")
*Caption: The Python Data Stack. Source:  [Jake VanderPlas](https://staff.washington.edu/jakevdp/),
  ["The State of the Stack,"](https://speakerdeck.com/jakevdp/the-state-of-the-stack-scipy-2015-keynote) SciPy Keynote (SciPy 2015).*

In practice, the "python data" software stack (see above) currently provides the most stable and powerful foundation layer for our desired tools. In particular, two widely used packages in the geoscientific software community, `xarray` and `dask`, provide a mechanism to easily build scalability into scientific analysis.  Our vision of future geoscientific software involves the adoption of these common software layers, and a clear communication between developers to define project scope and dependency that eliminates redundancy and fragmentation.

The current Pangeo efforts are focused on closing some of the pressing concerns on scalability of the software tools shown above. In particular, we are developing tools that support distributed parallel computing in high-performance-computing and cloud-computing environments.

![Pangeo Cartoon](../img/pangeo_cartoon.png "Pangeo Cartoon")
*Caption: The Pangeo Platform; source:  Abernathey et al (2017),
  ["Pangeo: An Open Source Big Data Climate Science Platform "](https://figshare.com/articles/Pangeo_NSF_Earthcube_Proposal/5361094) NSF award 1740648.*

## Get Involved
The scientific culture in the geoscientific community must be tied to, and evolve from, the community's software culture.  Hence, we depend upon contributions from the entire community, both scientific and industrial.

We encourage everyone to get involved by:

- contributing to the goals and vision of the organization,
- contributing to the design documents of the proposed software,
- contributing to the software, via issues and pull requests, and/or
- using the software for your scientific analysis and letting us know about your experiences (e.g., contributing to examples)

For now, community discussion is happening on our
 - [pangeo google group](https://groups.google.com/forum/#!forum/pangeo).
 - [pangeo github issues](https://github.com/pangeo-data/pangeo/issues).

************
