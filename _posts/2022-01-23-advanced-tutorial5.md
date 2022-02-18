---
layout: post
title: Session 5 - MCDM & Weighted Overlays (Part 1)

---


**Advanced GIS  ·  Sciences Pop Urban School**

Lecturer: Raphaëlle Roffo

&nbsp; 

## I. Session 5 Overview

**Download the [slides](../../../../docs/assets/pdf/advanced-session5-getec2022.pdf)**

- *Environmental Justice and GIS*
- *Building a multi criteria analysis using GIS*
- *Weighting criteria and working with scores*


&nbsp; 

## II. Tutorial

### 2.1 Goals:

- *Using the QGIS Graphical Modeler to build a replicable model*
- *Using the high resolution Population density HDRxFacebook dataset*
- *Defining Selection Criteria*
- *Reclassifying data*
- *Assigning weights to the criteria*
- *Determining final score*


&nbsp; 
### 2.2 Context

Suitability analysis (aka Site Selection) is a very common and powerful type of GIS analysis. The goal of a suitability analysis is to identify the most optimal place for something to be located. The most common approach to suitability analysis consists in overlaying multiple layers representing different criteria each, assigning them relative weights, and recombine those criteria into a single suitability score.

London population is set to increase from 9.03 million in 2021 to 10.11 million by 2036 (source: Greater London Authority). How can we ensure decent standards of living for this additional million dwellers ? 

Research suggests that proximity to green spaces has a strong positive impact on communities’ physical and mental health. In particular, outdoor playgrounds have been proven to increase children’s capabilities and to significantly improve their behavioural and social skills (Brussoni et al, 2017). As seen with the Covid-19 lockdowns, living within walking distance from such parks seems all the more important to the wellbeing of urban communities and especially young children with no access to a private garden.

We also observe that land allocation in central London is not always optimal, with a considerable amount of brownfield  (land that was previously developed but is no longer in use), which is not optimal from an economic, social and environmental perspective.

Literature suggests that conversion of brownfield into green spaces is a very efficient way to lower soil pollution and tap into formerly unutilized land to generate positive social impact on local communities. (Vitiello, 2008; Grenstein & Sungu-Eryilmaz, 2004; Adorjàn et al, 2015).

Our research objective consists in identifying brownfields that are suitable for regeneration into pocket parks with playground facilities, with the purpose of having the greater positive impact on children.


&nbsp; 


### 2.3 Set up the project

Create an `Advanced-Session5` folder and add it to your favourites in your QGIS Browser. Set your CRS to `EPSG:27700`, because we will be focusing on London. Add a basemap of your choice - for instance CartoDB Positron - to your map canvas. If you do not have basemaps under the `XYZ Tiles` section of your browser, refer to the [Intro to GIS Session 3 tutorial](../2021/11/16/intro-tutorial3/) to set it up. 


&nbsp; 

### 2.4 Data Sources

Download the following datasets in your folder and load them onto your map canvas:

- [Brownfield Register](https://data.london.gov.uk/dataset/brownfield_register): polygons of identified brownfield sites in London that are potential candidates to being redeveloped as playgrounds. Download the geopackage file.

- [High Resolution Population Density - Children under 5](https://data.humdata.org/dataset/united-kingdom-high-resolution-population-density-maps-demographic-estimates): Download the `Children Under 5` geotiff dataset, because we want to maximise the number of children with access to the pocket parks. You can learn more about the [methodology here](https://dataforgood.facebook.com/dfg/tools/high-resolution-population-density-maps#methodology).

- From your Advanced GIS Session 3, your [London LSOA layer with Census join](https://github.com/raphaelleroffo/intro-to-gis/raw/main/London-LSOA-2011Census.gpkg): We are interested in the variable `Census 2011 Dataset: % Couple household with dependent children`, because we want to maximise the number of children with access to the pocket parks

- [Existing Green Infrastructure](https://data.london.gov.uk/dataset/green-and-blue-cover): We want to prioritize regeneration of brownfields that are the furthest from existing green spaces. Download the `blueandgreen_ndvi0.1.zip` file that uses a threshold of 0.1 on the NDVI to classify an area as green.

- [Conservation Areas](https://data.london.gov.uk/dataset/conservation_areas): Conservation Areas are subject to planning restrictions and would require additional work to get a redevelopment project approved. We need to exclude those areas from our range of possibilities. Download the geopackage file.


&nbsp; 

Zoom onto the London area, and save your project as `Advanced-Session5.qgz`.


&nbsp; 

## III. Data pre-processing

### 3.1 The QGIS Graphic Modeler











<img src="../../../../docs/assets/images/adv5-1.png" width="800">

&nbsp; 


&nbsp; 

### **[Next Tutorial >](../advanced-tutorial6/)**

### **[Back to the syllabus >](../../../..//tuto2-advanced-gis/)**