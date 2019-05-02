# OGC-API-Map-Tiles

This GitHub repository contains the new revision of the [OGC](http://opengeospatial.org)'s
Web Map Service and Web Map Tile Service standards for requesting maps and tiles of geospatial information on the web. It is a complete
rewrite of previous versions, focusing on a simple RESTful core specified
as reusable [OpenAPI](http://openapis.org) components.

## Overview

### Maps

A "OGC API - Maps" is a standard API that provides maps representing geospatial data.

```
GET /.../.../style/{styleId}
```

The identifier of the "layer" is replaced by "{collectionId}" 

Maps can be requested in any available CRS and can be subset by bbox width and height (and eventually other parameters such as time and elevation)
```
GET /.../.../style/{styleId}/{crsId}?bbox=160.6,-55.95,-170,-25.89&width=600&height=400
```
Returns a map - a representation of real-world elements at a given resolution


### Tiles

A "OGC API - Tiles" is a standard API that provides tiles of maps representing geospatial data.

```
GET /.../.../style/{styleId}/tiles/{tileMatrixSetId}/{tileMatrixId}/{tileRow}/{tileCol}
```

The identifier of the "layer" is replaced by "{collectionId}" 

Returns a tile - a representation of real-world elements at a given resolution restricted by the selected Tile Matrix Set


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
