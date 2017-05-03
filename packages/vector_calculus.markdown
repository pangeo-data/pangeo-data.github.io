---
layout: page
title: "Vector Calculus"
description: "Package Design Document"
#header-img: "img/about-bg.jpg"
---


# Vector calculus operations: "pangeo-mosaics"

## Design document for pangeo-mosaics package

## Introduction : pangeo.mosaics 
Arrays of data from ocean/atmosphere models or gridded satellite data  are defined at particular locations on a particular type of grid (structured or unstructured). Several data analysis tasks require an a-priori knowledge of the grid geometry and of the location of model data on the grid. This information should be known for computing for instance spatial derivative and spatial integrals.  In practice, a horizontal derivative of vorticity is performed differently whether the vorticity is defined at cell corners or at cell edges.

The purpose of this package is to store data that describes these grid specifications in order to provide methods for computing grid-dependent quantities on xarray objects corresponding to gridded data. 

## Relation to existing packages
Several xarray-based tools already exist for computing derivatives and grid-related quantities from atmospheric or ocean model data. Among others : 
 - [xgcm](https://github.com/xgcm/xgcm) : Python package for analyzing general circulation model output data.  The author (Ryan Abernathy) wants to fold it into mosaic/deprecrate it if possible.
 - [infinite-diff](https://github.com/spencerahill/infinite-diff/) : Simple finite differencing methods for derivatives and advection on physical domains.  Currently being analyzed for any useful functionality that can be moved into mosaic; will be deprecated once that is done.
 - [windspharm](https://github.com/ajdawson/windspharm) : Compute vorticity, divergence, and others using spherical harmonics.  This is a slightly different use-case than the main mosaic goal, because the calculations are spectral and agnostic to the grid information/finite differencing methods used by the original model.
 - [oocgcm](http://oocgcm.readthedocs.io/en/latest/)  : Proof of concept package on which mosaics will be based.

A large number of numpy based packages already exist. Listing all of them is probably out of scope. We are aware of the following packages : 
 - [PyDom](http://servforge.legi.grenoble-inp.fr/projects/PyDom/)  : analysis package for NEMO ocean model output. deprecated, no longer supported
 - [pycomodo](http://pycomodo.forge.imag.fr/) : tools for intercomparison of solutions of ocean models used in France. 
 - [mitgcm_python](https://github.com/braaannigan/mitgcm_python)  :  Python code for reading in mitgcm outputs from tiled output
...

None of the above package allows to apply straighforwardly the same analysis to different model data sources. 

## Requirements 
The library should provide methods 
 - for storing arrays that describe the physical grid (positions of cell centers, width of grid cells, etc..)
 - for defining data structures for holding vector fields
 - for performing basic vector calculus (scalar product of vector fields, )
 - for moving data from one grid location to other grid location (eg. u-points to t-points on C-grid)
 - for computing spatial derivatives (gradients, curl, laplacian,... )
 - for computing horizontal and vertical advection terms $u\cdot\grad \tau$ and $w\partial_z  \tau$
 - for compute spatial integral in regions defined from masks (x,y or xyz)
 - for computing fluxes of quantities across sections 
 - for restricting the analysis to particular subregion of the initial dataset (slicing grid class for regular grids)

The library should also : 
 - be aware of the land-ocean mask  for oceanographic applications
 - be adapted to data sources that do not provide grid descriptor files (eg. when only array of latitudes and longitude of cell centers are available)
 - be adapted to time evolving grids (eg. ALEs)
 - treat as cleanly as possible the wrap-around ( east west cyclic boundary, and north fold)


## Design approach
 - The library will implement classes that hold information and method for particular grid types. 
 - The library will distinct objects for 2d grids and 3d grids. 
 - The API should be as close as possible for all the classes, whatever the grid type (Arakawa C, B, etc...)
 - The definition of the methods associated to the grid are data-source agnostic but the creation of the grid class should be data-source specific (depends on the model conventions)
 - For Arakawa C-grids, the library will use pycomodo conventions for C-grid models

## Dependencies and relation to other pangeo packages. 
 - interaction with regridding tools (in particular for statistics in boxes)
 - interaction with data-store package should be clarified. 

## Remaining open questions 
 - Shall we use gridspecs conventions for defining grid related quantities for non-C-grids ? 
 - Shall we provide methods for unsrtuctured grids ?
 - How to use model dependant discretization scheme ? 
 - How to deal with units for updating metadata ? using pint ?
   - Probably should not use Pint, because two different packages that both use Pint cannot be used together. Or Pint can be used in a way that the user never interfaces with the Pint unit registry.
 - Shall we think of a way to associated the derivative operators to particular dataarrays ? see ticket 17 on oocgcm...
 - How to describe sections ? 
 - How to deal with the various vertical coordinates?  

## Algorithms


## Implementation plan and timeline
 - start with two-dimensional C-grid after cleaning of oocgcm
 - improve wrapaound and advection terms in 2d Arakawa C-grids. 
 - test the creation of grid objects from different data sources. 
 - implement to 3d Arakawa C-grids. 

## Testing series


************

[link to hackpad](https://aospy.hackpad.com/Vector-calculus-operations-pangeo-mosaics-oAPE6Rqvcwt)
