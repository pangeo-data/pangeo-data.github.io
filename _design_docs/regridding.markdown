---
layout: page
title: "Regridding"
description: "Package Design Document"
#header-img: "img/about-bg.jpg"
---

# Regridding Design Document

## Introduction (minimally needed)
This package will provide geospatial regridding/remapping functionality on xarray data objects

## Background
Geospatial gridded datasets (climate models, remote sensing images, etc.) frequency exist on dissimilar grids. Existing tools (CDO, NCL, NCO, ESMF, etc.)  have addressed this with both stand-alone command line tools and python libraries. While existing python libraries have some of the desired functionality, they do not currently interface with xarray.

## Requirements
This is a list of requirements:
 - Interface directly with xarray, utilizing coordinates defined on `DataArray` objects.
 - Provide a remap-like interface (`da.remap.remap_like(da_target, how='bilinear')`)
 - Provide a remap-to interface (`da.remap.remap_to([('lat', 0.5), ('lon', 0.75)], how='nearest')`)
 - Provide access to mapping tables
 - A series of resampling/remapping algorithms
   - linear/bilinear interpolation
   - distance weighted
   - nearest neighbor
     -Nearest neighbor for 1D source coordinates will probably make it into xarray as a special case for my vectorized indexing rewrite (in `reindex`/`reindex_like`)
   - conservative area (1st/2nd order)
   - largest area fraction
 - Use dask for out of core / scaling
 - or just wrap existing remapping lib

## Design
My original thought here would be to xarray's accessor namespace on top of the `DataArray`. In my examples above, this would be the `remap` attribute.

To be efficient, many of these regridding techniques will need to make use of a tree datastructure for multi-dimensional lookups. It would nice could be integrated a bit more deeply into xarray (e.g., `KDTreeIndex`)

### Application programing interfaces (API)
Often it is useful to specify function signatures, class methods / attributes.

## Testing
This  lists tests that should be used to verify that the code is working  correctly, especially with respect to meeting requirements.
Ideally, this would be a list of unit tests demonstrating that requirements have been met.

*************

[link to hackpad](https://aospy.hackpad.com/Regridding-Design-Document-tENJARIeg83)
