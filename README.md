# OGC API - Features

This GitHub repository contains [OGC](http://opengeospatial.org)'s
standard for querying geospatial information on the web, "OGC API - Features". The 
latest version of the specification can be found at [docs.opengeospatial.org/is/17-069r3/17-069r3.html](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html).

OGC API standards define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable
API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. OGC API Features
specifies the fundamental API building blocks for interacting with features.
The spatial data community uses the term 'feature' for things in the real world
that are of interest.

If you are unfamiliar with the term 'feature', the explanations on
[Spatial Things, Features and Geometry](https://www.w3.org/TR/sdw-bp/#spatial-things-features-and-geometry)
in the W3C/OGC Spatial Data on the Web Best Practice document provide more detail.

## Overview

OGC API Features provides access to collections of geospatial data.

```
GET /collections
```

Lists the collections of data on the server that can be queried ([section 7.13](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_collections_)),
and each describes basic information about the geospatial data collection, like its id and description, as well as the
spatial and temporal extents of all the data contained.

```
GET /collections/buildings/items?bbox=160.6,-55.95,-170,-25.89
```

Requests all the data in the collection "buildings" that is in the New Zealand economic zone.
The response format (typically HTML or a [GeoJSON](http://geojson.org/) feature
collection, but GML is supported, too, and extensions can easily supply others) is determined using
[HTTP content negotiation](https://restfulapi.net/content-negotiation/).

Data is returned in pageable chunks, with each response containing a `next` link
as many collections are quite large. The core specification supports a few basic filters, in
addition to the `bbox` filter above, with extensions providing more advanced options
([section 7.15](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_items_)).

```
GET /collections/{collectionId}/items/{featureId}
```

Returns a single 'feature' - something in the real-world (a building,
a stream, a county, etc.) that typically is described by a geometry plus other properties.
This provides a stable, canonical URL to link to the 'thing'
([section 7.16](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature_)).

## Using the standard

The standard is on the OGC website:

* [OGC API - Features - Part 1: Core](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html)

A [PDF version](http://docs.opengeospatial.org/is/17-069r3/17-069r3.pdf) is available, too.

Those who want to just see the endpoints and responses can explore [examples of
OpenAPI definitions](https://github.com/opengeospatial/ogcapi-features/tree/master/core/examples/openapi).

The reference version of the OpenAPI components and XML schemas are published
in the [OGC schema repository](http://schemas.opengis.net/ogcapi/features/).

Several implementations of the draft standard exist:

* [Implementations of the draft specification / demo services](implementations.md)

## Communication

Join the [mailing list](https://lists.opengeospatial.org/mailman/listinfo/wfs-fes.swg) or [![chat at https://gitter.im/opengeospatial/WFS_FES](https://badges.gitter.im/opengeospatial/WFS_FES.svg)](https://gitter.im/opengeospatial/WFS_FES?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Most all work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-features/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Additional parts of OGC API - Features

The OGC Features API SWG has identified the following extensions to Part 1 (Core)
as the highest priority:

* [OGC API - Features - Part 2: Coordinate Reference Systems by Reference (draft)](http://docs.opengeospatial.org/DRAFTS/18-058.html);
* filter/query capabilities;
* simple transactions.

A joint sprint with [STAC](https://github.com/radiantearth/stac-spec) and the [OGC API Catalogues SWG](https://github.com/opengeospatial/CAT4.0) to advance richer query/filter capabilities is planned for [November 5-7, 2019, in Arlington, VA](https://www.opengeospatial.org/pressroom/pressreleases/3074).

## Additional information

Open issues for Part 1 (Core) are documented in a [GitHub project](https://github.com/opengeospatial/ogcapi-features/projects/1).

In parallel, Part 1 (Core) has also be submitted to ISO/TC 211 and is in the [Draft International Standard (DIS) ballot](https://www.iso.org/standard/32586.html).

Open issues for Part 2 (CRS) are documented in another [GitHub project](https://github.com/opengeospatial/ogcapi-features/projects/2).

Additional links:

* [Background of this activity](background.md)
* [The next version of WFS - an overview](overview.md)
* [UML for Part 1, Core](uml/README.md)
* [Status of Part 1, Core, in ISO](https://www.iso.org/standard/32586.html)
* [Home of the standard on the OGC website](https://www.opengeospatial.org/standards/ogcapi-features)

## [Contributing](CONTRIBUTING.md)

The contributor understands that any contributions, if accepted by the OGC Membership and ISO/TC 211, shall be incorporated into OGC and ISO/TC 211 OGC API standards documents and that all copyright and intellectual property shall be vested to the OGC.

The Features API Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Features API Standards Working Group Charter](CHARTER.adoc)
* [Open issues](https://github.com/opengeospatial/ogcapi-features/issues)
* [Proposing changes](https://github.com/opengeospatial/ogcapi-features/wiki/Propose-a-change-to-a-draft-of-a-specification-document)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-features/master/LICENSE)
