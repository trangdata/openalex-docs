---
description: Companies and organizations that distribute works
---

# 🏢 Publishers

Publishers are companies and organizations that distribute journal articles, books, and theses. OpenAlex indexes about 7,000 publishers.

You can get a publisher from the OpenAlex API like this:

* Get the publisher Elsevier with OpenAlex ID `P4310311775`\
  [https://api.openalex.org/publishers/P4310311775](https://api.openalex.org/publishers/P4310311775)

Our publisher data is closely tied to the publisher information in Wikidata. So the [Canonical External ID](../../how-to-use-the-api/get-single-entities/#canonical-external-ids) for OpenAlex publishers is a Wikidata ID, and almost every publisher has one. Publishers are linked to sources through the `host_organization` field.

## What's next

Learn more about what you can do with concepts:

* [The Publisher object](publisher-object.md)
* [Get a single publisher](get-a-single-publisher.md)
* [Get lists of publishers](get-lists-of-publishers.md)
* [Filter publishers](filter-publishers.md)
* [Search publishers](search-publishers.md)
* [Group publishers](group-publishers.md)
