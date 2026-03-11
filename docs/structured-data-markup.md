# [Draft] Structured data markup and Schema.org

_What is structured data, how do you add it, and how do you test it?_

This guide is aimed at helping engineers and information architects identify ways to use structured data and ensure it is valid.

## Definitions 📖

| Term | Definition|
| ---- | --------- |
| Structured data | Content marked up with machine-readable annotations that describe its properties and relationships to other content, according to a standard or convention. |
| Schema.org | A controlled vocabulary published by Google, Microsoft, Yahoo, and Yandex to provide search engines with greater context for understanding the properties of and relationships between content on a website. |
| JSON-LD | A standard syntax for representing data properties and links using JavaScript Object Notation. |

## Introduction to structured data 🏗️

When working with structured data we sometimes use terms interchangeably, which can cause confusion. This section covers some relevant distinctions.

### What is structured data?

_Content marked up with machine-readable annotations that describe its properties and relationships to other content, according to a standard or convention._

(details to follow)

### What is Schema.org?

_A controlled vocabulary published by Google, Microsoft, Yahoo, and Yandex to provide search engines with greater context for understanding the properties of and relationships between content on a website._

The schemas published by Schema.org describe “things”—content objects or entities—such as a [news article](https://schema.org/NewsArticle), [breadcrumb trail](https://schema.org/BreadcrumbList), or [government organization](https://schema.org/GovernmentOrganization). Each object is part of a [hierarchical taxonomy](https://schema.org/docs/full.html) and has its own properties, with more specific objects inheriting properties from their “parent” objects while introducing properties of their own.

As well as having their own properties, schema objects can also be related to one another using URLs (e.g. a `NewsArticle` published by a `GovernmentOrganization`). Such data linkages, if specified correctly, can form a limited knowledge graph that search engines ([and presumably LLMs](llms-ai-and-geo.md)) can understand.

Schema.org is not a full ontology, in the sense of [OWL](https://www.w3.org/TR/owl-ref/). For a quick comparison, read Henriette Harmse’s post on [The difference between Schema.org and OWL](https://henrietteharmse.com/2022/01/25/the-difference-between-schema-org-and-owl/).

### What is JSON-LD?

_A standard syntax for representing data properties and links using JavaScript Object Notation._

(details to follow)

### What are RDFa and Microdata?

(details to follow)

### What is Wikidata?

(details to follow)

## Structured data tools 🛠️

1. [Schema Markup Generator (JSON-LD)](https://technicalseo.com/tools/schema-markup-generator/) — GUI for creating a small number of popular objects
2. [Schema Markup Validator](https://validator.schema.org/) — structured data testing tool
3. [Rich Results Tester](https://search.google.com/test/rich-results) — Google results testing tool
4. [JSON-LD Playground](https://json-ld.org/playground/) — viewer for exploring JSON-LD objects
5. [Schema Visualizer](https://schema-visualizer.yoast.com/) — schema validator and graph viewer

## Search engine guidance 🔍

* [Structured data markup that Google Search supports](https://developers.google.com/search/docs/appearance/structured-data/search-gallery)
* [Marking up your site with structured data (Bing)](https://www.bing.com/webmasters/help/marking-up-your-site-with-structured-data-3a93e731)

## Further reading 📚

* [The difference between Schema.org and OWL](https://henrietteharmse.com/2022/01/25/the-difference-between-schema-org-and-owl/) — blog post
* [JSON-LD 1.1: A JSON-based Serialization for Linked Data](https://www.w3.org/TR/json-ld11/#abstract) — W3C standard 
* [Using @id in Schema.org Markup for SEO & Knowledge Graphs](https://momenticmarketing.com/blog/id-schema-for-seo-llms-knowledge-graphs#understanding-references-and-connections) — blog post