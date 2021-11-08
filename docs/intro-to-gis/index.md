# Introduction to GIS
**Sciences Po Urban School, GETEC Masters, Fall semester 2021-2022**

**Lecturer: Raphaëlle Roffo**

### Overview
It is estimated that 80-90% of all data contain some spatial component (Carl & Hane, 1992). Geographic Information Systems (GIS) are an essential tool to manipulate this data, draw insights and produce visualisations to inform decision-making. This Introduction course aims to familiarise students with the field of Geographic Information Science and with carrying out geospatial analysis using the open-source software QGIS. At the end of the cours, students will be able to source data from open data providers, understand commonly used spatial data structures, and develop start-to-end GIS workflows.


### Format
6 sessions of 2 hours. The first session will be a lecture covering GIS as a field of research, typical workflows, data sources and collection methods. Subsequent sessions will follow a more interactive format centred around tutorials and flipped classroom methods.

### Coursework
Working in groups of 2 or 3, students will be provided a dataset to explore and will be tasked with carrying out simple geospatial analysis and visualisation. They will produce a technical report detailing the methodology they adopted and the insights they can draw from this data.

### Sessions

**Session 1: What is GIS?**

*Class Content:*

- *Course overview and objectives*
- *GIS as a field of research and a tool*
- *Why is spatial special?*
- *Issues with 2D representations of the Earth surface: Coordinate Reference Systems and Projections*
- *Common use cases*
- *GIS and geospatial data science workflows*

*Tutorial:*

- *Installing QGIS*
- *Exploring the QGIS console*


**Session 2: Sourcing and loading data into GIS**

*Class Content:*
- *Navigating data types (vector and raster) and common data formats (.shp, .geojson, .csv, PostGIS, etc)*
- *Where to source data and what to look for (metadata, etc)*
- *Exploring the data structure of typical spatial formats using GeoDa*

*Tutorial:*

- *Load data into QGIS: .shp and .csv*
- *Setting the right Coordinate Reference Systems and Projections*


**Session 3: Working with vector data: the attribute table**

*Class Content:*

- *Understanding the attribute table*
- *Querying data based on spatial qualities or their attributes*
- *Joining layers: why and how?*

*Tutorial:*
- *Run spatial and attribute-based queries*
- *Attribute table operations: generating new fields, refactoring data, geometric operations, etc.*
- *Joining layers*


**Session 4: Cartographic design**

*Class Content:*
- *Kepler.gl tutorial: quick off-the-shelf data visualisation*
- *Styling a map: basemap choice, preferred symbologies, class breaks definition, scale*
- *Exporting a map: setting up a layout and adding map elements (north arrow, scale bar, legend, title etc.) 

*Tutorial:*
- *Source and load basemaps*
- *Apply symbology of choice to vector data*
- *Export maps using layouts*


**Session 5: Working with vector data: geoprocessing**

*Class Content:*

- *Use cases; why may you need to buffer, clip, intersect?*
- *Crossing multiple layers: common geoprocessing tools*
- *Walk-through common mistakes and data errors*
- *Coursework guidelines*

*Tutorial:*
- *Learn about the main geoprocessing tools, and where to find more advanced functionalities*


**Session 6: course wrap-up**

*This final session is designed as a Q&A session. Students should have designed a methodology for the final coursework and are encouraged to prepare specific questions. Students will be able to select topics to be revisited in class, or to hear about more advanced GIS techniques if they wish.*


### Resources

- Longley, P.A., Goodchild, M.F., Maguire, D.J. and Rhind, D.W., 2005. Geographic information systems and science. John Wiley & Sons.
- QGIS training guide: https://docs.qgis.org/3.10/en/docs/gentle_gis_introduction/
- Robin Wilson’s data sources listing: https://freegisdata.rtwilson.com/
