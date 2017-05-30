# Feed Reference Resource

## Department of Medicine V2

- Feed Burner
- http://feeds.feedburner.com/EDPCardiology
- xmlns:feedburner

### Attributes

wrap in `<item>`:
	
- title
- link
- description: some has `<!CDATA` inside. Has `<a>` inside. Need to be parsed to valid code 
- content:encoded: same requirement as above
- img (some have): <content:encoded> => `<img>`. Take `src` attribute. (Special Case: How to Solve this problem?)

## ACTSI - Type1


- XML generated based on index block, publishing to cascade
- http://actsi.org/php/newsletters.xml
- Starting from `<system-data-structure definition-path="Newsletter Layout V2">`. Since it is a xml display page, almost all fields need to be treated so no illegal character will show (Any mark for a page xml? Any solution?)

### Attributes

Item has to be decided based on special tag (no certain where to start):

`<section>` -> check `header` and `input-type`
	
Under `<article>`:

items are aligned by `<page-layout>/<columns>`

search through `<column>` (`<column-1>`, `<column-2>`, `<column-3>`): `<row> - <row-block> -> <system-data-strcture> -> <news-article>`:

- `<article-title>`
- `<article-image> -> <path>`
- `<article-copy>`: include multiple paragraphs with `<a>` inside. Need character escape
- `<external-url>`
	
	
## ACTSI - Type2

- FeedBurner
- http://feeds.feedburner.com/Dom-education-rss
- Not following structure above, but need to use same JavaScript for render. Need treatment for this kind of problem

### Attributes

Same structure as all feedburner one (Create special case for feedburner?). All information under `<item>`:

- title
- link
- description: has illegal character -> Need special treatment
- No image

## Alumni(Emory Wire)

- http://www.alumni.emory.edu/emorywire/feed.rss
- Need to burn to feedburner for Vineup

### Attributes

wrap in `<item>`:
	
- title
- link
- description/content with `<![CDATA]>`
- may use: `<media: thumbnail>`	

## Candler

- 25livepub
- http://25livepub.collegenet.com/calendars/th_admissions_cal.rss

### Attributes

wrap in `<item>`:
	
- title
- link
- description

## Conclusion

### Feed Burner

Standard Way.

wrap in `<item>`:
	
- title
- link
- description: some has `<!CDATA` inside. Has `<a>` inside. Need to be parsed to valid code 

Need treatment for image:

Some fees do not have images. 

### Index Block from Cascade Server

Non-standard Way.

- Organization of block depends on page structure (read directly from cascade page)
- Is there any way to regular way of generating index block?
- Hard to find common way of retrieving information

### Other Standard Resources (25live, trumba...)

Standard Way.

wrap in `<item>`:
	
- title
- link
- other information

### Common Problems

- Character escape

- Process of calling from front-end (Common get-request.php? Simple AJAX call?)

- Possible placeholder inside cascade (most of url above has CORS problem inside cascade server)