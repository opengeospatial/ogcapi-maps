# Previous Examples

This page shows previous examples of API definition documents.

This page is not maintained and is retained for historic purposes.

## Examples

WARNING: This section needs to be updated.

Until mid July 2019, the work was focused on providing OpenAPI services description examples and domains (libraries). Now we believe this work is finalized, but each time that we take a look we still find gaps, mistakes and things that can be improved.
We expect that during the effort of extracting the knowledge accumulated (hopefully) in these files to create the standard, we will keep fixing, perfecting and evolving things.

IMPORTANT NOTE: We are now using the Swagger HUB again and the following should be considered the "gold copy". The Swagger account is:
* [Domain documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=DOMAIN)
* [API example documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=API)

The material in the [standards folder](core/standard/openapi) takes precedence to the text of the standard and the Swagger HUB takes precedence to the material in GitHub. The [standards folder](core/standard/openapi) examples are intended to be identical to the Swagger HUB ones except for the path names. To go from  Swagger HUB to GitHub do the following substitutions:
* Replace "https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-" with "https://raw.githubusercontent.com/opengeospatial/OGC-API-Maps/master/standard/openapi/ogc-api-"
* Replace "/1.0.0#/" by ".yaml#/"

The files in the [standards folder](core/standard/openapi) are structured in several parts that can be combined together.

A [OGC API maps and tiles OPF FULL example in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-full/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-map-tiles-opf-xmp-full.yaml) that contains full example of server with some features and coverages that are served as maps and/or tiles.

The latter is normally too long to be analyzed. The following are easier to understand.

Examples:
* A [OGC API OPF example for vector tiles in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve only tiled features (vector tiles) of one or more collections.
* A [OGC API OPF example for tiled map in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-map-tiles-opf-xmp-mt-more-1-collection.yaml) that describes a service that can serve only map (raster) tiles of one or more collections.
* A [OGC API OPF example for maps in Swagger](core/standard/openapi/ogc-api-maps-opf-xmp-ore-1-collection.yaml) that describes a service that can serve only maps of one or more collections.
* A [OGC API OPF example for tiled coverages in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve tiled coverages of one or more collections. This example was not initially needed by the sponsors but is motivated by the elevation map in a GeoPackage example.

Libraries:
* A [OGC API common DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-common/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-common.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API common standard additional material.
* A [OGC API maps DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-maps/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-maps.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API maps standard additional material.
* A [OGC API maps and tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-map-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It will be included by OGC API maps standard and tiles standard.
* A [OGC API tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles/1.0.0) or in [GitHub](core/standard/openapi/ogc-api-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API tiles standard additional material.
