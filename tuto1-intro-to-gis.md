---
layout: page
title: Tutorials - Intro to GIS
---

&nbsp;

**Sciences Po Urban School**

* GETEC Masters - Fall Semester 2020
* GETEC Masters - Fall Semester 2021
* GLM Masters - Spring Semester 2022
* GETEC Masters - Fall Semester 2022



This course is open sourced under an MIT license. I hope you enjoy learning GIS and exploring the QGIS software! You are also more than welcome to use this material for teaching; however if you do so, please make sure to credit my work :)

&nbsp; 
## Overview

It is estimated that 80-90% of all data contain some spatial component (Carl & Hane, 1992). Geographic Information Systems (GIS) are an essential tool to manipulate this data, draw insights and produce visualisations to inform decision-making. This Introduction course aims to familiarise students with the field of Geographic Information Science and with carrying out geospatial analysis using the open-source software QGIS. At the end of the cours, students will be able to source data from open data providers, understand commonly used spatial data structures, and develop start-to-end GIS workflows.

&nbsp; 

## Format

6 sessions of 2 hours. The first session will be a lecture covering GIS as a field of research, typical workflows, data sources and collection methods. Subsequent sessions will follow a more interactive format centred around tutorials and flipped classroom methods.

&nbsp; 
## Coursework

Working in groups of 2 or 3, students will be provided a dataset to explore and will be tasked with carrying out simple geospatial analysis and visualisation. They will produce a technical report detailing the methodology they adopted and the insights they can draw from this data.


&nbsp; 
## Sessions


### [Session 1: What is GIS?](_posts/2021-11-16-intro-tutorial1.md)


*[Class Content:](docs/assets/pdf/intro-session1-getec2022.pdf)*

- *Course overview and objectives*
- *GIS as a field of research and a tool*
- *Why is spatial special?*
- *Issues with 2D representations of the Earth surface: Coordinate Reference Systems and Projections*
- *Common use cases*
- *GIS and geospatial data science workflows*

*Tutorial:*

- *Installing QGIS*
- *Exploring the QGIS console*

&nbsp; 

### [Session 2: Sourcing and loading data into GIS](_posts/2021-11-16-intro-tutorial2.md)

*[Class Content:](docs/assets/pdf/intro-session2-getec2022.pdf)*
- *Navigating data types (vector and raster) and common data formats (.shp, .geojson, .csv, PostGIS, etc)*
- *Where to source data and what to look for (metadata, etc)*
- *Exploring the data structure of typical spatial formats using GeoDa*

*Tutorial:*

- *Downloading data from an open data portal*
- *Setting up a QGIS project*
- *Loading data into QGIS*
- *Saving vector data to a different format*


&nbsp; 

### [Session 3: Working with vector data: the attribute table](_posts/2021-11-16-intro-tutorial3.md)

*[Class Content:](docs/assets/pdf/intro-session3-getec2022.pdf)*

- *Understanding the attribute table*
- *Querying data based on spatial qualities or their attributes*
- *Joining layers: why and how?*

*Tutorial:*

- *Loading basemaps*
- *Accessing summary statistics about a field*
- *Understanding the attribute table*
- *Exploring how features and records are related*
- *Creating a point layer from a CSV file*
- *Creating a table join*
- *Creating a query to select features by attribute*
- *Using queries to only display a subset of your layer's features*

&nbsp; 

### [Session 4: Cartographic design](_posts/2021-11-16-intro-tutorial4.md)

*[Class Content:](docs/assets/pdf/intro-session4-getec2022.pdf)*

- *Kepler.gl tutorial: quick off-the-shelf data visualisation*
- *Styling a map: basemap choice, preferred symbologies, class breaks definition, scale*
- *Exporting a map: setting up a layout and adding map elements (north arrow, scale bar, legend, title etc.)* 

*Tutorial:*

- *Loading data from Open Street Map*
- *Accessing vector symbology settings*
- *Creating rule-based symbology*
- *Adding and styling labels*
- *Setting scale-dependent visibility*
- *Saving spatial bookmarks*
 

&nbsp; 

### [Session 5: Working with vector data: geoprocessing](_posts/2021-11-16-intro-tutorial5.md)

*[Class Content:](docs/assets/pdf/intro-session5-getec2022.pdf)*

- *What are geoprocessing tools?*
- *Crossing multiple layers: common geoprocessing tools*
- *Use cases; why may you need to buffer, clip, intersect*

*Tutorial:*

- *Building a choropleth*
- *Defining relevant class breaks*
- *Running simple geoprocessing tools*
- *Adding map layout elements (legend, title, etc.) using the Print Layout Composer*
- *Exporting a map as an image, PDF or SVG vector*


&nbsp; 

### [Session 6: course wrap-up](_posts/2021-11-16-intro-tutorial6.md)

*This final session is designed as a Q&A session. Students should have designed a methodology for the final coursework and are encouraged to prepare specific questions. Students will be able to select topics to be revisited in class, or to hear about more advanced GIS techniques if they wish.*

*Tutorial:*

- *Carrying out a full visualisation exercise of exposure to flood risk in London*

&nbsp; 

&nbsp; 


## Resources

- Longley, P.A., Goodchild, M.F., Maguire, D.J. and Rhind, D.W., 2005. Geographic information systems and science. John Wiley & Sons.
- QGIS training guide: https://docs.qgis.org/3.10/en/docs/gentle_gis_introduction/
- Robin Wilson’s data sources listing: https://freegisdata.rtwilson.com/
