# Location object

The `Location` object describes the location of a given work. It's only found as part of the `Work` object.

Locations are meant to capture the way that a work exists in different versions. So, for example, a work may have a version that has been peer-reviewed and published in a journal (the [version of record](https://en.wikipedia.org/wiki/Version\_of\_record)). This would be one of the work's locations. It may have another version available on a preprint server like [arXiv](https://arxiv.org/)—this version having been posted before it was accepted for publication. This would be another one of the work's locations.

Locations are meant to cover anywhere that a given work can be found. This can include journals, proceedings, institutional repositories, and subject-area repositories like [arXiv ](https://arxiv.org/)and [bioRxiv](https://www.biorxiv.org/). If you are only interested in a certain one of these (like journal), you can use a [filter](../filter-works.md) to specify the `locations.source.type`. ([Learn more about types here.](../../venues/venue-object.md#type))

There are three places in the `Work` object where you can find locations:

* [`primary_location`](./#primary\_location): The best (closest to the [version of record](https://en.wikipedia.org/wiki/Version\_of\_record)) copy of this work.
* [`best_oa_location`](./#best\_oa\_location): The best available open access location of this work.
* [`locations`](./#locations): A list of all of the locations where this work lives. This will include the two locations above if availabe, and can also include other locations.

### `is_oa`

_Boolean:_ `True` if this work is Open Access (OA).&#x20;

There are [many ways to define OA](https://peerj.com/articles/4375/#literature-review). OpenAlex uses a broad definition: having a URL where you can read the fulltext of this work without needing to pay money or log in.

```json
is_oa: true
```

### landing\_page\_url

_String:_ The landing page URL for this location.&#x20;

```json
landing_page_url: "https://doi.org/10.1590/s1678-77572010000100010"
```

### license

_String:_ The location's publishing license. This can be a [Create Commons](https://creativecommons.org/about/cclicenses/) license such as cc0 or cc-by, a publisher-specific license, or null which means we are not able to determine a license for this location.&#x20;

```json
license: "cc-by"
```

### source

_Object:_ Information about the source of this location, as a [`DehydratedSource`](../../venues/venue-object.md#the-dehydratedsource-object) object.

The concept of a source is meant to capture a certain social relationship between the host organization and a version of a work. When an organization puts the work on the internet, there is an understanding that they have, at some level, endorsed the work. This level varies, and can be very different depending on the source!

```json
source {
    id: "https://openalex.org/S125754415",
    display_name: "Proceedings of the National Academy of Sciences of the United States of America",
    issn_l: "0027-8424",
    issn: ["1091-6490", "0027-8424"],
    host_organization: "https://openalex.org/P4310320052",
    type: "journal"
}
```

### pdf\_url

_String:_ A URL where you can find this location as a PDF.&#x20;

```json
pdf_url: "http://www.scielo.br/pdf/jaos/v18n1/a10v18n1.pdf"
```

### version

_String:_ The version of the work, based on the [DRIVER Guidelines versioning scheme.](https://wiki.surfnet.nl/display/DRIVERguidelines/DRIVER-VERSION+Mappings) Possible values are:.

* `publishedVersion`: The document’s version of record. This is the most authoritative version.
* `acceptedVersion`: The document after having completed peer review and being officially accepted for publication. It will lack publisher formatting, but the _content_ should be interchangeable with the that of the `publishedVersion`.
* `submittedVersion`: the document as submitted to the publisher by the authors, but _before_ peer-review. Its content may differ significantly from that of the accepted article.

```json
version: "publishedVersion"
```
