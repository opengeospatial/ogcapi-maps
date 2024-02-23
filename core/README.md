# OGC API - Maps - Part 1: Core Specification

This directory contains the OGC API - Maps - Part 1: Core specification.  The specification defines a Web API for requesting map images over the Internet. OGC API - Maps makes it easy for a client to request images, changing parameters such as size and coordinate reference systems at the time of request. A server that implements OGC API - Maps provides information about what maps it offers, as well as producing a map and answering queries about the content of the maps. OGC API - Maps is expected to address use cases similar to those addressed by the Web Map Service (WMS) standard.

## Building

```
cd standard

docker run -v "$(pwd)":/metanorma -v ${HOME}/.fontist/fonts/:/config/fonts  metanorma/metanorma  metanorma compile --agree-to-terms -t ogc -x html,pdf 20-058.adoc

```