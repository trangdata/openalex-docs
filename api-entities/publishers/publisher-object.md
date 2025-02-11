# Publisher object

Here are the fields in a publisher object. When you use the API to get a single publisher or lists of publishers, this is what's returned.

### `alternate_titles`

_List:_ A list of alternate titles for this publisher.

```json
alternate_titles: [
  "Elsevier",
  "elsevier.com",
  "Elsevier Science",
  "Uitg. Elsevier",
"السفیر",  
"السویر",  
"انتشارات الزویر",  
"لودویک السفیر",  
  "爱思唯尔"
]
```

### `cited_by_count`

_Integer:_ The number of citations to works that are linked to this publisher through journals or other sources.

For example, if a publisher publishes 27 journals and those 27 journals have 3,050 works, this number is the sum of the cited\_by\_count values for all of those 3,050 works.&#x20;

```json
cited_by_count: 407508754
```

### `country_codes`

_List:_ The countries where the publisher is primarily located, as an [ISO two-letter country code](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2).

```json
country_codes: ["DE"]
```

### `counts_by_year`

_List:_ The values of [`works_count`](publisher-object.md#works\_count) and [`cited_by_count`](publisher-object.md#cited\_by\_count) for _each_ of the last ten years, binned by year. To put it another way: for every listed year, you can see how many new works are linked to this publisher, and how many times _any_ work linked to this publisher was cited.

Years with zero citations and zero works have been removed so you will need to add those back in if you need them.

```json
counts_by_year: [
    {
        year: 2021,
        works_count: 4211,
        cited_by_count: 120939
    },
    {
        year: 2020,
        works_count: 4363,
        cited_by_count: 119531
    },
    
    // and so forth
]
```

### `created_date`

_String:_ The date this `Publisher` object was created in the OpenAlex dataset, expressed as an [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) date string.&#x20;

```json
created_date: "2017-08-08"
```

### `display_name`

_String:_ The primary name of the publisher.

```json
display_name: "Elsevier BV"
```

### `hierarchy_level`

_Integer:_ The hierarchy level for this publisher. A publisher with hierarchy level 0 has no parent publishers. A hierarchy level 1 publisher has one parent above it, and so on.

```json
hierarchy_level: 1
```

### `id`

_String:_ The OpenAlex ID for this publisher.

```json
id: "https://openalex.org/P4310320990"
```

### `ids`

_Object:_ All the external identifiers that we know about for this publisher. IDs are expressed as URIs whenever possible. Possible ID types:

* `openalex` _String:_ this publishers's [OpenAlex ID](../../how-to-use-the-api/get-single-entities/#the-openalex-id)
* `ror` _String:_ this publisher's ROR ID
* `wikidata` _String:_ this publisher's [Wikidata ID](https://www.wikidata.org/wiki/Wikidata:Identifiers)

<pre class="language-json"><code class="lang-json">ids: {
  openalex: "https://openalex.org/P4310320990",
  ror: "https://ror.org/02scfj030",
<strong>  wikidata: "https://www.wikidata.org/entity/Q746413"
</strong>},
</code></pre>

### `parent_publisher`

_String:_ An OpenAlex ID linking to the direct parent of the publisher. This will be null if the publisher's `hierarchy_level` is 0.

```json
parent_publisher: "https://openalex.org/P4310311775"
```

### `sources_api_url`

_String:_ An URL that will get you a list of all the sources published by this publisher.

We express this as an API URL (instead of just listing the sources themselves) because there might be thousands of sources linked to a publisher, and that's too many to fit here.

```json
sources_api_url: "https://api.openalex.org/sources?filter=host_organization.id:P4310319965"
```

### `updated_date`

_String:_ The last time anything in this publisher object changed, expressed as an [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) date string. This date is updated for _any change at all_, including increases in various counts.

```json
updated_date: "2021-12-25T14:04:30.578837"
```

### `works_count`

_Integer:_ The number of works published by this publisher.

```json
works_count: 13789818
```
