# Crawl control for websites

_Understanding disallow, noindex, and nofollow and when to use them._

## Definitions 📖

**Disallow** is set in `/robots.txt` while `noindex` and `nofollow` are set on the `<meta>` element.

- Disallow → don’t look at it 🙈
- noindex  → don’t index it 🙊
- nofollow → don’t crawl the external links on it 🚫🕷️

## Please be aware ⚠️

These directives function as mere requests, like a sign saying “Employees must wash hands.” A user agent (crawler) needs to choose to respect these rules for them to have any effect. Conventional search engine crawlers like Googlebot, Bingbot, and DuckDuckBot do respect them. This may, or may not, be sufficient if your server is being hammered by bots.

## Prevent crawling of parameterized URLs 🚫

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

## Discourage crawling external links on a specific URL 🙅

Use `nofollow` in the `<meta>` element to tell crawlers not to follow the links on a page:

	<meta name="robots" content="nofollow">

This tells crawlers they can read the page but should not crawl any of the external links on it. This functions as a hint (rather than a directive) that you do not vouch for those outbound links.

This value can also be implemented as an attribute on specific links:

	<a href="https://www.example.com/" rel="nofollow">some external site</a>

⚠️ **Note:** If your use case is preventing search engines from crawling search page facets use `Disallow` rules in `/robots.txt` to prevent crawl of faceted URLs. The `nofollow` option applied to internal content does not achieve the same result as `Disallow`. Google advises that the `nofollow` attribute is for [discouraging crawl of external links](https://developers.google.com/search/docs/crawling-indexing/qualify-outbound-links#nofollow).

### Further reading

- [Robots meta tags specifications → nofollow](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag#nofollow)
- [Nofollow attribute](https://www.screamingfrog.co.uk/learn-seo/nofollow/#whento)

## Prevent a page from being indexed 🛡️

Use `noindex` in the `<meta>` element to tell crawlers not to index the page or to remove it from the index if it has already been added:

	<meta name="robots" content="noindex">

This tells crawlers they can read the page but should not allow it to be indexed and served in search results.

⚠️ **Note:** If your use case is removing a page from search results, or preventing it from ever being included, publish the page with this metadata value and allow the page to be crawled (i.e. don’t use `nofollow` and don’t block in `/robots.txt`). If you don’t allow crawl, bots will not know that they should remove the page from the index.

### Further reading

- [Block search indexing with noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing)
- [Robots meta tags specifications → noindex](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag#noindex) 
- [Qualify your outbound links to Google](https://developers.google.com/search/docs/crawling-indexing/qualify-outbound-links#nofollow)

## Use canonicals to manage duplicate content 🚦

**Note:** Canonicalization may affect crawl indirectly by sending a signal to ignore the pages that canonicalize elsewhere.

Use `rel="canonical"` in the `<link>` element to tell crawlers which version of a duplicated page you consider to be primary:

	<link rel="canonical" href="https://www.example.com/category/thing.html">

Ideally if you find two versions of a page you decide which one to retire and redirect it to the one you want to keep. But this isn’t always possible and sometimes you have to deal with multiple cases of the same content.

A common scenario is when tracking information is copied into a website’s content editor, such as a link on the homepage that points to: 

	https://www.example.com/category/thing.html?utm_medium=email&utm_source=marketingplatform&utm_campaign=spring2026

If a search engine crawls the homepage it may treat the above URL as an entirely different page from the one that your navigation points to, which is: 

	https://www.example.com/category/thing.html

This is where `rel="canonical"` can help. Adding:

	<link rel="canonical" href="https://www.example.com/category/thing.html">

to the `<head>` of the destination page (a “self-referential” link) will let crawlers know that the publisher considers `https://www.example.com/category/thing.html` to be the canonical version of the page.

Google’s short video [Canonicalization SEO Mythbusting](https://www.youtube.com/watch?v=gEWkYTPSEjs) explains some common misconceptions.

### Pagination

In sum, pages that are part of a paginated series should self-canonicalize.

Screaming Frog [recommends](https://www.screamingfrog.co.uk/learn-seo/canonicals/#bestpractices) that parameterized pagination URLs for content like products or articles *not be canonicalized* to the first page in the series because it may reduce the likelihood that Google will pass Pagerank to the pages in the listing.

Google also [advises using unique canonical URLs for paginated content](https://developers.google.com/search/docs/specialty/ecommerce/pagination-and-incremental-page-loading#use-urls-correctly).

A paginated sequence would ideally include unique URLs in the canonical element…

	<!-- on page 1 of /articles -->
	<link rel="canonical" href="https://www.example.com/articles">
	
	<!-- on page 2 of /articles -->
	<link rel="canonical" href="https://www.example.com/articles?page=1">
	
	<!-- on page 3 of /articles -->
	<link rel="canonical" href="https://www.example.com/articles?page=2">

	<!-- on page 4 of /articles, etc. -->
	<link rel="canonical" href="https://www.example.com/articles?page=3">

…while the pages enumerated by the listing also appear in your site’s sitemap.xml. This enables discovery via both full site crawl and sitemap.xml.

### Canonicalization and site search

In short: 

1. Self-canonicalize search result pages regardless of their query strings, e.g.
	
		<!-- on /search?query=bananas&category=fruit&page=2 -->
		<link rel="canonical" href="https://www.example.com/search?query=bananas&category=fruit&page=2">

2. Use `noindex` on search result pages to prevent them from appearing in external search engines, e.g. 
		
		<!-- on /search, /search?query=bananas, etc. -->
		<meta name="robots" content="noindex">

3. Optional: If you want or need to block crawl of search results, use an appropriate `Disallow` rule in `/robots.txt`, e.g. 

		Disallow: /search?

### Further reading

- [Canonicals](https://www.screamingfrog.co.uk/learn-seo/canonicals/) by Screaming Frog
- [How to specify a canonical with rel="canonical" and other methods](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls#best-practices)
- [Pagination — use URLs correctly](https://developers.google.com/search/docs/specialty/ecommerce/pagination-and-incremental-page-loading#use-urls-correctly)

## Putting it all together 💫

A good mix of these techniques for most sites may include:

1. Use **`Disallow`** with wildcards in `/robots.txt` to block URL parameters that should not ever be crawled.
2. Use **`nofollow`** in the `<meta>` element on pages to tell crawlers not to follow external links on the page.
3. If a page is appearing in results and you need to remove it, use `noindex` in the `<meta>` element on that page and *allow it to be crawled*.
4. Canonicalize your pages: ensure every page outputs a `rel="canonical"` in the `<link>` including query strings that change the content displayed. Omit query strings that don’t change the content displayed.

This blend of signals will limit where well-intentioned crawlers go, when they stop, and what they remember.