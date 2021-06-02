### META INFORMATION
Meta data and the majority of main content should be rendered server side.

### PRIORITY META TAGS

The variable values here (`${value}`) should be unique to each page and rendered server side whenever possible. For our purposes, og tags and twitter tags shown adopt the same title values from the basic SEO tags at top.

```
<title>`${pageTitle}`</title>
<meta name="description content="`${metaDesc}`">
<link rel="canonical" href="`${canonicalUrl}`">
<meta name="robots" content="`${seoRobots}`">
<meta name="viewport" content="width=device-width, initial-scale=1">

<meta property="og:title" content="`${pageTitle}`">
<meta property="og:description" content="`${metaDesc}`">
<meta property="og:type" content="`${ogType}`">
<meta property="og:url" content="`${canonicalUrl}`">
<meta property="og:site_name" content="`${ogSiteName}`">
<meta property="og:image" content="`${ogImage}`">

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="`${twitterSite}`">
<meta name="twitter:title" content="`${pageTitle}`">
<meta name="twitter:description" content="`${metaDesc}`">
<meta name="twitter:image" content="`${twitterImage}`">
<meta name="twitter:image:alt" content"`${twitterImageAlt}`">
```

- `${pageTitle}` = max 60 characters, unique to page, including relevant keyword placement for the page
- `${metaDesc}` = max 155 characters, unique to page, including relevant keyword placement for the page
- `${canonicalUrl}` = full absolute URL of page, including https protocol and subdomain, excluding any parameters appended to requested URL variations, all lowercase
- `${seoRobots}` = noindex and nofollow directives as inheritied from CMS page properties; this tag is absent by default unless overridden by CMS
- `${ogType}` = "article" for posts/articles or "website" for homepage or section/category pages
- `${ogSiteName}` = domain without subdomain, lowercase
- `${ogImage}` = absolute url for main art image, should be at best 1080 pixels width
- `${twitterSite}` = official twitter handle preceded by "@" symbol
- `${twitterImage}` = twitter:image, URL to main image, minimum 144x144 max 4096x4096pixels
- `${twitterImageAlt}` = value same as alt attribute of main image, if available, 420 characters max

#### Notes/reference:

Please note open graph's basic metadata implementation includes a prefix="og: http://ogp.me/ns#" on the html tag.

- [Facebook sharing debugger for og tags](https://developers.facebook.com/tools/debug/sharing/)

- [Facebook sharing dev best practices](https://developers.facebook.com/docs/sharing/best-practices/)

- [Twitter cards dev overview](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/summary)

- [Twitter cards dev overview, large image](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/summary-card-with-large-image)

- [Twitter card validator](https://cards-dev.twitter.com/validator)


### STRUCTURED DATA/SCHEMA

Structured data/schema should be implemented where appropriate using JSON-ld, not Microdata.

Structured data/schema should be delivered server side where possible and placed within a `<script type="application/ld+json"></script>` tag within the `<head>` of the page. Easily locate a page's markup by finding `ld+json` in devtools.

Embedding multiple types on a page, if appropriate, can be added as an array via the `@graph` property and tested for no errors, although it's less documented. Example:
```
<script type="application/ld+json">
{
    "@context":"http://schema.org",
    "@graph":[
        {
            "@context":"http://schema.org","@type":"ReportageNewsArticle",
            [...]
        },
        {
            "@context":"http://schema.org","@type":"AnotherExample",
            [...]
        }
    ]
}
</script>
```

Tools/References if needed:

- [General Google guidelines for structured data/schema usage](https://developers.google.com/search/docs/guides/sd-policies)

- Specific schema types of interest and supported by Google:
  - [Article](https://developers.google.com/search/docs/data-types/article); see [Schema.org's more specific subtypes](https://schema.org/NewsArticle) if validating correct usage of ReportageNewsArticle or other subtypes as necessary
  - [Breadcrumb](https://developers.google.com/search/docs/data-types/breadcrumb)
  - [Event](https://developers.google.com/search/docs/data-types/event)
  - [Logo](https://developers.google.com/search/docs/data-types/logo)
  - [Product](https://developers.google.com/search/docs/data-types/product)
  - [Recipe](https://developers.google.com/search/docs/data-types/recipe)
  - [Review snippet](https://developers.google.com/search/docs/data-types/review-snippet)
  - [Subscription and paywalled content](https://developers.google.com/search/docs/data-types/paywalled-content)
- [Google Structured Data Testing Tool, must show no errors](https://search.google.com/structured-data/testing-tool), officially migrating to schema.org [here](https://validator.schema.org/)


#### OTHER ON-PAGE CONSIDERATIONS
- use a single h1 tag for the main header on a page, descriptive of content; use structured h2 and h3 tags for other onpage headers as needed
- duplicate title and description tags across different URLs should be avoided; all should be unique
- img tags should include an alt attribute that is unique and descriptive of the visual content