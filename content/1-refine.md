---
title: Refine
nav: true
---

# What is OpenRefine?

{% include figure.html img="refine.jpg" alt="openrefine interface" %}

OpenRefine is a [free](https://www.gnu.org/philosophy/free-sw.en.html){:target="_blank"}, [open source](https://github.com/OpenRefine/OpenRefine){:target="_blank"}, Java application, that runs offline in a web browser. 

{% capture text %}
The original creator [David Huynh](http://web.archive.org/web/20141021040915/http://davidhuynh.net/spaces/nicar2011/tutorial.pdf){:target="_blank"} said Refine is:

#### "A power tool for working with messy data"

- more powerful than a spreadsheet
- more interactive and visual than scripting
- more provisional / exploratory / experimental / playful than a database
{% endcapture %}
{% include card.md text=text %}

## Tabular Data 

Refine can handle all sorts of data from all sorts of sources:

- **Import formats:** TSV, CSV, custom separator, Excel, ODF spreadsheet, XML, JSON, RDF, Google Sheets, MARC...
- **Import sources:** local file, archive (zip), URL, clipboard, database, or Google Sheets
- **Output formats:** TSV, CSV, HTML, Excel, ODF spreadsheet, SQL, Wikidata, RDF schema, or custom template

Once imported, the data is represented as tabular, using this basic terminology: 

{% include figure.html img="table.png" alt="table parts" width="100%" %}

Refine is efficient enough to provide comfortable performance up to 100,000's of rows (although, you may want to [increase memory allocated to Java](https://github.com/OpenRefine/OpenRefine/wiki/FAQ:-Allocate-More-Memory){:target="_blank"}).

{% capture usecase %}
**Explore** - navigate and evaluate quality with visualizations and filters that help dig deeply into the data so you can get to know it better...

**Clean** - efficiently discover and fix inconsistency with faceting, clustering, cell transforms, GREL expressions...

**Transform** - easily change formats, subset, or reshape with split/join multi valued cells, split columns, transpose columns/rows...

**Extend** - enrich data by combining files, merging projects, fetching URLs, reconciliation with online databases...

**Automate** - record and preserve your processing routine for transparency, then automate reuse by exporting operation history in JSON!
{% endcapture %}
{% include card.md text=usecase header="Use Cases" %}

## Messy Data?

Inconsistent formats, unnecessary white space, extra characters, typos, etc... 
Messy data is the bane of analysis! 
Each column contains exactly the same info:

| 2015-10-14 | $1,000 | ID |
| 10/14/2015 | 1000 | I.D. |
| 10/14/15 | 1,000 | US-ID |
| Oct 14, 2015 | 1000 dollars | idaho |
| Wed, Oct 14th | US$1000 | Idaho, |
| 42291 | $1k | Ihaho |

Multi-valued cells limit ability to manipulate, clean, and use the data:

| “Using OpenRefine by Ruben Verborgh and Max De Wilde, September 2013” | | |
| "University of Idaho, 875 Perimeter Drive, Moscow, ID, 83844, p. 208-885-6111, info@uidaho.edu" | | |

Luckily, Refine provides powerful visualizations and tools to discover these types of data issues, then isolate and fix them.
