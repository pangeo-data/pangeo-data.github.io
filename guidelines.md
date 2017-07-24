---
layout: page
title: Package Guidelines
description: Guidelines for Pangeo packages to follow
---

Our vision for the Pangeo project is an ecosystem of mutually compatible
Geoscience python packages which follow open-source best practices.
These practices are well established across the scientific python community.


### General Best Practices for Open Source

1. Open source license
1. Community guidelines (provide example)
1. Version control of source code (for example, on [github](http://github.org))
1. Thorough test coverage and continuous integration of testing
1. Comprehensive Documentation


### Best Practices for Pangeo Projects

To address the needs of geoscience researchers, we have developed some
additional recommendations.

1. _Solve a general problem:_ packages should solve a general problem
that is encountered by broad groups of researchers.
1. _Clearly defined scope:_ packages should have a clear and relatively
narrow scope.
1. _No duplication:_ developers should try to leverage existing
packages as much as possible to avoid duplication of effort.
1. _Consume and Produce XArray Objects:_ XArray data structures facilitate
mutual interoperability between packages.
1. _Operate Lazily:_ packages should avoid explicitly triggering computation
on [Dask](http://dask.pydata.org/en/latest/array.html) objects.


### Why XArray and Dask?

The Pangeo project strongly encourages the use of XArray data structures
wherever possible.
XArray Dataset and DataArrays contain multidimensional
numeric array data and also the metadata describing the data's coordinates,
labels, units, and other relevant attributes.
XArray makes it easy to keep this important metadata together with the raw data;
applications can then take advantage of the metadata to perform calculations
or create visualizations in a coordinate-aware fashion.
The use of XArray eliminates many common bugs, reduces the need to write
boilerplate code, makes code easier to understand, and generally makes users
and developers happier and more productive in their day-to-day scientific
computing.


XArray's data model is explicitly based on the
[CF Conventions](http://cfconventions.org/), a
well-established community standard which encompasses many different common
scenarios encountered in Earth System science.
However, XArray is flexible and does not _require_ compliance with CF
conventions.

Most geoscientists have encountered the CF data model via the ubiquitous
[netCDF file format](https://www.unidata.ucar.edu/software/netcdf/).
While XArray can easily read and write netCDF files, it doesn't have to.
This is a key difference between software built on XArray and numerous
other tools designed to process netCDF data (e.g. nco, cdo, etc. etc.):
_XArray data can be passed directly between python libraries (or over a
network) without ever touching a disk drive._
This "in-memory" capability is a key ingredient to the Big-Data scalability of
Pangeo packages.
Very frequenctly the bottleneck in data processing pipelines is reading and
writing files.

Another important aspect of scalability is the use of Dask for parallel and
out-of-core computations. The raw data underlying XArray objects can be either
standard in-memory [numpy arrays](http://www.numpy.org/) or
[Dask arrays](http://dask.pydata.org/en/latest/array.html).
Dask arrays behave nearly
identically to numpy arrays (they support the same API), but instead of storing
raw data directly, they store a symbolic computational graph of operations
(e.g. reading data from disk or network, performing transformations or
mathematical calculations, etc.) that must be executed in order to obtain the
data. No operations are actually executed until actual numerical values are
required, such as for making a figure. (This is called _lazy execution_.)
Dask figures out how to execute these computational graphs efficiently on
different computer architectures using sophisticated techniques.
By chaining operations on dask arrays together, researchers can symbolically
represent large and complex data analysis pipelines and then deploy them
effectively on large computer clusters.
