# Trail data in OpenTrails format

This directory contains trail data provided by the Landscape Analysis Lab in [OpenTrails](http://www.opentraildata.org) format.

The files were converted from the the original [shapefile archive](https://en.wikipedia.org/wiki/Shapefile) provided by the LAL.

---

OpenTrails uses CSV and GeoJSON files to describe the entire park system,
including the park boundaries, trails and trailheads within the system and the
organizations that manage and serve as stewards of these public resources.

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

## Trailheads

We currently lack a `trailheads.geojson` file.  This is what a single trailhead record would look like:

```geojson
{
    "type": "Feature",
    "properties": {
        "id": "th-2",
        "name": "Lost Cove Trail",
        "steward_id": "ebrpd",
        "segment_ids": "segment-2",
        "restrooms": "No",
        "drinkwater": "No", 
        "parking": "Yes",
        "kiosk": "Yes",
        "osm_tags": "natural=tree"
    },
    "geometry": {
        "type": "Point",
        "coordinates": [
             -122.14586734771727,
             37.775803045522146 ]
    }
}
```

#### `id`

A unique identifier for the trailhead, not necessarily something for humans,
but for machines to reliably tell trailheads apart.

#### `name`

A human readable name for the trailhead, you might use this as a label on a map
or on a sign.

#### `steward_id`

Associates a trailhead with an administrative organization, which is defined in
a stewards.csv file. This is typically a parks and recreation or other public
agency.

#### `area_id`

ID of the primary land area (such as park or preserve) that the trailhead is
located within, if any.

#### `segment_ids`

Associates a trailhead with specific segments of trail Communicates the actual
accessibility of a trail from a trailhead.

This is where it get’s interesting, because the following five fields were
designed with OSM in mind. The names and values of these, as specified in the
OpenTrails standard, map directly to commonly used tags in OSM.

#### booleans

The following four are boolean properties requiring simple "yes" or "no" values:

* `restrooms` - Is there a bathroom at this trailhead?

* `drinkwater` - Is there a source of drinking water?

* `parking` - Is there vehicle parking?

* `kiosk` - Is there an information display?

#### `osm_tags`

This can be a list of any OSM tags that may be useful in describing the state
of the trailhead. This is the primary extension mechanism of the OpenTrails
standard. There exists a large subset of the OSM tags that may be applicable.
See [list of recommended OSM tags](https://docs.google.com/document/d/1KF8KAio-SqGHhh9oFY_KjfwIi3PePOHg7KfTSPh27fc/edit#bookmark=id.saceiw7dq99).
