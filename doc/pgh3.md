
# PostgreSQL H3 extension

Postgresql extension to wrap the hexagonal hierarchical geospatial indexing system of [h3 library](https://github.com/uber/h3).


## Functions

### h3_edge_length_km

Average hexagon edge length in kilometers at the given resolution.

__Synopsis:__ `h3_edge_length_km(resolution integer)`

__Returntype:__ `double precision`


### h3_edge_length_m

Average hexagon edge length in meters at the given resolution.

__Synopsis:__ `h3_edge_length_m(resolution integer)`

__Returntype:__ `double precision`


### h3_ext_version

Returns the version number of the H3 extension. This is not the version number of the h3 library itself.

__Synopsis:__ `h3_ext_version()`

__Returntype:__ `text`


### h3_geo_to_h3index

Get the H3 index for the point at the given resolution.

__Synopsis:__ `h3_geo_to_h3index(p point, resolution integer)`

__Returntype:__ `text`


### h3_geo_to_h3index

Get the H3 index for the PostGIS point geometry at the given resolution.

__Synopsis:__ `h3_geo_to_h3index(g geometry, resolution integer)`

__Returntype:__ `text`


### h3_get_basecell

Get the base cell for a H3 index.

__Synopsis:__ `h3_get_basecell(h3index text)`

__Returntype:__ `integer`


### h3_get_resolution

Get the resolution for a H3 index.

__Synopsis:__ `h3_get_resolution(h3index text)`

__Returntype:__ `integer`


### h3_h3index_is_valid

Check if a H3 index is valid.

__Synopsis:__ `h3_h3index_is_valid(h3index text)`

__Returntype:__ `boolean`


### h3_h3index_to_geo

Convert a H3 index to coordinates. Returned as a PostGIS point geometrry.

__Synopsis:__ `h3_h3index_to_geo(h3index text)`

__Returntype:__ `geometry`


### h3_h3index_to_geoboundary

Convert the boundary of H3 index to polygon coordinates. Returned as a PostGIS polygon geometrry.

__Synopsis:__ `h3_h3index_to_geoboundary(h3index text)`

__Returntype:__ `geometry`


### h3_hexagon_area_km2

Average hexagon area in square kilometers at the given resolution.

__Synopsis:__ `h3_hexagon_area_km2(resolution integer)`

__Returntype:__ `double precision`


### h3_hexagon_area_m2

Average hexagon area in square meters at the given resolution.

__Synopsis:__ `h3_hexagon_area_m2(resolution integer)`

__Returntype:__ `double precision`


### h3_polyfill

Fills the given PostGIS polygon or multipolygon with hexagons at the given resolution. Holes in the polygon will be omitted.

__Synopsis:__ `h3_polyfill(geom geometry, resolution integer)`

__Returntype:__ `SETOF text`


### h3_polyfill_estimate

Estimate the number of indexes required to fill the given PostGIS polygon or multipolygon with hexagons at the given resolution. Holes in the polygon will be omitted.

__Synopsis:__ `h3_polyfill_estimate(geom geometry, resolution integer)`

__Returntype:__ `integer`


### h3_polyfill_polygon

Fills the given PostGIS polygon with hexagons at the given resolution. Holes in the polygon will be omitted.

__Synopsis:__ `h3_polyfill_polygon(polygong geometry, resolution integer)`

__Returntype:__ `SETOF text`


### h3_polyfill_polygon_estimate

Estimate the number of indexes required to fill the given PostGIS polygon with hexagons at the given resolution. Holes in the polygon will be omitted.

__Synopsis:__ `h3_polyfill_polygon_estimate(polygong geometry, resolution integer)`

__Returntype:__ `integer`


### h3_to_children

Returns the children (finer) indeesx contained the given index.

__Synopsis:__ `h3_to_children(h3index text, resolution integer)`

__Returntype:__ `SETOF text`


### h3_to_parent

Returns the parent (coarser) index containing the given index.

__Synopsis:__ `h3_to_parent(h3index text, resolution integer)`

__Returntype:__ `text`



## Internal functions

These are mostly function for which a more comfortable wrapper function exists.

### _h3_h3index_to_geo

Convert a H3 index to coordinates. Returned as a postgresql point type.

__Synopsis:__ `_h3_h3index_to_geo(h3index text)`

__Returntype:__ `point`


### _h3_h3index_to_geoboundary

Convert the boundary of H3 index to polygon coordinates. Returned as a postgresql native polygon type.

__Synopsis:__ `_h3_h3index_to_geoboundary(h3index text)`

__Returntype:__ `polygon`


### _h3_polyfill_polygon

Fills the given exterior ring with hexagons at the given resolution. The interior_ring polygons are understood as holes and will be omitted.

__Synopsis:__ `_h3_polyfill_polygon(exterior_ring polygon, interior_rings polygon[], resolution integer)`

__Returntype:__ `SETOF text`


### _h3_polyfill_polygon_estimate

Estimate the number of indexes required to fill the given exterior ring with hexagons at the given resolution. The interior_ring polygons are understood as holes and will be omitted.

__Synopsis:__ `_h3_polyfill_polygon_estimate(exterior_ring polygon, interior_rings polygon[], resolution integer)`

__Returntype:__ `integer`

