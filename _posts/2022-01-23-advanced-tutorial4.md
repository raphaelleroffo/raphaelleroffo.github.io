---
layout: post
title: Session 4 - Cartograms
---


**Advanced GIS  ·  Sciences Po Urban School**

Lecturer: Raphaëlle Roffo

&nbsp; 

## I. Session 4 Overview

**Download the [slides](../../../../docs/assets/pdf/advanced-session4-getec2022.pdf)**

- *Bivariate choropleths - continued*
- *Coursework update*
- *Cartograms: what are they, why use them?*
- *Isochrones: use cases*

&nbsp; 

## II. Tutorial

### Goals:

- Building an isochrone map
- (Building a cartogram - pending updates from the [cartogram3](https://github.com/austromorph/cartogram3) plugin)


&nbsp; 
### Set up the project

Create an `Advanced-Session4` folder and add it to your favourites in your QGIS Browser. Set your CRS to `EPSG:3857`, add a basemap of your choice, for instance CartoDB Positron, to your map canvas. If you do not have basemaps under the `XYZ Tiles` section of your browser, refer to the [Intro to GIS Session 3 tutorial](../2021/11/16/intro-tutorial3/) to set it up. 

Zoom onto the London area, and save your project as `Advanced-Session4.qgz`.



## III. Installing the TravelTime plugin

### 3.1 Install the plugin

Go into your top menu `Plugins` > `Manage and install plugins`. In the `All` tab, search for "TravelTime" and install the plugin. 

<img src="../../../../docs/assets/images/adv4-1.png" width="800">

&nbsp; 

A new toolbar should now have appeared in your top toolbars (if not, you can activate it by going into your top menu `View` > `Toolbars` then checking the box in front of `TravelTime platform Toolbar`). The plugin is also accessible from your top menu `Plugins`.

<img src="../../../../docs/assets/images/adv4-2.png" width="800">

&nbsp; 

### 3.2 Activate your API Key

Now, click on the Configuration button. You may get a pop-up message about a master password, you can ignore that and click cancel. You should then get this window. In order for TravelTime to function properly, you need to connect to their database using their API. Click on `Get a free API Key` and you will be taken to [this page](https://docs.traveltime.com/qgis/sign-up) to register. 

<img src="../../../../docs/assets/images/adv4-3.png" width="800">

&nbsp; 


Provide your Name, mail address and indicate Sciences Po as company. Create a password for your account then verify the email that was sent to you. You can now login using yoru email address and password, and you will be taken to this page:

<img src="../../../../docs/assets/images/adv4-4.png" width="800">

&nbsp; 

Copy the application ID and paste it into that TravelTime window in QGIS, and do the same with the API Key. You can then click OK, and you are now ready to use the plugin.


## IV. Creating an isochrone

Let's use the quick time map functionality of TravelTime. Find a point of interest, for instance the British Museum, and center your canvas around that area. Now click on the small down arrow by the `Quick Time Map` icon. You can select the mode of transportation (public transport, cycling, walking or driving), a duration of travel, and a departure or arrival time.

<img src="../../../../docs/assets/images/adv4-5.png" width="800">

&nbsp; 

You can select for instance 15 minutes cycling and leave the departure time parameters unchanged. Now click on the actual icon, and your mouse cursor will turn into a black cross on your map canvas. Once you click anywhere on the canvas, an isochrone of all areas accessible within 15 minutes cycling of that point will be drawn. 

<img src="../../../../docs/assets/images/adv4-6.png" width="800">

&nbsp; 

Zoom out to get a sense of the coverage of that isochrone. Notice that this new layer is only a scratch layer; if you want to save it you need to right click that layer > `Make Permanent` and save it in a new geopackage.

<img src="../../../../docs/assets/images/adv4-7.png" width="800">

&nbsp; 

You can click on the `QuickTimeMap` icon again and click on a different point to generate a new isochrone. Try using a single starting point and different modes of transportation (you can rename the layers that are being generated, to keep track). Toggle the layers on and off to compare the outputs. Notice that with public transport, little islands tend to appear at tube/train stations that are connected to your point of departure.

<img src="../../../../docs/assets/images/adv4-8.png" width="800">

&nbsp; 





&nbsp; 

&nbsp; 

### **[Next Tutorial >](../advanced-tutorial5/)**

### **[Back to the syllabus >](../../../..//tuto2-advanced-gis/)**