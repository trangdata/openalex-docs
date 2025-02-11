# Limitations

## Works with more than 100 authors are truncated

When retrieving a list of works in the API, the `authorships` list within each work will be cut off at 100 authorships objects in order to keep things running well. When this happens the boolean value `is_authors_truncated` will be available and set to `true`. This affects a small portion of OpenAlex, as there are around 35,000 works with more than 100 authors.

* Example list of works with truncated authors\
  [https://api.openalex.org/works?filter=authors\_count:>100](https://api.openalex.org/works?filter=authors\_count:%3E100)

To see the full list of authors, go to the individual record for the work, which is never truncated.

* Work with all 249 authors available\
  [https://api.openalex.org/works/W2168909179](https://api.openalex.org/works/W2168909179)
