# Maps

## How to get a map tile from a feature collection step by step

### Follow the links approach
* Visit the landing page
  - discover a link to collections
* Visit the /collections page
  - look for the list of {collectionId}s and select an id.
* Visit your favorite collection using /collections/{collectionId}
  - look for a link of rel='map'
* Visit the link of rel='map'
  - look for the 'links' property and select a 'link' with rel='item' and 'type' with the format you like
  - look for the 'styles' property with the list of stylesId's and select and id.
  - look for the 'crs' property to know about the crs values
* Use the URL template and substitute the variable by values to get a URL and add all query parameters to subset the map
  - get your map!

### API approach
* Visit the API page directly
  - look for the /collections path
  - look for the /collections/{collectionId}/map path
  - look for the /collections/{collectionId}/map/{styleId} path
* Visit the /collections page
  - look for the list of {collectionId}s and select an id.
* Visit the /collections/{collectionId}/map/tiles page
  - look for the 'styles' property with the list of stylesId's and select and id.
  - look for the 'crs' property to know about the crs values
* Use the /collections/{collectionId}/map/{styleId} template and substitute the variable by values to get a URL and add all query parameters to subset the map
  - get your map!


### Details

A "OGC API - Maps" is a standard API that provides maps representing geospatial data.

```
GET /{geospatialResource}/map/{styleId}
```

The identifier of the {geospatialResource} is replaced by "/collections/{collectionId}" or a coverage or another geospatialResource.

Maps can be requested in any available CRS and can be subset by bbox width and height (and eventually other parameters such as time and elevation)
```
GET /{geospatialResource}/map/{styleId}?crs=CRS84&bbox=160.6,-55.95,-170,-25.89&width=600&height=400
```
Returns a map - a representation of real-world elements at a given resolution. 
