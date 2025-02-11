# Filter works

It's easy to filter works with the `filter` parameter:

* Get works where the publication year is 2020\
  [https://api.openalex.org/works?filter=publication\_year:2020](https://api.openalex.org/works?filter=publication\_year:2020)

In this example the filter is `publication_year` and the value is 2020.

{% hint style="info" %}
It's best to [read about filters](../../how-to-use-the-api/get-lists-of-entities/filter-entity-lists.md) before trying these out. It will show you how to combine filters and build an AND, OR, or negation query.
{% endhint %}

## `/works` attribute filters

You can filter using these attributes of the [`Work`](work-object/) object (click each one to view their documentation on the `Work` object page):

* [`authorships.author.id`](work-object/#author) (alias: `author.id`)
* [`authorships.author.orcid`](work-object/#author) (alias: `author.orcid`)
* [`authorships.institutions.country_code`](work-object/#institutions) (alias: `institutions.country_code`)
* [`authorships.institutions.id`](work-object/#institutions) (alias `institutions.id`)
* [`authorships.institutions.ror`](work-object/#institutions) (alias: `institutions.ror`)
* [`authorships.institutions.type`](work-object/#institutions)
* [`authorships.is_corresponding`](work-object/#is\_corresponding) (alias: `is_corresponding`): this filter marks whether or not we have corresponding author information for a given work
* [`best_oa_location.is_oa`](work-object/#best\_oa\_location)
* [`best_oa_location.license`](work-object/#best\_oa\_location)
* [`best_oa_location.source.id`](work-object/#best\_oa\_location)
* [`best_oa_location.source.issn`](work-object/#best\_oa\_location)
* [`best_oa_location.source.host_organization`](work-object/#best\_oa\_location)
* [`best_oa_location.source.type`](work-object/#best\_oa\_location)
* [`best_oa_location.version`](work-object/#best\_oa\_location)
* [`cited_by_count`](work-object/#cited\_by\_count)
* [`concepts.id`](work-object/#concepts) (alias: `concept.id`)
* [`concepts.wikidata`](work-object/#concepts)
* [`doi`](work-object/#title)
* [`ids.pmcid`](../authors/author-object.md#ids)
* [`ids.pmid`](work-object/#ids) (alias: `pmid`)
* [`ids.openalex`](work-object/#ids) (alias: `openalex`)
* [`ids.mag`](work-object/#ids) (alias: `mag`)
* [`is_paratext`](work-object/#is\_paratext)
* [`is_retracted`](work-object/#is\_retracted)
* [`locations.is_oa`](work-object/#locations)
* [`locations.license`](work-object/#locations)
* [`locations.source.id`](work-object/#locations)
* [`locations.source.issn`](work-object/#locations)
* [`locations.source.host_organization`](work-object/#locations)
* [`locations.source.type`](work-object/#locations)
* [`locations.version`](work-object/#locations)
* [`open_access.is_oa`](work-object/#open\_access) (alias: `is_oa`)
* [`open_access.oa_status`](work-object/#open\_access) (alias: `oa_status`)
* [`primary_location.is_oa`](work-object/#primary\_location)
* [`primary_location.license`](work-object/#primary\_location)
* [`primary_location.source.id`](work-object/#primary\_location)
* [`primary_location.source.issn`](work-object/#primary\_location)
* [`primary_location.source.host_organization`](work-object/#primary\_location)
* [`primary_location.source.type`](work-object/#primary\_location)
* [`primary_location.version`](work-object/#primary\_location)
* [`publication_year`](work-object/#publication\_year)
* [`publication_date`](work-object/#publication\_date)
* [`type`](work-object/#type)

{% hint style="info" %}
Want to filter by the `display_name` of an associated entity (author, institution, source, etc.)? [See here.](search-works.md#why-cant-i-search-by-name-of-related-entity-author-name-institution-name-etc.)
{% endhint %}

## `/works` convenience filters

These filters aren't attributes of the [`Work`](work-object/) object, but they're handy for solving some common use cases:

#### `abstract.search`

Value: a search string

Returns: works whose abstract includes the given string. See the [search page](../../how-to-use-the-api/get-lists-of-entities/search-entities.md) for details on the search algorithm used.

* Get works with abstracts that mention "artificial intelligence": [`https://api.openalex.org/works?filter=abstract.search:artificial%20intelligence`](https://api.openalex.org/works?filter=abstract.search:artificial%20intelligence)\`\`

#### `authors_count`

Value: an Integer

Returns: works with the chosen number of [`authorships`](work-object/#authorships) objects (authors). You can use the inequality filter to select a range, such as `authors_count:>5`_._

* Get works that have exactly one author\
  [https://api.openalex.org/works?filter=authors\_count:1](https://api.openalex.org/works?filter=authors\_count:1)

#### `authorships.institutions.continent` \_\_ (alias: `institutions.continent`)

Value: a String with a valid [continent filter](../geo/continents.md#filter-by-continent)

Returns: works where at least _one_ of the author's institutions is in the chosen continent.

* Get works where at least one author's institution in each work is located in Europe\
  [https://api.openalex.org/works?filter=authorships.institutions.continent:europe](https://api.openalex.org/works?filter=authorships.institutions.continent:europe)

#### `authorships.institutions.is_global_south` \_\_ (alias: `institutions.is_global_south`)

Value: a Boolean (`true` or `false`)

Returns: works where at least _one_ of the author's institutions is in the Global South ([read more](../geo/regions.md#global-south)).

* Get works where at least one author's institution is in the Global South\
  [https://api.openalex.org/works?filter=authorships.institutions.is\_global\_south:true](https://api.openalex.org/works?filter=authorships.institutions.is\_global\_south:true)

#### `cited_by`

Value: the [OpenAlex ID](../../how-to-use-the-api/get-single-entities/#the-openalex-id) for a given work

Returns: works found in the given work's [`referenced_works`](work-object/#referenced\_works) section. You can think of this as **outgoing citations**.

* Get works cited by [https://openalex.org/W2766808518](https://openalex.org/W2766808518):\
  [`https://api.openalex.org/works?filter=cited_by:W2766808518`](https://api.openalex.org/works?filter=cited\_by:W2766808518)\`\`

#### `cites`

Value: the [OpenAlex ID](../../how-to-use-the-api/get-single-entities/#the-openalex-id) for a given work

Returns: works that cite the given work. This is works that have the given OpenAlex ID in the [`referenced_works`](work-object/#referenced\_works) section. You can think of this as **incoming citations**.

* Get works that cite [https://openalex.org/W2741809807](https://openalex.org/W2741809807): [`https://api.openalex.org/works?filter=cites:W2741809807`](https://api.openalex.org/works?filter=cites:W2741809807)\`\`

{% hint style="info" %}
The number of results returned by this filter may be slightly higher than the work's[`cited_by_count`](work-object/#cited\_by\_count)due to a timing lag in updating that field.
{% endhint %}

#### `concepts_count`

Value: an Integer

Returns: works with the chosen number of [`concepts`](work-object/#concepts).

* Get works with at least three concepts assigned\
  [https://api.openalex.org/works?filter=concepts\_count:>2](https://api.openalex.org/works?filter=concepts\_count:%3E2)

#### `display_name.search` (alias: `title.search`)

Value: a search string

Returns: works whose[`display_name`](work-object/#display\_name) (title) includes the given string; see the [search page](../../how-to-use-the-api/get-lists-of-entities/search-entities.md) for details.

* Get works with titles that mention the word "wombat":\
  [`https://api.openalex.org/works?filter=title.search:wombat`](https://api.openalex.org/works?filter=title.search:wombat)

{% hint style="info" %}
For most cases, you should use the [`search`](search-works.md#works-full-search) parameter instead of this filter, because it uses a better search algorithm and searches over abstracts as well as titles.
{% endhint %}

#### `from_created_date`

Value: a date, formatted as `yyyy-mm-dd`

Returns: works with [`created_date`](work-object/#created\_date) greater than or equal to the given date.

This field requires an OpenAlex Premium subscription to access. Please [contact us](mailto:support@openalex.org) if you are interested.

* Get works created on or _after_ January 12th, 2023 (does not work without valid API key):\
  [`https://api.openalex.org/works?filter=from_created_date:2023-01-12&api_key=myapikey`](https://api.openalex.org/works?filter=from\_created\_date:2023-01-12\&api\_key=myapikey)\`\`

#### `from_publication_date`

Value: a date, formatted as `yyyy-mm-dd`

Returns: works with [`publication_date`](work-object/#publication\_date) greater than or equal to the given date.

* Get works published on or _after_ March 14th, 2001:\
  [`https://api.openalex.org/works?filter=from_publication_date:2001-03-14`](https://api.openalex.org/works?filter=from\_publication\_date:2001-03-14)\`\`

{% hint style="info" %}
Filtering by publication date is not a reliable way to retrieve recently updated and created works, due to the way publishers assign publication dates. Use `from_created_date` or `from_updated_date` to get the latest changes in OpenAlex.
{% endhint %}

#### `from_updated_date`

Value: a date, formatted as `yyyy-mm-dd`

Returns: works with [`updated_date`](work-object/#updated\_date) greater than or equal to the given date.

This field requires an OpenAlex Premium subscription to access. Please [contact us](mailto:support@openalex.org) if you are interested.

* Get works updated on or _after_ January 12th, 2023 (does not work without valid API key):\
  [`https://api.openalex.org/works?filter=from_updated_date:2023-01-12&api_key=myapikey`](https://api.openalex.org/works?filter=from\_updated\_date:2023-01-12\&api\_key=myapikey)\`\`

#### **`fulltext.search`**

Value: a search string

Returns: works whose fulltext includes the given string. Fulltext search is powered by an index of word sequences called n-grams - see [Get N-grams](get-n-grams.md) for coverage details.

* Get works with fulltext that mention "climate change": [`https://api.openalex.org/works?filter=fulltext.search:climate%20change`](https://api.openalex.org/works?filter=fulltext.search:climate%20change)\`\`

{% hint style="info" %}
We combined some n-grams before storing them in our search database, so querying for an exact phrase using quotes does not always work well.
{% endhint %}

#### `has_abstract`

Value: a Boolean (`true` or `false`)

Returns: works that have or lack an abstract, depending on the given value.

* Get the works that have abstracts:\
  [`https://api.openalex.org/works?filter=has_abstract:true`](https://api.openalex.org/works?filter=has\_abstract:true)

#### `has_doi`

Value: a Boolean (`true` or `false`)

Returns: works that have or lack a DOI, depending on the given value. It's especially useful for [grouping](group-works.md).

* Get the works that have no DOI assigned:\
  [`https://api.openalex.org/works?filter=has_doi:false`](https://api.openalex.org/works?filter=has\_doi:false) \`\`

#### `has_oa_accepted_or_published_version`

Value: a Boolean (`true` or `false`)

Returns: works with at least one of the [`locations`](work-object/#locations) has [`is_oa`](work-object/#is\_oa)= true and [`version`](work-object/#version) is acceptedVersion or publishedVersion. For Works that undergo peer review, like journal articles, this means there is a peer-reviewed OA copy somewhere. For some items, like books, a published version doesn't imply peer review, so they aren't quite synonymous.

* Get works with an OA accepted or published copy\
  [`https://api.openalex.org/works?filter=has_oa_accepted_or_published_version:true`](https://api.openalex.org/works?filter=has\_oa\_accepted\_or\_published\_version:true)

#### `has_oa_submitted_version`

Value: a Boolean (`true` or `false`)

Returns: works with at least one of the [`locations`](work-object/#locations) has [`is_oa`](work-object/#is\_oa)= true and [`version`](work-object/#version) is submittedVersion. This is useful for finding works with preprints deposited somewhere.

* Get works with an OA submitted copy:\
  [`https://api.openalex.org/works?filter=has_oa_submitted_version:true`](https://api.openalex.org/works?filter=has\_oa\_submitted\_version:true)\`\`

#### `has_orcid`

Value: a Boolean (`true` or `false`)

Returns: if `true` it returns works where at least one author or has an [ORCID ID](work-object/#ids). If `false`, it returns works where no authors have an ORCID ID. This is based on the `orcid` field within [`authorships.author`](work-object/#author).

* Get the works where at least one author has an ORCID ID:\
  [`https://api.openalex.org/works?filter=has_orcid:true`](https://api.openalex.org/works?filter=has\_orcid:true) \`\`

#### `has_pmcid`

Value: a Boolean (`true` or `false`)

Returns: works that have or lack a PubMed Central identifier ([`pmcid`](work-object/#ids)) depending on the given value.

* Get the works that have a `pmcid`:\
  [`https://api.openalex.org/works?filter=has_pmcid:true`](https://api.openalex.org/works?filter=has\_pmcid:true)\`\`

#### `has_pmid`

Value: a Boolean (`true` or `false`)

Returns: works that have or lack a PubMed identifier ([`pmid`](../authors/author-object.md#ids)), depending on the given value.

* Get the works that have a `pmid`:\
  [`https://api.openalex.org/works?filter=has_pmid:true`](https://api.openalex.org/works?filter=has\_pmid:true)\`\`

#### `has_ngrams`

Value: a Boolean (`true` or `false`)

Returns: works for which n-grams are available or unavailable, depending on the given value. N-grams power fulltext searches through the [`fulltext.search`](filter-works.md#fulltext.search) filter and the [`search`](search-works.md#works-full-search) parameter.

* Get the works that have n-grams:\
  [`https://api.openalex.org/works?filter=has_ngrams:true`](https://api.openalex.org/works?filter=has\_ngrams:true)

#### `has_references`

Value: a Boolean (`true` or `false`)

Returns: works that have or lack [`referenced_works`](work-object/#referenced\_works), depending on the given value.

* Get the works that have references:\
  [`https://api.openalex.org/works?filter=has_references:true`](https://api.openalex.org/works?filter=has\_references:true)

#### `primary_location.source.has_issn`

Value: a Boolean (`true` or `false`)

Returns: works where the [primary\_location](work-object/#primary\_location) has at least one ISSN assigned.

* Get the works that have an ISSN within the primary location:\
  [`https://api.openalex.org/works?filter=primary_location.source.has_issn:true`](https://api.openalex.org/works?filter=primary\_location.source.has\_issn:true)\`\`

#### `raw_affiliation_string.search`

Value: a search string

Returns: works that have at least one [`raw_affiliation_string`](work-object/#raw\_affiliation\_string) which includes the given string. See the [search page](../../how-to-use-the-api/get-lists-of-entities/search-entities.md) for details on the search algorithm used.

* Get works with the words _Department of Political Science, University of Amsterdam_ somewhere in at least one author's `raw_affiliation_string`: [`https://api.openalex.org/works?filter=raw_affiliation_string.search:department%20of%20political%20science%20university%20of%amsterdam`](https://api.openalex.org/works?filter=raw\_affiliation\_string.search:department%20of%20political%20science%20university%20of%20amsterdam)\`\`

#### `related_to`

Value: the [OpenAlex ID](../../how-to-use-the-api/get-single-entities/#the-openalex-id) for a given work

Returns: works found in the given work's [`related_works`](work-object/#related\_works) section.

* Get works related to [https://openalex.org/W2486144666](https://openalex.org/W2486144666):\
  [`https://api.openalex.org/works?filter=related_to:W2486144666`](https://api.openalex.org/works?filter=related\_to:W2486144666)

#### `repository`

Value: the [OpenAlex ID](../../how-to-use-the-api/get-single-entities/#the-openalex-id) for a given [source](../venues/venue-object.md)

Returns: works where the chosen [source ID](../venues/venue-object.md#id) exists within the [`locations`](work-object/#locations).

You can use this to find works where authors are associated with your university, but the work is not part of the university's repository. :clap:

* Get works that are available in the University of Michigan Deep Blue repository (OpenAlex ID: https://openalex.org/S4306400393)\
  [`https://api.openalex.org/works?filter=repository:S4306400393`](https://api.openalex.org/works?filter=repository:S4306400393)
* Get works where at least one author is associated with the University of Michigan, but the works are not found in the University of Michigan Deep Blue repository\
  [`https://api.openalex.org/works?filter=institutions.id:I27837315,repository:!S4306400393`](https://api.openalex.org/works?filter=institutions.id:I27837315,repository:!S4306400393)

#### `to_publication_date`

Value: a date, formatted as `yyyy-mm-dd`

Returns: works with [`publication_date`](work-object/#publication\_date) less than or equal to the given date.

* Get works published on or _before_ March 14th, 2001:\
  [`https://api.openalex.org/works?filter=to_publication_date:2001-03-14`](https://api.openalex.org/works?filter=to\_publication\_date:2001-03-14)\`\`

#### `version`

Value: a String with value `publishedVersion`, `submittedVersion`, `acceptedVersion`, or `null`

Returns: works where the chosen version exists within the [`locations`](work-object/#locations). If `null`, it returns works where no version is found in any of the locations.

* Get works where a published version is available in at least one of the locations:\
  [https://api.openalex.org/works?filter=version:publishedVersion](https://api.openalex.org/works?filter=version:publishedVersion)
