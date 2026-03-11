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

In the context of web content “structured data” refers to methods of marking up (“tagging”) content with machine-readable annotations that describe it in terms of some shared standard or convention.

An early example of adding structure to web content was the [Microformats](https://en.wikipedia.org/wiki/Microformat) effort of the mid-2000s. Microformats was a HTML-compatible method for adding semantics to content that would map to RFC standards such as [vCard](https://en.wikipedia.org/wiki/VCard) and [iCalendar](https://en.wikipedia.org/wiki/ICalendar). This made it possible for users to more easily add contact information or events discovered on the web to contacts and calendaring software.

For example, a controlled set of class names could be added to elements that contain contact information:

```html
<ul class="vcard">
  <li class="fn">Joe Doe</li>
  <li class="org">The Example Company</li>
  <li class="tel">604-555-1234</li>
  <li><a class="url" href="http://example.com/">http://example.com/</a></li>
</ul>
```

This [hCard](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Microformats#h-card) Microformat could be detected and converted to a downloadable vCard by browser extensions such as [Operator](https://en.wikipedia.org/wiki/Operator_(extension)) for Firefox. 

In 2011 Schema.org was [formed](https://en.wikipedia.org/wiki/Schema.org) by Google, Bing, and Yahoo. It expanded on efforts like Microformats and began the process of building out a vocabulary of types that can be used for annotating a range of content found on websites.

### What is Schema.org?

[Schema.org](https://schema.org/) is an industry [partnership](https://en.wikipedia.org/wiki/Schema.org) created by Google, Microsoft, Yahoo, and Yandex to provide a systematic method for publishers to mark up their content with machine-readable data that provides more context for the nature of content on a website. It is not a standard in the W3C sense.

The schemas published by Schema.org can be used to tell search engines what type of “thing” a piece of content is, such as a [news article](https://schema.org/NewsArticle), [breadcrumb trail](https://schema.org/BreadcrumbList), or [government organization](https://schema.org/GovernmentOrganization). Each object (or entity) is part of a [hierarchical taxonomy](https://schema.org/docs/full.html) and has its own properties (e.g. name, URL, unique identifier), with more specific types inheriting properties from their “parents” while introducing properties of their own.

As well as having their own properties, schema objects can also be related to one another using URLs (e.g. a `NewsArticle` published by a `GovernmentOrganization`). Such data linkages, if specified correctly, can form a limited knowledge graph that search engines ([and presumably LLMs](llms-ai-and-geo.md)) can understand.

Schema.org is not a full ontology, in the sense of [OWL](https://www.w3.org/TR/owl-ref/). For a quick comparison, read Henriette Harmse’s post on [The difference between Schema.org and OWL](https://henrietteharmse.com/2022/01/25/the-difference-between-schema-org-and-owl/).

### What is JSON-LD?

JSON-LD is a standard syntax for representing data properties and creating links between them using JavaScript Object Notation (JSON). The LD refers to “Linked Data.”

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