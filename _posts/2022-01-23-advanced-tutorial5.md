---
layout: post
title: Session 5 - MCDM & Weighted Overlays (Part 1)

---


**Advanced GIS  ·  Sciences Po Urban School**

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

- [Existing Open Greenspaces](https://osdatahub.os.uk/downloads/open/OpenGreenspace): We want to prioritize regeneration of brownfields that are far from existing green spaces. Download the `TQ` tile, which covers Greater London, as an ESRI Shapefile. Notice that the data folder you download contains a polygon layer (the actual open green spaces) and a point layer for the access points to those open green spaces (gates / entrance). We will actually use those points as our reference as they determine the accessibility of the green area more precisely.

- [Conservation Areas](https://data.london.gov.uk/dataset/conservation_areas): Conservation Areas are subject to planning restrictions and would require additional work to get a redevelopment project approved. We need to exclude those areas from our range of possibilities. Download the geopackage file.


&nbsp; 

Zoom onto the London area, apply some basic styling (use singleband pseudocolour for the population density geotiff),and save your project as `Advanced-Session5.qgz`.

In case you are stuck with the setup, you can also launch the project using [this geopackage](https://drive.google.com/file/d/1RZ6vlAGc4oh1sI8bmswkZsOHOK9Pk839/view?usp=sharing) + your downloaded GeoTIFF.


<img src="../../../../docs/assets/images/adv5-0.png" width="800">

&nbsp; 

## III. Model setup

### 3.1 The QGIS Graphical Modeler

The QGIS Graphical Modeler is the equivalent to the ESRI ArcGIS "Model builder". It allows you to clearly take inputs, run them through algorithms of your choice (= geoprocessing tools, raster analysis tools, basically anything that is available to you through your `Processing Toolbox`) and produce outputs. One advantage of the Graphical Interface is that it allows you to replicate your workflow and automate the run of your model. This is very useful, for instance, if you realise you want to change input but apply the exact same methodology. Or if you want to edit one parameter of one of your algorithms to re-run your entire analysis. It makes repeating, tweaking, iterating through a workflow much easier.

It can be accessed through your top menu `Processing` > `Graphical Modeler...` or in your Processing Toolbox by clicking on the cogs icon > `Create new model...`. A new window opens:

<img src="../../../../docs/assets/images/adv5-1.png" width="800">

&nbsp; 

In the top toolbar of that window, hover over the different icons. The first set of icons help you open an existing model, save your model, save your model to your project. The second allows you to pan across / select / undo or redo actions / zoom in and out of your model overview. The next set of icons enables you to export your model as a Python script or as an image/PDF/SVG. Finally, the book icon lets you write some help documentation for your model, and the green triangle can be clicked to run your model.

Give a name to your model and a group (For instance, `Pocket_Park_Selection` in a `Suitability_Analysis` Group). 


<img src="../../../../docs/assets/images/adv5-2.png" width="800">

&nbsp; 

Then, click `Save as...` to save your model, then click the icon to save it to your project too. 


<img src="../../../../docs/assets/images/adv5-3.png" width="800">

&nbsp; 


Note that if you close this window and don't find your model when you reopen that window, you can use the `Open Model...` icon to retrieve it. Remember to save your changes frequently.


<img src="../../../../docs/assets/images/adv5-4.png" width="800">

&nbsp; 


### 3.2. Clipping workflow for your population density raster

#### 3.2.1 Add a raster input for your population density grid layer

As a first step we want to clip our population density grid for children under 5 to the extent of our London LSOA layer.

In your Graphical Modeler interface, click the tab `Inputs` and have a look at the available parameters. Drag a `Raster layer` onto your modeling area. Give it a descriptive name and make sure it's a mandatory input into your model.


<img src="../../../../docs/assets/images/adv5-5.png" width="800">

&nbsp; 

#### 3.2.2 Add a vector input for your LSOA layer


In order to clip this layer to the London extent, we also need to feed the London LSOA layer into our model. In the parameters, click `Vector Layer`. Add a layer called `London LSOA` of type `Polygon`, and make sure it's a mandatory input.


<img src="../../../../docs/assets/images/adv5-6.png" width="800">

&nbsp; 

Your two layers are now ready to be processed. Press the Save button (you might need to "overwrite" your existing model in its saved location - go ahead). Note that so far QGIS does not know which layers you are actually referring to, you are just creating the pipelines for your analysis.


<img src="../../../../docs/assets/images/adv5-7.png" width="800">

&nbsp; 

#### 3.2.3 Clip the raster to London extent

Next, click on the Algorithms section and search for "Clip raster by extent". Drag that on your modeling area, to the right of your two input layers. A pop-up window opens (make it bigger by pinching the corners of that pop up window). 

- Set your Input layer to a Model Input (click on the `123` icon to change the type of input), and pick your `Great Britain Pop Denisty Raster Grid`.
- Do the same with your Mask layer: set it as Model input `London LSOA`. 
- Give your output a name: `London_Children_Under_Five_Pop_Density`
- You can ignore the dependencies section for this one (_more on this in the next sections_).


<img src="../../../../docs/assets/images/adv5-8.png" width="800">

&nbsp; 

Once you've pressed OK, a new box for your algorithm appears, along with a green Output box (your clipped raster layer).

<img src="../../../../docs/assets/images/adv5-9.png" width="800">

&nbsp; 

#### 3.2.4 Try running your clipping workflow

You now have a simple workflow that takes two inputs and returns one output. Let's try to run that: press the green arrow (or F5 on your keyboard). A new pop up windows appears, with three parameters for you to fill: what layer should you use as your `Great Britain Pop Denisty Raster Grid`, and which one as your `London LSOA`, and do you want to save your output on your computer? (for now just save as temporary file / scratch layer)

<img src="../../../../docs/assets/images/adv5-10.png" width="800">

&nbsp; 

You can see that your model ran successfully and produce the outpur layer you wanted, clipped to a bounding box that represents the extent of London boundaries (a raster grid that ranges from the minimum to the maximum x and y values in the London LSOA layer). You can remove that layer and go back to your Graphical Modeler.

<img src="../../../../docs/assets/images/adv5-11.png" width="800">

&nbsp; 


### 3.3 Create Input layers for the remaining parameters in your pocket parks suitability analysis

We need to make sure the remaining parameters in our pocket parks suitability analysis are loaded into our model. Click the `Inputs` tab and add three new `Vector layer` inputs for:

- Brownfields (polygons - mandatory)
- Greenspace Access Points (points - mandatory)
- Conservation Areas (polygons - mandatory)

<img src="../../../../docs/assets/images/adv5-12.png" width="800">

&nbsp; 

Save your changes. Your inputs are now ready to be pre-processed to become usable as selection criteria.

<img src="../../../../docs/assets/images/adv5-13.png" width="800">

&nbsp; 



## IV. Data pre-processing

We are using a raster approach in this analysis so we first need to turn all of our layers into raster scores.

### 4.1 Brownfields 

The first layer we want to reclassify is the brownfields. Basically if the site is not a brownfield we will not consider it as a possible option so we will assign those areas a value of 0. Brownfield areas will be assigned a value of 1. But because our layer is a vector polygon layer, we first need to rasterize it.


The [help](https://docs.qgis.org/3.16/en/docs/user_manual/processing_algs/gdal/vectorconversion.html#gdalrasterize) page gives you more information about each parameters.


### 4.2 Conservation Areas reclassification

We need to 
0 or 1
### 4.3 Children under 5 reclassification

Quantiles in London
### 4.4 Greenspace Access Points

rasterize then
proximity Distance layer

### 4.5 LSOA

Refactor tool
Then score


## V. Weighted overlay

### 5.1. Assign weights

Assign weights

### 5.2. Run model

### 5.3. Notes

- overview of the workflow - to be added onto reports as a good overview of the workflow
- can export model as Python script
- can change input layers easily as long as they're of the same type

<img src="../../../../docs/assets/images/adv5-.png" width="800">

&nbsp; 

<img src="../../../../docs/assets/images/adv5-.png" width="800">

&nbsp; 

<img src="../../../../docs/assets/images/adv5-.png" width="800">

&nbsp; 

<img src="../../../../docs/assets/images/adv5-.png" width="800">

&nbsp; 

<img src="../../../../docs/assets/images/adv5-.png" width="800">

&nbsp; 



&nbsp; 

### **[Next Tutorial >](../advanced-tutorial6/)**

### **[Back to the syllabus >](../../../..//tuto2-advanced-gis/)**