# Trail data in OpenTrails format

This directory contains trail data provided by the Landscape Analysis Lab in [OpenTrails](http://www.opentraildata.org) format.

The files were converted from the the original [shapefile archive](https://en.wikipedia.org/wiki/Shapefile) provided by the LAL.

* `areas.geojson` - boundaries of land designated for minimal development
  through which trails pass

* [`named_trails.csv`](named_trails.csv) - collections of trail segments that describe cohesive lengths of identifiable trails 

* [`stewards.csv`](stewards.csv) - organizations involved in Sewanee trail management

* [`trail_segments.geojson`](trail_segments.geojson) - paths with consistent physical characteristics and appropriate uses that can connect to other segments to form a trail

* `trailheads.geojson` - points of transition or access between trail and
  non-trail paths

See the [OpenTrails Cheat Sheet](http://www.outerspatial.com/opentrails/cheat) for examples of each file.  It shows the format and provides sample content for each file, giving us a model of what our files should ultimately look like.


## Conversion process

We used the OpenTrails [online converter](http://open-trails.codeforamerica.org) to convert the original shapefile archive into the files listed above.

Note that we used the original shapefile archive as provided.  We should
probably review and work through the data prep steps described below and then try re-converting for better results.


## Data preparation steps

It may be beneficial to review the OpenTrails [Guidebook](https://docs.google.com/document/d/1tZQRaHh76dP-t2_KhMR9zT2DktuOGwRjCAfvHU9_Tpg/edit) and follow the step-by-step guide to preparing shapefile data for conversion (see page 4). The steps covered are as follows:

* [x] create shapefiles
* [ ] update fieldnames in your trail segment shapefile
* [ ] update fieldnames in your trailhead shapefile
* [ ] associate trailheads with trail segments

As noted above, the [OpenTrails Cheat Sheet](http://www.outerspatial.com/opentrails/cheat) provides examples of each the five files we'd ultimately like to end up with.  It nicely presents the format and sample contents for each file.
