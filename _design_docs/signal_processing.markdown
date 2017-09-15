---
layout: page
title: "Signal Processing"
description: "Package Design Document"
#header-img: "img/about-bg.jpg"
---


# Signal processing design

## Introduction
Analyzing and characterizing the temporal and spatial scales from the outputs of climate model components (atmosphere, ocean, hydropshere, cryosphere) require the use of signal processing techniques. This python package aims at gathering such tools in the framework of pangeo-data using xarray and dask.

## Relation to existing packages
 - pyClim: filtering and timeseries analysis
 - eofs
 - spanlib: spectral analysis library
 - NCL 
 - ...

## Suggested package name
Here is the section for barnstorming about the package name.
For the moment, I am thinking about xscale  (for "across scales") because the idea of this package is to analyze and separate the different time and space scales in a climate signal. I don't really know if something sounding similar to xarray is a good or a bad idea. Any other ideas ?

## Requirements 
 1. For the moment, we may classify the different techniques required into the different sections:
   - General statistics
   - Correlation, covariance, autocorrelation, regression, etc
   - Structure functions (turbulence)
   - Significance tests associated to those statistics
 2. Filtering
   - Linear filters based on convolution products
   - Non-linear filters based on regression methods (polynomial, LOESS ...)
   - Spectrally-based filtering
 3. Multi-dimensional spectra
   - Pre-processing (detrending, tapering, zero-padding, multi-tapering)
   - Post-processing (normalization, visualization)
   - Time-frequency spectrum
   - Wavelets
   - Derivative in Fourier space
   - Cross-spectrum analysis
   - Spectrum from structure functions (turbulence)
 4. Principal Component Analysis (PCA)
   - Empirical Orthogonal Functions (EOF) (Standard, Complex, Rotated)
   - Canonical Correlation Analysis (CCA)
   - Single and Multi Tapper Singular Spectrum Analysis (SSA M-SSA) 
   - Nonlinear Laplacian spectral Analysis
 5. Noise reduction techniques
 6. Information theory 

## Design approach
First, there are two solutions for the structure of the signal processing package:
 1. One big package that includes all the different signal processing techniques in an unique repository.
 2. One  package that is a collection of several sub-packages, which separate  the different signal processing techniques by field (e.g., spectral,  filtering, eof). Such sub-packages would have their own repository.
Which one should we use ?

## Open questions
 - Should this "big" package be splitted into several packages ?
 - Should we contribute to the eofs package or implement a new version ?
   - Has anyone approached Andrew (author of eofs)? I reckon he'd be keen to be involved.
     - Not that I'm aware of, but we should.  Would be good in general to loop in in the UK Met Office/Iris/etc. crowd, which he is a part of.
     - I could get in touch with him. Maybe we should wait to have a clear visibility with the website.
 - I am thinking about turbulence diagnostics. This may involve both the vector calculus and the signal processing packages. It could result in another project based on top of those packages and dedicated to compute spectral slopes, cospectrum for energy transfer, structure functions, linear instability etc.
 


*********************

[link to hackpad](https://aospy.hackpad.com/Signal-processing-design-IAGSTdb17Ti)
