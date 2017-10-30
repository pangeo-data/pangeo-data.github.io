---
layout: page
title: "Regions and Shapes"
description: "Package Design Document"
#header-img: "img/about-bg.jpg"
---

# Regions and shapes

## Introduction

Climate analysis requires use of geometry data for analysis purposes.  A vector-based representation of this geometry is particularly useful for intermodel comparisons.  An existing repository https://github.com/MPAS-Dev/geometric_features includes the capability to store point, transect, and region information in a database of geojson files.  Possible extension with http://salem.readthedocs.io/en/stable/index.html could be used to make region masks.  A possible use case: specification of river runoff data (flow time series) corresponding to a point.

## Requirements

Community geometry should be specified in a version-controlled database
File formats should be open source and easy to use, e.g., geojson
region masks should be produced from input of a grid and geojson geometry file

## Design

### Application programing interfaces (API)

## Testing

*************

[link to hackpad](https://aospy.hackpad.com/Regions-and-shapes-xvOM5Zwvgqf)
