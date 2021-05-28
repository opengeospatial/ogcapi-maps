# OGC API - Maps

This GitHub repository contains [OGC](https://www.ogc.org/)'s multi-part standard for querying and retrieving maps on the web, "OGC API - Maps". The draft specification is available in [HTML](http://docs.ogc.org/DRAFTS/20-058.html) and [PDF](http://docs.ogc.org/DRAFTS/20-058.pdf). 

A [Map](https://en.wikipedia.org/wiki/Map) provides a visual representation of relationships between things within a defined space. OGC API - Maps defines a standardized way to request information about a map, query a map's contents, and obtain an image of a map to serve multiple purposes (e.g. displaying maps in web pages, mapping software, etc.). OGC API - Maps also makes it easy to change parameters of the map at the time of request (e.g. size, coordinate reference system used).

OGC API - Maps is part of the suite of [OGC API standards](https://ogcapi.ogc.org/) that define modular API building blocks to enable access and use of location (i.e. geospatial) information in a consistent way. Information about other OGC APIs can be found [online](https://ogcapi.ogc.org/).

## Overview

IMPORTANT NOTE: The description in this README.md can be older than the one in the [standard](core/standard) draft. In case of discrepancy the standard draft takes precedence.

OGC API - Maps is a standard API that provides maps representing geospatial data.

```
GET /.../.../map/{styleId}
```

Maps typically contain multiple types of information (e.g. buildings, roads, lakes, etc.), commonly known as "layers". In OGC API - Maps, "{collectionId}" or "coverage" is used to identify the individual layers a map contains.

Maps use Coordinate Reference Systems (CRS) to define their position within a space (e.g. the Earth's surface). OGC API - Maps allows maps to be requested in any available CRS.

```
GET /.../.../map/{styleId}?crs=CRS84&bbox=160.6,-55.95,-170,-25.89&width=600&height=400
```
Maps can be requested in any available CRS and can be subset by bbox width and height (and eventually other parameters such as time and elevation)
```
GET /.../.../map/{styleId}?crs=CRS84&bbox=160.6,-55.95,-170,-25.89&width=600&height=400
```
Returns a map - a representation of real-world elements at a given resolution. {styleId} is optional.

## Standards

After a while getting familiar and playing with the OpenAPI definition files (explained just below in the "Examples section"), we have finally started to write the standard. We have decided on an aggressive path towards a modular specification with a simple core and multiple extensions. The extensions are yet to be determined.

The standard is written using asciidoc using many files that might be difficult to trace. Please see the standard document as a single HTML page that is EASY TO READ here: http://docs.opengeospatial.org/DRAFTS/20-058.html

We received several recommendations to separate the specifications into a core and extensions. In March 2020, we decided to restructure the GitHub repository to separate the core and the extensions into different documents that might be elaborated at different speeds.

At this moment in time we are working on doing this separation by moving files around.

### OGC API - Maps - Part 1: Core
The definition of OGC API - Maps - Part 1: Core is the immediate next step. The Standards Working Group (SWG) [agreed](https://github.com/opengeospatial/ogcapi-maps/issues/32) on the structure shown below.

1. Map resource: It specifies a map resource, which is a resource that contains information on how to formulate a request to a map. This document includes the CRSs and styles supported and other metadata (including attribution). It also specifies how to apply a style to a map resources to get a styled map.

2. DatasetMap - OGC API Common - Part 1 (dataset, /map resource at the root): Defines how to get a map resource from the dataset (or datasets) represented by the services. it will tell the path to get a map resources.

3. GeoDataResourceMap - OGC API Common - Part 2 / OGC Feature - Part 1 (collection connection, /maps resource after {collectionID}): It will define how to specify the a link to a map resource containing a representation of this geospatial data resource (path).

NOTE: GeoDataResourceSelection - together with 3, geodata= query parameters: This is identical to the GeoDataResourceSelection conformance class of OGC API - Common and if done adequately, the conformance class is shared with OGC API - Tiles (or the other way around) and is not repeated here.

### Extensions

1. BBoxSubset: It specifies how to include a query parameter to subset a styled map using a BBOX, WIDTH, HEIGHT etc as a query parameters. This is a partition that could be input for OGC API Common. Some considerations include OGC API - Features BBOX, representation of Time instances, and Clip versus Intersect.



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

* [ogcapi-maps/openapi/](https://github.com/opengeospatial/ogcapi-maps/tree/master/openapi)

Several implementations of the draft standard exist:

[Implementations of the draft specification / demo services](./implementations.adoc)

## Relation to other OGC standards and previous works

OGC API - Maps follows on the footsteps of the [OGC](http://opengeospatial.org)'s Web Map Service (WMS) by enabling client applications to request maps of geospatial information on the web. However, OGC API - Maps is completely different from WMS, as OGC API - Maps focuses on a simple RESTful core specified as reusable [OpenAPI](http://openapis.org) components.

This is the [CURRENT](http://docs.opengeospatial.org/DRAFTS/20-058.html) working version of this initiative. An [Old](http://docs.opengeospatial.org/per/19-069.html) version of the specification was a deliverable in [Testbed-15](https://www.ogc.org/projects/initiatives/testbed15).

IMPORTANT: Some examples of OpenAPI documents that are used as inspiration and test of this work are at: https://app.swaggerhub.com/apis/UAB-CREAF

The OGC API - Maps and [OGC API - Tiles](https://github.com/opengeospatial/ogcapi-tiles) specifications are closely related and should be considered complementary.

## Examples

An example OpenAPI definition, that describes hypothetical WebAPI conformat to this standard is available at https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-maps-opf-xmp-more-1-collection/1.0.0
A resolved (almost without dependencies with other files) YAML file, synchronized with the previous working document, is available in this github repository at: https://github.com/opengeospatial/ogcapi-maps/tree/master/openapi/swaggerhub/maps.yaml

Another example OpenAPI definition, that describes a service that can serve only map (raster) tiles of one or more collections, is available at https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0

Several more examples are in the [openapi folder](openapi). The files are structured such that they can be combined together.

Previous examples, some no longer accessible, are at [previous_examples.md](previous_examples.md).

## Communication

Join the WMS mailing list

Most work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-maps/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership (and eventually the ISO/TC 211), shall be incorporated into the relevant OGC standards documents and that all copyright and intellectual property shall be vested to the OGC.

The WMS Standards Working Group (SWG) is the group at OGC that is responsible for the stewardship of the standard being developed in this GitHub repository, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/ogcapi-maps/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-maps/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169
