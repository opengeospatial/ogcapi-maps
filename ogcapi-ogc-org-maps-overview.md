# OGC API - Maps

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable
API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. The draft OGC API - Maps standard describes an API that presents data as maps by applying a style. The draft standard allows a client application to request maps as images, or change parameters such as size and coordinate reference systems at the time of request, making them implementer-friendly and easily understandable by developers without geospatial experience.


## Overview of OGC API - Maps - Part 1: Core

OGC API - Maps is a draft API standard that provides maps representing geospatial data.

```
GET /collections
```

A list of collections of all maps available from this API.

```
GET /collections/{collectionId}
```

Description of a collection `{collectionId}` available from this API. It defines what is possible to do with it to generate a map.

```
GET /collections/{collectionId}/map
```

Retrieves the maps description for this collection including the `links` to get a `map`, and the `infoTemplate`.

```
GET /map
```

Retrieves the maps description for this collection including the `links` to get a `map`, and the `infoTemplate`.


```
GET /collections/{collectionId}/map/{styleId}
```

Retrieves a map in the requested crs, on the requested bbox designed to be shown in a rendering device of a width and a height. Some formats require to apply a style on the server side (e.g. png, jpeg, gif) and some others   might include a reference to a style to be applied in the client side.


```
GET /collections/{collectionId}/map/{styleId}/info
```

Retrieves a information about a feature presented on the map in the requested crs, on the requested bbox designed to be shown in a rendering device of a width and a height. Some formats require to apply a style on the server side (e.g. png,  jpeg, gif) and some others might include a reference to a style to be applied  in the client side.


```
GET /map/{styleId}
```

Retrieves a map in the requested crs, on the requested bbox designed to be shown in a device of a width and a height. Some formats require to apply  a style on the server side (e.g. png, jpeg, gif) and some others might include  a reference to a style to be applied in the client side.


```
GET /map/{styleId}/info
```

Retrieves a information about a feature presented on the map for collections in the requested crs, on the requested bbox desigend to be shown in a rendering device of a  width and a height. Some formats require to apply a style on the server side (e.g. png, jpeg, gif) and some others might include a reference to a style to be applied in the client side.
