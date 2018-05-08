# Basemaps_QTiles
Creating basemaps from Natural Earth Data with QTiles in QGIS

About the project: 

This project is part of an internship assignment which aimed at creating tiled basemaps for the KNMI geospatial infrastructure. The data and tools used to create the basemaps are open-source. Therefore, this project and the basemaps are reproducible for everyone who wants to create simple basemaps (raster tiled basemaps) from free vector data! 

Several basemap styles were created in this project:

![alt text](https://github.com/ingmapping/Basemaps_QTiles/blob/master/WorldMaps_demo.gif)

1) WorldMap 
2) WorldMap_Light
3) WorldMap_Canvas
4) WorldMap_GreyCanvas
5) WorldMap_LightGreyCanvas

About Natural Earth:

Natural Earth is a public domain map dataset available at 1:10m, 1:50m, and 1:110 million scales. Featuring tightly integrated vector and raster data, with Natural Earth it is possible to make a variety of visually pleasing, well-crafted maps with cartography or GIS software. In this project, vector datasets were downloaded for styling in a QGIS project before finally generating raster tiles with the QTiles plugin.

Natural Earth Data can be downloaded from the official website: http://www.naturalearthdata.com/downloads/ 

About QTiles plugin in QGIS:

The QTiles plugin generates raster tiles from QGIS project for selected zoom levels and tile naming convention (Slippy Map or TMS). It can package tiles for variety of formats and applications. For instance, it can export tiles in a directory structure or in a MBTiles file.  Currently there is no release of QTiles plugin for QGIS 3.0. It was designed for QGIS version 1.9.0 and higher. In this project QGIS 2.18.16 was used on Linux Fedora 26. 

The plugin is available via official repository: 
https://plugins.qgis.org/plugins/qtiles/ 

For developers there is also a Github repository:
https://github.com/nextgis/QTiles

## Basemap 1: WorldMap basemap 

### Shapefiles used: 

* 50m Physical, Rivers + lake centerlines: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_rivers_lake_centerlines.zip  (389.27 KB)

* 10m Physical, Coastline (includes major islands):http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_coastline.zip
(2.93 MB) 

* 10m Physical, Lakes:http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_lakes.zip (1.74 MB)

* 10m  Physical, Glaciated areas (includes glaciers and recently de-glaciated areas): http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_glaciated_areas.zip (1.57 MB)

* 50m Physical, Glaciated areas (includes glaciers and recently de-glaciated areas): http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_glaciated_areas.zip (211.39 KB)

* 50m Physical, Land: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_land.zip (446.45 KB)

* 10m Physical, Bathymetry 5000m: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_F_5000.zip (2.72 MB) 

* 10m Physical, Bathymetry 4000m: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_G_4000.zip (3.43 MB)

* 10m Physical, Bathymetry 1000m: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_J_1000.zip (741.08 KB)

* 10m Physical, Bathymetry 200m: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_K_200.zip (1.14 MB) 

* 10m Physical, Bathymetry 0m: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_L_0.zip  (2.86 MB) 

* 10m Physical, Ocean: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_ocean.zip (3.48 MB) 

* 50m Physical, Ocean: http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_ocean.zip (450.91 KB) 

## Tutorial Basemap 1: WorldMap basemap

### Step 1: Download Natural Earth data 

Download the shapefiles (in .zip format) from the website of Natural Earth: http://www.naturalearthdata.com/downloads/. Create a folder “WorldMap” and a subfolder “Data”. Import the downloaded .zip files into the “Data” subfolder. Afterwards, unzip all the .zip files. 

```
mkdir -p WorldMap/Data
cd WorldMap/Data
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_rivers_lake_centerlines.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_coastline.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_lakes.zip 
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_glaciated_areas.zip 
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_glaciated_areas.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_land.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_F_5000.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_G_4000.zip 
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_J_1000.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_K_200.zip
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_bathymetry_L_0.zip 
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/physical/ne_10m_ocean.zip 
wget http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/physical/ne_50m_ocean.zip 
unzip ne_50m_rivers_lake_centerlines.zip 
unzip ne_10m_coastline.zip
unzip ne_10m_lakes.zip 
unzip ne_10m_glaciated_areas.zip 
unzip ne_50m_glaciated_areas.zip 
unzip ne_50m_land.zip 
unzip ne_10m_bathymetry_F_5000.zip
unzip ne_10m_bathymetry_G_4000.zip
unzip ne_10m_bathymetry_J_1000.zip
unzip ne_10m_bathymetry_K_200.zip
unzip ne_10m_bathymetry_L_0.zip 
unzip ne_10m_ocean.zip 
unzip ne_50m_ocean.zip 
```

