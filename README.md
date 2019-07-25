# OGC-API-Map-Tiles

This GitHub repository contains the new revision of the [OGC](http://opengeospatial.org)'s Web Map Service and Web Map Tile Service standards for requesting maps and tiles of geospatial information on the web. It is a complete rewrite of previous versions, focusing on a simple RESTful core specified as reusable [OpenAPI](http://openapis.org) components.

This work encompasses two standards that will be developed simultaneously. In the end, must people believe at least 2 standards will emerge or even more when the core and extension model is applied. I'm not so sure.

## Standards
After a while getting familiar ad playing with the OpenAPI definition files (explained just below in the "Exemples section"), we have finally started to write the standard. We have decided an aggressive path to modularization having 2 cores, one for tiles and another for maps that can be combined as needed. Several extension for tiles and maps will emerge in the process.

### Tiles
#### Core
For the moment we have focus out efforts on defining the "tile core" that you can find [here](standard/clause_7_tile_core.adoc).

The core is:
* Only one collection
* Only support for WebMercatorQuad
* No TileMatrixSet definition
* No TileMatrixSet Link
* No featureInfo
* Can only retrieve one tile at a time
* Has no information about updates

#### Extensions
We foresee the following extensions (some of them can end into OGC standards and some might not)
* Other TileMatrixSets  (started in: standard/clause_7_tile_tms.adoc)
* Info (featureInfo) (started in: standard/clause_7_tile_info.adoc)
* Collections (more than one) (started in: standard/clause_7_tile_collections.adoc)
* Collections-info (with feautureInfo) (pending)
* Multi-tile (retrieve a ZIP with many tiles) (pending, necessary for the update workflow)
* Delta-updates (using checkpoints) (pending, necessary for the update workflow)

### Maps
#### Core
The definition of the maps core is the immediate next step that will be done [here](standard/clause_8_map_core.adoc).

The maps core would be something that allows to create a map that cannot be necessarily retrievable (yet). The reason: We need to support /maps/{styleID}/tiles/…
* It has no resolution
** No parameters related with width, height, bbox, crs… etc.
* Actually, it is map that can only be retrieved by extending it to (one of):
** a tile
** a map+resolution
* It will not have styles (because this forces a dependency to the styles API that I would like to avoid): {styleID}=“default”.

#### Extensions
We foresee the following extensions (some of them can end into OGC standards and some might not).
None of them has been started yet.

* StyleIds (Pending. In collaboration with the styles API. The only one necessary for the delta updates use cases)
* Map+resolution
* Info
* Collections (more than one)
* Collections-info
* Maps with styles on the fly (involving collections)

## Examples
Until mid July 2019, the work was focused on providing OpenAPI services description examples and domains (libraries). Now we believe this work is finalized, but each time that we take a look we still find gaps, mistakes and things that can be improved.
We expect that during the effort of extracting the knowledge accumulated (hopefully) in these files to create the standard, we will keep fixing, perfecting and evolving things.

IMPORTANT NOTE: We are now using the Swagger HUB again and should be considered the "gold copy". The Swagger account is:
* [Domain documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=DOMAIN)
* [API example documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=API)

The material in the [standards folder](standard/openapi) takes precedence to the text of the standard and the Swagger HUB takes precedence to the material in GitHub. The [standards folder](standard/openapi) examples are intended to be identical to the Swagger HUB ones except for the path names. To go from  Swagger HUB to gitHub do the following substitutions:
* Replace "https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-" by "https://raw.githubusercontent.com/opengeospatial/OGC-API-Map-Tiles/master/standard/openapi/ogc-api-"
* Replace "/1.0.0#/" by ".yaml#/"

The files in the [standards folder](standard/openapi) are structured in several parts that can be combined together.

![Diagram of the examples and domains](standard/images/diagram-xmp.png)

A [OGC API maps and tiles OPF FULL example in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-full/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles-opf-xmp-full.yaml) that contains full example of server with some features and coverages that are served as maps and/or tiles.

The later is normally it is too long to be analyzed. The following are more easy to understand.

Examples:
* A [OGC API OPF example for vector tiles in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve only tiled features (vector tiles) of one or more collections.
* A [OGC API OPF example for tiled map in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles-opf-xmp-mt-more-1-collection.yaml) that describes a service that can serve only map (raster) tiles of one or more collections.
* A [OGC API OPF example for maps in Swagger](standard/openapi/ogc-api-maps-opf-xmp-ore-1-collection.yaml) that describes a service that can serve only maps of one or more collections.
* A [OGC API OPF example for tiled coverages in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve tiled coverages of one or more collections. This example was not initially needed by the sponsors but is motivated by the elevation map in a GeoPackage example.

Libraries:
* A [OGC API common DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-common/1.0.0) or in [GitHub](standard/openapi/ogc-api-common.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API common standard additional material.
* A [OGC API maps DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-maps/1.0.0) or in [GitHub](standard/openapi/ogc-api-maps.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API maps standard additional material.
* A [OGC API maps and tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It will be included by OGC API maps standard and tiles standard.
* A [OGC API tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API tiles standard additional material.

## Overview

IMPORTANT NOTE: The description in this README.md can be older than the one in the [standard](standard) draft. In case of discrepancy the standard draft takes precedence.

### Maps

A "OGC API - Maps" is a standard API that provides maps representing geospatial data.

```
GET /.../.../map/{styleId}
```

The identifier of the "layer" is replaced by "{collectionId}" or "coverage"...

Maps can be requested in any available CRS and can be subset by bbox width and height (and eventually other parameters such as time and elevation)
```
GET /.../.../map/{styleId}?crs=CRS84&bbox=160.6,-55.95,-170,-25.89&width=600&height=400
```
Returns a map - a representation of real-world elements at a given resolution. {styleId} is optional.


### Tiles

A "OGC API - Tiles" is a standard API that provides tiles of maps representing geospatial data.

```
GET /.../.../tile/{styleId}/{tileMatrixSetId}/{tileMatrixId}/{tileRow}/{tileCol}
```

Returns a tile - a representation of real-world elements at a given resolution restricted by the selected Tile Matrix Set. {styleId} is optional.

The identifier of the "layer" is replaced by "{collectionId}" or "coverage"...

Tiles are available at some TileMatrixSetId and styles that need to be enumerated in:
```
GET /.../.../tiles
```

There is a need for describing the TileMatrixSet available
```
GET /tileMatrixSet/{tileMatrixSetId}
```

## Using the standard

Those who want to just see the endpoints and responses can explore generic
OpenAPI definitions in this folder (please paste one of them in the Swagger Editor):

* OGC-API-Map-Tiles/standard/openapi/

## Communication

Join the WMS mailing list

Most all work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/OGC-API-Map-Tiles/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership (and eventually the ISO/TC 211), shall be incorporated into OGC and ISO/TC 211 Web Map Service and Web Map Tile Service standards documents and that all copyright and intellectual property shall be vested to the OGC.

The WMS Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/OGC-API-Map-Tiles/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/OGC-API-Map-Tiles/master/LICENSE)
