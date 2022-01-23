---
layout: post
title: Session 2 - What is GIS?
---


**Advanced GIS  ·  Sciences Po Urban School**

Lecturer: Raphaëlle Roffo

&nbsp; 

## I. Session 1 Overview

**Download the [slides](../../../../docs/assets/pdf/advanced-session1-getec2022.pdf)**

- *Course overview and objectives*
- *Raster data in GIS*


&nbsp; 

## II. Tutorial

### Goals:

- Sourcing public satellite data
- Importing satellite imagery in QGIS
- Using Raster calculations to compute a vegetation index (the NDVI).

&nbsp; 

## III. The NDVI

The Normalized Difference Vegetation Index (NDVI) is a widely used index that can be computed from remote sensing data, allowing researchers to monitor vegetation health and land use remotely. Put simply, every surface on the planet absorbs and reflects certain ranges from the electromagnetic spectrum. Plants appear green to the human eye because the wavelengths that correspond to the colour green bounce off the chlorophyll pigments while the colour red is absorbed. So we know that **a healthy plant will reflect absorb red light**.

We also know that during photosynthesis, plants develop more cell structures that happen to reflect near-infrared (NIR) waves. So **when a plant is growing and healthy, it will also reflect more NIR.**

The NDVI is simply  a way of observing the relationship between the amount of red light and NIR waves captured by remote sensors such as satellites. It is calculated using this formula:

**NDVI = (NIR-Red) / (NIR+Red)**


Now, using QGIS, we are able to 

## IV. Sourcing the data

Visit [https://ers.cr.usgs.gov/login](hhttps://ers.cr.usgs.gov/login) and create a new account. Once you've successfully created an account and are logged in, go to the [Earth Explorer page](https://earthexplorer.usgs.gov). This is one of many platforms from which you can download public satellite data, for free.

We are interested in London. By default, the map is centered on Siouxville in the US, but scroll out and navigate to the UK, then zoom onto London, roughly to this extent:

![](../../../../docs/assets/images/adv-s1.png)


&nbsp; 

Click on `Use map`; when you zoom out, you'll notice it has set four pins to determine a bounding box around your previous zoom level. This determines the zone in which you will be looking for data. Click `Results` 

![](../../../../docs/assets/images/adv-s2.png)

In the bottom set of parameters, select dates 01-01-2022 to 23-01-2022. You can actually retrieve Sentinel data all the way back to November 2015 when it was first launched.

In the next tab `Cloud Cover`, set the slider to only keep images with a 0-30% cloud cover range, and exclude images with range unknown.

![](../../../../docs/assets/images/adv-s3.png)

Next, press `Data Sets`. On the new panel, select Sentinel > Sentinel-2 data then press `Results`.

![](../../../../docs/assets/images/adv-s4.png)

You can now see a series of tiles that partly or entirely cover our area of interest. By pressing the foot icon, you get an overview of the layer's footprint. By pressing the second icon (the small image), you get a preview of the actual image, directly on your canvas. You can preview several images or footprints together. Sentinel-2 breaks down the surface of the Earth into square tiles that it revisits every 2 to 10 days depending on the latitude (closer to 2-3 days in Europe). Those tiles slightly overlap to avoid gaps in the image. Notice that the London area we selected actually falls on two tiles: tile L1C_T30UXC to the West and tile L1C_T30UYC to the East. Technically, tile L1C_T30UXC contains the entire study area, but we will still go through the process of working with both tiles for this tutorial. 

![](../../../../docs/assets/images/adv-s5.png)

The pictures taken on 18/01/2022 are cloudy and hide the area we're interested in. Instead, it seems that the pictures taken on 13/01/2022 are clear and cloud-free. These are the ones we are intereested in. Click the fifth icon to download those two pictures. Select GeoTIFF format (this is a special photo format that also encodes geographic location)

![](../../../../docs/assets/images/adv-s6.png)


Note that the download is launched from a pop-up window. If nothing happens after you click `Download`, your browser might be blocking the pop-up and you should be able to allow the pop-up from your browser's address bar. Save the two files to a `Session1` folder. 

&nbsp; 

## V. Processing the data in QGIS

&nbsp; 

Open QGIS and create a shortcut to your `Session 1` folder.

### 1. 
&nbsp; 

&nbsp; 

### **[Next Tutorial >](../advanced-tutorial2/)**

### **[Back to the syllabus >](../../../..//tuto2-advanced-gis/)**