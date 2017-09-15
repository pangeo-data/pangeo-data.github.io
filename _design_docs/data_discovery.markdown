---
layout: page
title: "Data Discovery"
description: "Package Design Document"
---

# Data Storage/Discovery Design Document


## Introduction


## Requirements

### Use case 1

Be able to "ingest" data from multiple re-analyses, observational data products (e.g. satellite, Argo float, and others), and major model inter-comparison projects (CMIP) into a uniform format that xarray can work with.

### Use case 2

Be able to easily specify and load data from climate model experiments conducted by systematically varying parameters and / or model configurations

Access datasets hosted remotely - on a remote FTP server, on an HPC machine/cluster, on the cloud (OPeNDAP THREDDS; S3; boto + other cloud options) 
Method for specifying labels in order to align ingested datasets
"Import" existing data from disk
Check for newer version of data and update if necessary
Emulate [goat-geo](http://www.goat-geo.org/opendap-and-cmip5/) ability to pull/store useful re-analysis or observational datasets
Open Science Data Commons - part of OCC; a cloud hosting of lots of useful data from NASA/NOAA
Output some sort of record indicating the provenance of different data sources ingested, including original locations and versions.
 
## Design


![](../data_discovery.jpg)


## Other software

The Community intercomparison suite (http://www.cistools.net/) is a command line tool for the atmospheric sciences that uses a plugin framework to deal with loading and regridding data from a range of sources - simulations, flight campaigns, satellites, ground stations etc.. It can also be used as a python library, but this hasn't been developed particularly far yet.

This is worth looking at as well: https://pachyderm.io/ , https://github.com/PyFilesystem
Pachyderm is an abstraction for pipelines that reduces it the pipeline to io and compute while keeping track of data a-la-git. PyFilesystem is file system abstraction. 


********************

[link to hackpad](https://aospy.hackpad.com/Data-StorageDiscovery-Design-Document-fM6LgfwrJ2K)
