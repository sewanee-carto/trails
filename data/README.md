# Trail Data

This directory contains the trail geodata provided by the Landscape Analysis Lab.

* `shapefile.zip` - trail data in original ESRI shapefile format
* `trails.geojson` - trail data in geojson format
* `trails.kmz` - trail data in kmz format


## Conversion process

ogr2ogr -f GeoJSON -t_srs crs:84 trails.geojson shapefile/trails.shp

curl -X POST -F targetSrs=CRS:84 -F upload=@shapefile.zip
http://ogre.adc4gis.com/convert >| trails-2.geojson
