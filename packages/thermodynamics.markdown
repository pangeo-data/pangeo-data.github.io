---
layout: page
title: "Thermodynamics"
description: "Package Design Document"
#header-img: "img/about-bg.jpg"
---

# Thermo Design Document

## Introduction
People need to use equations to calculate thermodynamic quantities all the time. There should be a nice interface to do this.

## Requirements
 - Easy to use interface that minimizes how much you need to memorizes
 - Works on xarray dataarrays
   - Takes full advantage of labeled data and automated broadcasting (e.g. for latitude-dependent calculation of absolute salinity)
 - Handles units -- where present in metadata or passed in by user as keyword
 - Can work for atmosphere or ocean (or arbitrary set of equations)
 - Scales to big data
 - Can take advantage of metadata stored in DataArrays
 - Clear in documentation which form of equations are being solved
 - Support for custom equation of state (particularly for ocean)
 - What does it calculate?
   - Atmosphere
     - Potential temperature
     - saturation vapor pressure
     - Slope of adiabats in T-P space etc
     - etc
   - Ocean
     - Density
     - Slope of isopycnals in T-S space
     - etc
   - All functions of thermodynamic state variables

## Design
 - Isolate solving code into a new package, that gets used by the atmos package
 - Someone can make an ocean package that does something similar to the atmos package, containing equations for ocean thermodynamics
 - Have saturation vapor pressure assumption treated specially as keyword argument
 - Chain numba calls when doing ocean eqns, they're huge!
 - Aim for pure Python / numba implementation

## What are people doing now?
 - Ocean
   - [GSW](https://github.com/TEOS-10/python-gsw)
   - [Seawater toolkit](https://pypi.python.org/pypi/seawater/) (depractated but still widely used)
   - Or using routines extraced from models
   - **No one rolls their own** (formulas too clunky)
 - Atmosphere
   - [aoslib](https://github.com/PyAOS/aoslib) (python wrappers of fortran-based)
   - cf-python (link broken)
   - [atmos](https://github.com/atmos-python/atmos)
   - [climt](https://github.com/CliMT/climt)
   - [climlab](http://climlab.readthedocs.io/en/latest/)
   - [metpy](https://github.com/Unidata/MetPy)
   - [pyCESM](https://github.com/brian-rose/pyCESM)
   - etc
   - Formulas are simple, so **most people just roll their own**
 - Don't have a package that can use labeled xarray data effectively


*****************

[link to hackpad](https://aospy.hackpad.com/Thermo-Design-Document-LEm1RSahXks)
