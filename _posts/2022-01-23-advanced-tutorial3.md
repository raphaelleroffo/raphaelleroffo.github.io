---
layout: post
title: Session 3 - Bivariate Choropleths
---


**Advanced GIS  ·  Sciences Po Urban School**

Lecturer: Raphaëlle Roffo

&nbsp; 

## I. Session 2 Overview

**Download the [slides](../../../../docs/assets/pdf/advanced-session3-getec2022.pdf)**

- *Additional raster dataset examples*
- *Georeferencing: use cases*
- *Georeferencing: understanding the different types of transformation*
- *Digitization*


&nbsp; 

## II. Tutorial

### Goals:

- Creating a bivariate choropleth


&nbsp; 
### Download the data

Create an `Advanced-Session3` folder, and download the following data in this folder. Add the folder to your Favourites in QGIS to have an easy access to it.

- [**Census:**](https://data.london.gov.uk/dataset/lsoa-atlas) Census data for the Greater London Metropolitan Area. It’s comes as a CSV file (tabular,non-geographic data) and comes at the LSOA level. Choose the `Current LSOA boundaries post-2011` [file in CSV format](https://data.london.gov.uk/download/lsoa-atlas/0193f884-2ccd-49c2-968e-28aa3b1c480d/lsoa-data.csv) (NOT as `.xlsx`!). If when you click `Download` you land on a page that looks like this, simply press `Ctrl + S` or  `⌘ + S` to save the file, and make sure you give it a `.csv` extension.

<img src="../../../../docs/assets/images/adv3-1.png" width="700">

&nbsp; 


- [**LSOA Boundaries for England & Wales:**](https://geoportal.statistics.gov.uk/datasets/ons::lower-layer-super-output-areas-december-2011-boundaries-generalised-clipped-bgc-ew-v3/about) Lower Super Output Areas (LSOA), the smallest census unit in the UK, like the IRIS zones in France. A few versions are available but we will use the Boundaries Generalised Clipped (BGC) dataset, where the boundaries of each polygons have been generalised to 20 meters, resulting in a less heavy dataset without major information loss. Click `Download` and download the dataset as GeoJSON (or Shapefile).

- But because the LSOA dataset is national and our Census data is limited to Greater London, we need the [**Greater London boundaries**](https://data.london.gov.uk/dataset/inner-and-outer-london-boundaries-london-plan-consultation-2009 ). They will allow us to select the LSOAs that are within the Greater London Metropolitan Area. Download the data as [zipped Shapefile](https://data.london.gov.uk/download/inner-and-outer-london-boundaries-london-plan-consultation-2009/684e59f2-9208-4da1-bf67-d8dfeb72c047/lp-consultation-oct-2009-inner-outer-london-shp.zip).


## III. Data import and pre-processing

### 3.1 Set up the project: Try it on your own!

The first steps of this tutorial are similar to the [Intro to GIS Session 6 tutorial](../2021/11/16/intro-tutorial6/). Try to carry out these steps by yourself to test your skills!

1. Open a new blank project
2. Drag and drop the LSOA-level census dataset as CSV, the LSOA boundaries for England & Wales, and the Greater London boundaries onto your map canvas
3. Clip the LSOA layer to the shape of Greater London, so as to only keep the polygons that fall in Greater London.
4. Join the census table onto your Greater London LSOA polygons.

If you get stuck, don't panic as the following section walks you through this process.

### 3.2 Set up the project: Solution

### 3.2.1 Project setup

Open a blank QGIS project. Make sure the CRS is set to `EPSG:27700`, then drag and drop your Census CSV file, LSOA boundaries and Greater London boundaries onto your map canvas. Save your project as a QGZ file for now, for instance `Advanced-Session3.qgz`. Remember to save your changes often using the flapdisk icon.

<img src="../../../../docs/assets/images/adv3-2.png" width="700">

&nbsp; 

First, for improved clarity, let's rename our layers to make navigation easier:

- Rename `lp-consultation-oct-2009-inner-outer-london` to `Greater London Boundaries`. 
- Rename `Lower_Layer_Super_Output_Areas_(December_2011)_Boundaries_Generalised_Clipped_(BGC)_EW_V3` to `England & Wales LSOA boundaries`
- Rename `lsoa-data` to `Census LSOA London`
  
  
Now, what we want ultimately is a single polygon layer that contains census data at the LSOA level, and covers the Greater London extent.

But notice that, while we are only interested in the Greater London Metropolitan Area (GLMA) and only have census data for that region, the LSOA file we downloaded covers the whole of England & Wales. If we tried running the join between the LSOA boundaries layer and our census table, it may take a very long time to run due to the large number (34 753!) of features in the boundaries layer (= 34 753 rows in the attribute table). 

That’s why in this case and more generally speaking, it can be a good idea to only keep the features of the geographic area you’re interested in before running slightly intensive algorithms such as table joins or geoprocessing. This will speed up the processing time for the following steps.

<img src="../../../../docs/assets/images/adv3-3.png" width="700">

&nbsp; 

### 3.2.2 Clipping the LSOA to Greater London extent

First, we want to create a subset of the LSOA layer that only contains LSOAs in the GLMA. Use the `Clip` tool to get a neat, cookie-cutter like selection of LSOAs within the GLMA boundaries. Find the `Clip` in your Processing toolbox and set it up to clip your LSOAs to the shape of `Greater London Boundaries`. Set the output to be saved as a geopackage layer. You can call this geopackage `Advanced-Session3` and then the layer to be called `Greater London LSOA`. Press `Run`.

<img src="../../../../docs/assets/images/adv3-4.png" width="700">

&nbsp; 

You can now remove the `England & Wales LSOA Boundaries` and `Greater London Boundaries` layers from your map canvas, and save the changes.

<img src="../../../../docs/assets/images/adv3-5.png" width="700">

&nbsp; 


### 3.2.3 Joining the census data onto the LSOA polygons

The census data comes as a non-spatial table. We want to combine information from that table and the geographic boundaries of the LSOAs into a single dataset, using a table join.

If we look at the attribute table for the`Greater London LSOA` layer, it contains the LSOAs in Greater London, with some basic information and a column with a unique identifier for each LSOA: the `LSOA11CD` column.

If we look at the attribute table for the `Census LSOA London` table, it contains a lot of variables but also a `Lower Super Output Area` column which contains very similar codes to `LSOA11CD`. This is the official LSOA code, produced by the Office for National Statistics (ONS). After a couple quick checks (comparing Names and Codes in both table), we confirm that they are indeed the same codes in both tables.

Note that the `LSOA11NM` and `Names` columns would also seem to be good matches as Key fields for the join; however names are more prone to spelling differences (a space or apostrophe might be present in one table and not the other). That's why when available, you should alwyays opt for the standardised code instead!

<img src="../../../../docs/assets/images/adv3-6.png" width="700">

&nbsp; 

Double-click the `Greater London LSOA` layer to access the `Layers properties`, navigate to the `Joins` tab and click the Green Plus sign to create a new join based on those two fields. You can edit the custom prefix to be shorter, for instance `Census_`.

Press `OK` in that window, then `OK` again to close the Layer properties. If you open your attribute table you will now see the additional fields for taht layer.

<img src="../../../../docs/assets/images/adv3-7.png" width="700">

&nbsp; 

Now can be a good time to save a copy of this "super" LSOA Census layer in your geopackage. Right-click your London LSOA layer, `Export` > `Save Features as...` , save it in your `Advanced-Session3` geopackage and give it a descriptive name, for instance `LSOA-with-Census`. Make sure the CRS is British National Grid. You can then remove the two other layers. You can also import a basemap as backdrop to your project. If you do not have basemaps under the `XYZ Tiles` section of your browser, refer to the [Intro to GIS Session 3 tutorial](../2021/11/16/intro-tutorial3/) to set it up.

<img src="../../../../docs/assets/images/adv3-8.png" width="700">

&nbsp; 

&nbsp; 

## IV. Population density choropleth


### 4.1. Fixing the data type

Now, among all the variables in the census, we are interested in population density, present in the field `Population density; Persons per hectare 2013`. We want to build a choropleth of population density, which we will later on combine with flood risks exposure.

The field is not available for the use of graduated symbology. Can you guess why?

<img src="../../../../docs/assets/images/S6-16.png" width="700">

&nbsp; 

If you recall from our previous tutorial, the problem comes from the data type of the field. In your `Layer symbology`, under the `Fields` tab, open the field calculator and see if you can figure out which expression you need to write to obtain a numerical `PopDensity` field.

<img src="../../../../docs/assets/images/S6-17.png" width="700">

&nbsp; 

Once your field is created, remember to exit `Editing mode` by pressing the yellow pencil and saving your changes!





&nbsp; 


&nbsp; 

Congrats, you have successfully completed this tutorial!

&nbsp; 

&nbsp; 

### **[Next Tutorial >](../advanced-tutorial4/)**

### **[Back to the syllabus >](../../../..//tuto2-advanced-gis/)**