# Crawl control for websites

_Understanding disallow, noindex, and nofollow and when to use them._

## 📖 Definitions

**Disallow** is set in `/robots.txt` while `noindex` and `nofollow` are set on the `<meta>` element.

- Disallow → don’t look at it 🙈
- noindex  → don’t index it 🙊
- nofollow → don’t crawl the links on it 🚫🕷️

## ⚠️ Please be aware

These directives function as mere requests, like a sign saying “Employees must wash hands.” A user agent (crawler) needs to choose to respect these rules for them to have any effect. Conventional search engine crawlers like Googlebot, Bingbot, and DuckDuckBot do respect them. This may, or may not, be sufficient if your server is being hammered by bots.

## 🚫 Prevent crawling of parameterized URLs

Use `Disallow` in `/robots.txt` for crawl control over parameterized URLs. This can be helpful to limit the load that legitimate crawlers generate when spidering visible search results with multiple filters and facets.

Disallow Drupal pagination crawl sitewide:

	Disallow: /*?page=

Disallow query string crawl of q parameter:

	Disallow: /*?q=

Disallow any query string crawl sitewide:

	Disallow: /*?

### Prevent some URLs and allow others

To limit crawl in some cases but allow it in others, make use of specificity.

Disallow any query string crawl sitewide except for product pages:

	Allow: /product/*?
	Disallow: /*?

This works due to [order of precedence](https://developers.google.com/crawling/docs/robots-txt/robots-txt-spec#order-of-precedence-for-rules) for Googlebot.

### How to test

1. Visit the [robots.txt Validator and Testing Tool](https://technicalseo.com/tools/robots-txt/)
2. Click the Editor option
3. Paste the contents of the robots.txt file you’re testing into the editor
4. Modify it by editing/adding the new rule you want to test
5. Select a User Agent, e.g. Googlebot
6. Paste a disallowed URL into the URL field and click the Test button
7. Result should be Disallowed (red) and the rule that triggered it will be flagged
8. Paste an allowed URL into the URL field and click the Test button
9. Result should be Allowed (green)
10. Repeat as needed

### Examples in the wild

- [drupal.org/robots.txt](https://www.drupal.org/robots.txt)
- [redhat.com/robots.txt](https://www.redhat.com/robots.txt)
- [duckduckgo.com/robots.txt](https://duckduckgo.com/robots.txt)
- [google.com/robots.txt](https://www.google.com/robots.txt)
- [workday.com/robots.txt](https://www.workday.com/robots.txt)
- [wordpress.com/robots.txt](https://wordpress.com/robots.txt)
- [github.com/robots.txt](https://github.com/robots.txt)

### Further reading

- [Managing crawling of faceted navigation URLs](https://developers.google.com/search/docs/crawling-indexing/crawling-managing-faceted-navigation)
- [Robots.txt introduction and guide](https://developers.google.com/search/docs/crawling-indexing/crawling-managing-faceted-navigation)
- [Order of precedence](https://developers.google.com/crawling/docs/robots-txt/robots-txt-spec#order-of-precedence-for-rules)
- [Detailed precedence discussion](https://webmasters.stackexchange.com/a/130656)

## 🙅 Discourage crawling of links on a specific URL

Use `nofollow` in the `<meta>` element to tell crawlers not to follow the links on a page:

	<meta name="robots" content="nofollow">

This tells crawlers they can read the page but should not crawl any of the links on it.

If your use case is preventing search engines from crawling search page facets it is recommended to implement prevention of crawling faceted search URLs as well. The `nofollow` attribute is considered a *hint* rather than a *directive*, so combining it with a disallow in robots.txt sends a stronger signal discouraging crawl.

### Further reading

- [Robots meta tags specifications → nofollow](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag#nofollow)
- [Nofollow attribute](https://www.screamingfrog.co.uk/learn-seo/nofollow/#whento)

## 🛡️ Prevent a page from being indexed

Use `noindex` in the `<meta>` element to tell crawlers not to index the page or to remove it from the index if it has already been added:

	<meta name="robots" content="noindex">

This tells crawlers they can read the page but should not allow it to be indexed and served in search results.

If your use case is removing a page from search results, or preventing it from ever being included, publish the page with this metadata value and allow the page to be crawled (i.e. don’t use `nofollow` and don’t block in `/robots.txt`). If you don’t allow crawl, bots will not know that they should remove the page from the index.

### Further reading

- [Block search indexing with noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing)
- [Robots meta tags specifications → noindex](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag#noindex) 

## 🚦 Stop URL parameters only from being indexed

Use `rel="canonical"` in the `<link>` element to tell crawlers not to remember or index parameterized versions of the page:

	<link rel="canonical" href="https://www.example.com/search">

Suppose your search engine accepts keyword queries (e.g. “bananas”), has pagination, and provides a category filter for types of food such that…

1. a query for “bananas” produces a URL like: 

		https://www.example.com/search?q=bananas

2. a query for “bananas” with the Fruit filter selected produces a URL like: 

		https://www.example.com/search?q=bananas&c=fruit

3. a query for “bananas,” with Fruit filter selected, viewing the third page of results produces a URL like: 

		https://www.example.com/search?q=bananas&c=fruit&page=2

Provided each variant contains `<link rel="canonical" href="https://www.example.com/search">` in the `<head>` crawlers will know that they should only index the canonical version of the page.

Parameterized versions will not be indexed.

If your use case is removing parameterized versions of a page from search results, publish the page with the canonical element and allow the page to be crawled. If you don’t allow crawl, bots will not know that they should remove the page from the index. (Once they have been removed you can then block crawl.)

If your use case is preventing parameterized versions of a page from being indexed and they are not currently appearing in results, it’s okay to block crawl and use the canonical element as a backstop.

### Further reading

- [Canonicals](https://www.screamingfrog.co.uk/learn-seo/canonicals/)
- [How to specify a canonical with rel="canonical" and other methods](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls#best-practices)

## 💫 Putting it all together

A good mix of these techniques for most sites may include:

1. Use **`Disallow`** with wildcards in `/robots.txt` to block URL parameters that should not ever be crawled.
2. Use **`nofollow`** in the `<meta>` element on search pages to tell crawlers not to follow links on the page. If the search page includes results by default and those results contain content crawlers should know about, ensure that the content is included in sitemap.xml so that search engines can discover it.
3. If a page is appearing in results and you need to remove it, use `noindex` in the `<meta>` element on that page and allow it to be crawled.
4. Canonicalize your pages: ensure every page outputs a `rel="canonical"` in the `<link>` element such that query-string variants will always point to the unparameterized version of the URL.

This blend of signals will limit where well-intentioned crawlers go, when they stop, and what they remember.