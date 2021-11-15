# QGIS workshop for SAGES (Geneva) 2021-11-15

Download the data for this workshop:
- https://github.com/kgjenkins/qgis-workshop-sages/archive/main.zip

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
  - Categorized style
  - Label map with crop names + pest counts, using expression editor
    "crop" || '\n' || "NUMPOINTS"
- Right-click layer name > Make permanent
  - save as geopackage fieldcounts.gpkg in data directory
- Project menu > Import/Export > Export Map to Image

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

