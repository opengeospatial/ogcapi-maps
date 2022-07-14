This folder contains the extension to the core.

For some time, the bbox capacity (scaling) in maps was considered as an extension but it was finally moved to the core (part 1)

Current plans are that the GetFeatureInfo will not be included in the core. While there are some opinions that the GetFeatureInfo functionality could be better implemented by the Features of Coverages API, there are still some users that want the functionality as it is today. One use case is a API that does not allow download capabilities but still wants to allow for clicking on maps. This possible extension is not defined yet but could be considered (https://github.com/opengeospatial/ogcapi-maps/issues/81)
