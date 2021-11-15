# QGIS workshop for SAGES (Geneva)

Workshop tutorial created by Keith Jenkins kgj2@cornell.edu, Mann Library, Cornell University (revised 2021-11-15)

- <https://cornell-gis.github.io/qgis-workshop-sages/>

This workshop will cover basic tasks using QGIS: loading data, changing the styles used to display the data on a map, installing plugins, using processing tools to do basic analysis, and exporting a finished map image.

**Download and unzip** the data for this workshop:
- <https://github.com/cornell-gis/qgis-workshop-sages/archive/main.zip>
- When the download is complete, open your downloads folder
- Right-click the .zip file > Extract All...


## Introductions

- Keith Jenkins, GIS Librarian at Mann Library
- QGIS, free open source software
- Data formats
  - Geopackage
  - Shapefile
  - CSV (from Excel, etc.)
- CRS/projections
- Mapping scenario
  - July 2022, a never-before-seen insect attacks the Homer C. Thompson
    Vegetable Research Farm in Freeville
  - Note that this data is fictional!


## CSV with coordinate data

- Data Source Manager > Delimited text
  - Select the observations.csv file, check options
- Zoom to layer, CTRL-zoom-wheel for fine adjustment
- Basic style (point size, color)
- Inspect data (Identify Features, Attribute Table)
- Categorized (by variant)


## Basemaps

- Install QuickMapServices plugin
  - Plugins menu > Manage and install plugins
  - Search for "quickmap" and install
- Add more basemap definitions
  - Web menu > QuickMapServices > Settings > More Services > Get contributed pack
- Web menu > QuickMapServices > Google Hybrid
- Notice how the map looks stretched out left-to-right
- Change Project CRS to EPSG:3857 (to match basemap)
- Zoom to 100%
- Change opacity of basemap


## Add polygons (fields)

- Add data by dragging the fields.shp file onto QGIS
- Reorder layers as necessary (points on top)
- Style polygons - simple fill
- Fill style = No Brush
- Stroke width = 1.0 millimeter
- Labels tab
- Single labels, value = crop
- Font size, buffer 1.0 white (opacity)


## Analysis

- Processing menu > Toolbox
- Lots of tools!
- Count points in polygon
  - Polygons = freeville-fields
  - Points = observations
  - leave weight and class blank
  - Create temporary layer
- Explore results via Identify features / Attribute table
  - What crops tended to have more pests?
  - Graduated style (by NUMPOINTS)
  - Label map with crop names + pest counts, using expression editor
    "crop" || '\n' || "NUMPOINTS"
- Right-click layer name > Make permanent
  - save as geopackage fieldcounts.gpkg in data directory


## Exporting your map to an image or PDF

- Project menu > Import/Export > Export Map to Image (or PDF)
- Update the extent or leave as is
- To preserve the quality for large posters, etc. you can increase the resolution

It is also possible to create a more detailed map layout, with things like a title, text boxes, a north star, and legend. We won't go into the details here, but the general process is:

- Project menu > New Print Layout
- Choose a title for the layout (optional)
- Add Item menu > Add Map, then drag a rectangle on the page
- Edit menu > Move Content (or press C) to pan/zoom the content within the page
- Add legend, scale bar, etc. (from the Add Item menu)
- Layout menu > Export as PDF


## Analysis by date

- Processing Toolbox > Statistics by categories
  - Input vector layer = observations
  - leave "field to calculate statistics on" blank (we just want counts)
  - Field with categories = date
  - Create temporary layer
- Explore results via attribute tables
- Right-click layer name > Make permanent
  - save as CSV


## Time-based animations

- Right-click observations layer > Properties > Temporal
- Enable Dynamic Temporal Control
  - Configuration = Single Field with Date/Time
  - Field = date
  - Event duration = 1 day
- View menu > Panels > Temporal Controller Panel
  - Click 3rd icon (Animated temporal navigation)
  - Click the "refresh" button (circling arrows) to set time to full range of data
  - Step = 1 day
  - Speed can be adjusted 2 ways
    - Change the step
    - Or click the yellow gear icon at top right to set frames per second
- Frame images can be bulk exported to a folder, and can be turned into a video
 with other software (such as free ScreenToGif for Windows)
- Warning -- turn off the temporal controller whenever you are not actively
  using it!


## Other resources
- [QGIS project website](http://qgis.org/)
- [QGIS training manual](https://docs.qgis.org/latest/en/docs/training_manual/)
- [QGIS Map Showcase](https://www.flickr.com/groups/qgis/pool/) (for inspiration)
- [QGIS Tutorials and Tips](http://www.qgistutorials.com/en/) by Ujaval Gandhi
- [Cornell GIS LibGuide](https://guides.library.cornell.edu/gis) (appointments, etc.)
