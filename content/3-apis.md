---
title: API
nav: true
---

# Web APIs

Server-side Web Application Program Interfaces (APIs) are defined methods designed to make interaction with a server easier.
Think of them as recipes or contracts, where if you provide the expected input you will receive an expected output.
Web APIs provide an abstract way to interact with a server from the outside using a web protocol (http) to request or submit data.

{% capture plugs %}
Think about the outlets in your house.
Any device with the standard plug can be connected to the socket and receives the standardized amount of power. 
You do not need to know anything about the power generation or electrical grid that delivers it to your house (other than paying the bill). 
Likewise, the utility company doesn't need to know what you are plugging in, it just delivers the expected voltage.
This makes the interaction considerably simpler--you do not need to rig up custom wiring and voltage regulators for every device.
{% endcapture %}
{% include card.md text=plugs title="For Example..." img="rawpixel-1061399-unsplash.jpg" alt="power strip and plugs" %}

Many cultural institutions provide APIs allowing users to access information about their collections via simple HTTP requests. 
These sources enable new queries and aggregations of text that were previously impossible, cutting across boundaries of repositories and collections to support large scale analysis of both content and metadata.

{% include alert.md text='This workshop uses the term *server-side web APIs* to refer to services exposed on the web via a well documented set of HTTP requests.
However, API is a generic term that is used in many different programming contexts, generally "a set of clearly defined methods of communication among various components" ([API, Wikipedia](https://en.wikipedia.org/wiki/Application_programming_interface)).' color="secondary" %}

# GET Demo

The simplest forms of APIs use the [HTTP GET method](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods), essentially utilizing URL patterns to request information from a server.
With GET requests, your query is encoded in the URL string, thus limited in length (2048 ASCII characters), complexity, and security.

We can test using these APIs simply by constructing the URL following the recipe, then pasting it into a web browser. 
However, combining these methods with a tool such as OpenRefine or a scripting language such as Python can make them very powerful.

### Uniform Resource Locators

Understanding the URLs in your browser address bar is the first step to using this type of API. 
So let's dissect a URL:

{% include alert.md text="`https://example.com/about?key=value#anchor`" align="center" color="success" %}

protocol `://` domain `.` top-level domain (optional port :80) `/` path and filename `?` query with parameters `#` fragment or anchor

- **Protocol:** there is actually more than 100 defined Internet Protocols, however with URLs the most common are [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) or [File Transfer Protocol (FTP)](https://en.wikipedia.org/wiki/File_Transfer_Protocol).
- **Domain:** the [Domain Name System (DNS)](https://en.wikipedia.org/wiki/Domain_Name_System) is often described as a "phone book" that translates easy to understand web addresses into the appropriate [IP addresses](https://en.wikipedia.org/wiki/IP_address) of servers with the desired information. A subdomain can be added in front of the main domain. For example, in `lib.uidaho.edu` > `lib` is a subdomain of `uidaho`, which is a subdomain of the top-level domain `edu`. Occasionally, you may see a port number at the end of the domain which refer to specific communication endpoints that the server is listening on. For the web the standard ports are `:80` (http) and `:443` (https).
- **Path and filename:** these can be imagined like folders and files on the server (and actually are in static web sites). For example, `/about/index.html`, is the index file in the "about" folder. If no filename is given, by default the server provides the file named `index`.
- **Query string:** is added to the end of an URL following a `?` and is given in key value pairs. Multiple pairs can be separated by `&`. The characters must be URL encoded / escaped, since some characters such as space are not allowed in URLs. The queries are processed by the server or javascript, so what exactly they do depends on the page. For example, `/index.php?title=Query_string&action=edit` might return a wiki article in edit mode.
- **Anchor:** are added to the end of a URL following a `#`. They traditionally correspond to specific `id` on an html page, but are often used by javascript to add other functionality. For example, `/index.html#Chapter1` might jump to a chapter heading in the web page.

### IIIF

[International Image Interoperability Framework (IIIF)](https://iiif.io/) is an effort to standardize methods to access images and annotations from repositories.
The API standard was created by a collaborative community so that software developers can create compliant viewers and image servers, enabling better user and developer experiences across many platforms.

IIIF URI syntax looks like:

`{scheme}://{server}{/prefix}/{identifier}/{region}/{size}/{rotation}/{quality}.{format}`

Each parameter has standard options or syntax, gradually building up the exact specifications of the image you want.

Using the [IIIF Image API](https://iiif.io/api/image/2.1/), let's create an image download link for objects in our `potlatch-historical-collection.csv` demo project, which are hosted in the University of Idaho Library's [PHS collection](https://digital.lib.uidaho.edu/digital/collection/phs/search) on the [CONTENTdm](https://www.oclc.org/en/contentdm.html) platform.

Parts of the recipe:

- Server: our IIIF service is at the base URL `https://cdm17254.contentdm.oclc.org/digital/iiif`
- Prefix: the collection name `/phs`
- Identifier: the "CONTENTdm number" column found in our metadata
- Region: `full` to get the complete image
- Size: `max` to get largest size available
- Rotation: `0` to not rotate
- Quality: `default` to get the regular color image
- Format: `.jpg` to get a JPEG image

Steps:

- Subset using facet on "Format Digital" to only items that are images
- On "CONTENTdm number" column: Edit column > Add column based on this column
- Name new column "IIIF_link"
- Follow the API recipe to construct the new link using GREL, `"https://cdm17254.contentdm.oclc.org/digital/iiif/phs/" + value + "/full/max/0/default.jpg"`
- Test links by clicking

### DBpedia API

APIs also offer opportunities to enrich your data or connect with other sources. 
[DBpedia Spotlight](https://www.dbpedia-spotlight.org/) is a web service to annotate text with linked open data entries from [DBpedia](https://wiki.dbpedia.org/about).
For example, let's say we want to extract entities from this text and link them to DBpedia: "Moscow, Idaho is located in the Palouse near Pullman, Washington."
First, try pasting the GET URL into your browser to see how it works:

`https://api.dbpedia-spotlight.org/en/annotate?text=Moscow, Idaho is located in the Palouse near Pullman, Washington.`

The API has returned an HTML page, because the request came from a browser it assumes we want it in that form.
However, we may need another machine-readable format. 
The API will return `application/json`, `text/xml`, or `application/xhtml+xml` if we pass it as the `Accept` header in our request.

Parts of the recipe:

- Base: `https://api.dbpedia-spotlight.org/en/annotate`
- Key: `?text=`
- Value: the text we want annotated, escaped for URL
- Headers: `Accept:application/json`

Steps:

- Subset on "Description" using text filter on `icicles` (just to get us to down to a handful of items)
- On "Description" column: Edit column > Add column based on this column
- Name new column "dbpedia_link"
- Follow the recipe to construct the new link, `"https://api.dbpedia-spotlight.org/en/annotate?text=" + value.escape('url')`
- On "dbpedia_link" column: Edit column > Add column by fetching URLs
- Name new column "dbpedia_entities"
- Throttle delay less
- Click on "HTTP headers", add `application/json` in "Accept" field.
- Click okay, wait for harvest to complete!
- Inspect the resulting JSON, parse with `parseJson()`?