### Step 2: Create a QGIS project 

Run QGIS Desktop and create a new project (CTRL+N). Save the project as WorldMap.qgs in the WorldMap folder created earlier. 

### Step 3: Add Layers in the QGIS project

Add all shapefiles to the QGIS project: Layer → Add Layer → Add Vector Layer (CTRL+SHIFT+V). Choose the shapefiles in the “Data” subfolder. 

### Step 4: Put the Layers in the correct order

Place the layers in the correct order. From top to buttom:
- ne_50m_rivers_lake_centerlines
- ne_10m_coastline
- ne_ 10m_lakes
- ne_10m_glaciated_areas
- ne_50m_glaciated_areas
- ne_50m_land
- ne_10_bathymetry_F_5000
- ne_10_bathymetry_G_4000
- ne_10_bathymetry_J_1000
- ne_10_bathymetry_K_200
- ne_10_bathymetry_L_0
- ne_10m_ocean4
- ne_50m_ocean

### Step 5: Apply styles

Apply styling. Properties –> Style.  Right click on the layer and select properties, or simply double click on the layer. 
- ne_50m_rivers_lake_centerlines: Simple Line, Solid, Width: 0.260000 millimeter,  Color: #000000, Transparency 90%.
- ne_10m_coastline: Simple Line, Solid, Width: 0.260000 millimeter, Color: #b8b8b8, Transparency 50%.
- ne_ 10m_lakes: Simple Fill, Color: #59a0ce. Set outline to transparent. 
- ne_10m_glaciated_areas: Simple Fill, Color: #ffffff. Set outline to transparent. 
- ne_50m_glaciated_areas: Simple Fill, Color: #ffffff. Set outline to transparent. 
- ne_50m_land : Simple Fill, Color: #329b3f. Outline: Solid line, Color: #b8b8b8, Width: 0.260000 millimeter. 
- ne_10_bathymetry_F_5000: Simple Fill, Color: #386f9, Transparency 40%. Set outline to transparent. 
- ne_10_bathymetry_G_4000:  Simple Fill, Color: #427fb8. Set outline to transparent. 
- ne_10_bathymetry_J_1000: Simple Fill, Color: #4988be. Set outline to transparent.
- ne_10_bathymetry_K_200:  Simple Fill, Color: #5096c9. Set outline to transparent. 
- ne_10_bathymetry_L_0: Simple Fill, Color: #59a0ce. Set outline to transparent. 
- ne_10m_ocean: Simple Fill, Color: #59a0ce. Set outline to transparent. 
- ne_50m_ocean: Simple Fill, Color: #59a0ce. Set outline to transparent. 

### Step 6: Generate raster tiles with QTiles plugin

Open the QTiles plugin: Plugins →  QTiles (CTRL+T). 

Output: Select Directory to export the raster tiles as a directory structure. 

Extent: Set desired geographic extent of the map: 
	Canvas extent — current canvas extent will be used. 
	Full extent — full extent of all project layers will be used 
	Layer extent — output extent will be the same as extent of the selected layer 
We will select Full extent to take into account all project layers for the generation of the tiles.

Zoom: Set the zoom levels. The more zoomlevels, the more detail on the deeper zoom levels, however more tiles needed which will slow the process and which takes more size. In this case, a maximum zoom of 6 will do (5461 tiles, approximately: 54 MB). A zoom level of 9 will give a better user experience, however the total size of the tiles is approximately 1 GB. 

More about zoomlevels: https://wiki.openstreetmap.org/wiki/Zoom_levels 

Parameters: Set the tile size. 256X256 pixels is used for slippy maps. Choose the format: PNG. Select other wished options. Recommended is to write Leaflet-based viewer to check the result once the tiles are created. 

More about slippy maps: https://en.wikipedia.org/wiki/Tiled_web_map/ 

Press Run to start the tile generation. Once the process is completed, open the leaflet-based viewer QTiles.html in the browser to check if the tiles are rendered correctly.

## To be continued
