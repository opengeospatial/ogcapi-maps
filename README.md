# OGC API - Maps

This GitHub repository contains the draft OGC API - Maps specification that defines a Web API for requesting map images over the Internet. OGC API - Maps makes it easy for a client to request images, changing parameters such as size and coordinate reference systems at the time of request. A server that implements OGC API - Maps provides information about what maps it offers, as well as producing a map and answering queries about the content of the maps. OGC API - Maps is expected to address use cases similar to those addressed by the Web Map Service (WMS) standard.

## Standards
After a while getting familiar and playing with the OpenAPI definition files (explained just below in the "Examples section"), we have finally started to write the standard. We have decided on an aggressive path towards a modular specification with a simple core and multiple extensions. The extensions are yet to be determined.

The standard is written using asciidoc using many files that might be difficult to trace. Please see the standard document as a single HTML page that is EASY TO READ here: https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Maps/blob/master/core/standard/OAPI_Maps.html

We received several recommendations to separate the specifications into a core and extensions. In March 2020, we decided to restructure the GitHub repository to separate the core and the extensions into different documents that might be elaborated at different speeds.

At this moment in time we are working on doing this separation by moving files around.

### OGC API - Maps - Part 1: Core
The definition of OGC API - Maps - Part 1: Core is the immediate next step. The Standards Working Group (SWG) [agreed](https://github.com/opengeospatial/OGC-API-Maps/issues/32) on the structure shown below.

1. Map resource: It specifies a map resource, which is a resource that contains information on how to formulate a request to a map. This document includes the CRSs and styles supported and other metadata (including attribution). It also specifies how to apply a style to a map resources to get a styled map.

2. BBoxSubset: It specifies how to include a query parameter to subset a styled map using a BBOX, WIDTH, HEIGHT etc as a query parameters. This is a partition that could be input for OGC API Common. Some considerations include OGC API - Features BBOX, representation of Time instances, and Clip versus Intersect.

3. DatasetMap - OGC API Common - Part 1 (dataset, /map resource at the root): Defines how to get a map resource from the dataset (or datasets) represented by the services. it will tell the path to get a map resources.

4. GeoDataResourceSelection - together with 3, collections= query parameters: This is identical to the GeoDataResourceSelection conformance class of OGC API - Common and if done adequately, the conformance class could be shared with OGC API - Tiles (or the other way around).

5. GeoDataResourceMap - OGC API Common - Part 2 / OGC Feature - Part 1 (collection connection, /maps resource after {collectionID}): It will define how to specify the a link to a map resource containing a representation of this geospatial data resource (path).


### Extensions
We foresee the following extensions (some of them may eventually become OGC standards and others might not).
None of them has been started yet.

* StyleIds (Pending. In collaboration with the styles API. The only one necessary for the delta updates use cases)
* Map+resolution
* Info
* Collections (more than one)
* Collections-info
* Maps with styles on the fly (involving collections)

## Using the standard

Those who want to just see the endpoints and responses can explore generic
OpenAPI definitions in this folder (please paste one of them in the Swagger Editor):

* [OGC-API-Maps/openapi/](https://github.com/opengeospatial/OGC-API-Maps/tree/master/openapi)

Several implementations of the draft standard exist:

[Implementations of the draft specification / demo services](./implementations.adoc)

## Relation to other OGC standards and previous works

OGC API - Maps follows on the footsteps of the [OGC](http://opengeospatial.org)'s Web Map Service (WMS) by enabling client applications to request maps of geospatial information on the web. However, OGC API - Maps is completely different from WMS, as OGC API - Maps focuses on a simple RESTful core specified as reusable [OpenAPI](http://openapis.org) components.

This is the [CURRENT](https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Maps/blob/master/core/standard/OAPI_Maps.html) working version of this initiative. An [Old](http://docs.opengeospatial.org/per/19-069.html) version of the specification was a deliverable in [Testbed-15](https://www.ogc.org/projects/initiatives/testbed15).

IMPORTANT: Some examples of OpenAPI documents that are used as inspiration and test of this work are at: https://app.swaggerhub.com/apis/UAB-CREAF

The OGC API - Maps and [OGC API - Tiles](https://github.com/opengeospatial/OGC-API-Tiles) specifications are closely related and should be considered complementary.

## Examples

An example OpenAPI definition, that describes a service that can serve only maps of one or more collections, is available at https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-maps-opf-xmp-more-1-collection/1.0.0

Another example OpenAPI definition, that describes a service that can serve only map (raster) tiles of one or more collections, is available at https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0

Several more examples are in the [openapi folder](core/standard/openapi).

The files in the [standards folder](core/standard/openapi) are structured in several parts that can be combined together.

Previous examples, some no longer accessible, are at [previous_examples.md](previous_examples.md).

## Overview

IMPORTANT NOTE: The description in this README.md can be older than the one in the [standard](core/standard) draft. In case of discrepancy the standard draft takes precedence.

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


## Communication

Join the WMS mailing list

Most work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/OGC-API-Maps/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership (and eventually the ISO/TC 211), shall be incorporated into OGC and ISO/TC 211 Web Map Service and Web Map Tile Service standards documents and that all copyright and intellectual property shall be vested to the OGC.

The WMS Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/OGC-API-Maps/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/OGC-API-Maps/master/LICENSE)
