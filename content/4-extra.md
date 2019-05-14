---
title: Extra
nav: true
---

A few bonus examples to practice Refine+API skillz...

# ChronAm Demo

The [Chronicling America](https://chroniclingamerica.loc.gov/) project provides access to millions of pages of digitized historic newspapers.
It also includes a simple, open API to interact with the repository programmatically.
Unlike the IIIF which is a standard, this API is custom built into the repository system and is used by its own web pages to retrieve data.
Read the [documentation](https://chroniclingamerica.loc.gov/about/api/) to learn how to build URL queries.

To search individual pages, the recipe is:

- Base: `https://chroniclingamerica.loc.gov`
- Service location: `/search/pages/results`
- Query string: using the [search parameters](https://chroniclingamerica.loc.gov/search/pages/opensearch.xml) and selecting a format, `?key=value&key=value&format=json`

Let's say we want to see what was in the news this week in Idaho 100 years ago.
Build up the query string key+value pairs, similar to how you would build an "advanced search":

- From Idaho: `state=Idaho`
- From date range 05/13/1919 to 05/19/1919 (requires escaping): `dateFilterType=range&date1=05%2F13%2F1919&date2=05%2F19%2F1919`
- View only the front pages: `sequence=1`
- In JSON format: `format=json`

Combine all the parameters with `&` and to get:

`https://chroniclingamerica.loc.gov/search/pages/results?state=Idaho&dateFilterType=range&date1=05%2F13%2F1919&date2=05%2F19%2F1919&sequence=1&format=json`

Now use that link to start a new Refine project.
Steps:

- Click "Open" button in upper right. This creates a new tab, any other open projects remain open and are always saved.
- Create Project > Web Addresses (URLs)
- Paste in the API URL, click next
- JSON pasting options, select item block

Now you have a full text data set of the front pages of Idaho news papers this week 100 years ago!

# Text Processing API

[Text-processing.com](http://text-processing.com/) provides some basic natural language processing APIs designed for learning that are available without a key.
The APIs are based on Python [NLTK](https://www.nltk.org/) (see the [NLTK book](http://www.nltk.org/book/) for a great introduction to NLP and programming).

Like many API services used to enhance data, such as geocoding or named entity recognition, Text-processing uses [HTTP POST](https://en.wikipedia.org/wiki/POST_(HTTP)) to transfer information to the server for processing.
A POST can be significantly more complex than GET, since it allows any amount of data to be attached to the body of the request.
This is also more secure than GET, since the information is encrypted in the message, rather than appended to the URL.

However, since this is not just a URL, to use this type of API we will have to create POST requests using a programming language, such as Python.
Luckily, OpenRefine has Python built in! 

Let's start another new project, get some text data, parse it, and use the API to test the [Sentiment Analysis service](http://text-processing.com/docs/sentiment.html).

Start Aladore data project:

- Click "Open" button in upper right
- Create Project > Web Addresses (URLs)
- Paste in `https://evanwill.github.io/aladore-book/data/newbolt_aladore_1914.csv`, web accessible CSV data from [aladore-book](https://evanwill.github.io/aladore-book/)
- Remove front matter rows using Star
- Split/chunk chapters into individual sentences:
    - On "chapter_text" column > Edit cells > Split multi-valued cells
    - Use separator `[\.\!\?]` with regular expression box checked (this splits on `.`, `!`, or `?`, which should match the end of all sentences in the book)
    - On "chapter_text" column > Edit cells > Common transformations > Trim leading and trailing white space
    - On "chapter_number" column > Edit cells > Fill down
- Check line lengths:
    - On "chapter_text" column > Add column based on
    - Name new column "length"
    - Calculate character length using GREL, `value.length()`
    - Explore numeric facet

This sets up a project where we can start exploring the text as a collection of lines. 
Lets explore how the text represents "dog"

Sentiment analysis API:

- On "chapter_text" column, text filter on `dog` (or `shepherdess`, something to subset down to a handful of records)
- On "chapter_text" column > Add column based on 
- Name new column "dog_sentiment"
- Check "store error"
- In the "Language" drop down, select "Python / Jython"
- Paste in Python POST request script:

```
import urllib2
url = "http://text-processing.com/api/sentiment/"
data = "text=" + value
post = urllib2.urlopen(url, data)
return post.read()
```

This POST request sends our text data to the Text-processing API which returns JSON data. We could parse this data using further functions, such as `value.parseJson()["probability"]["neg"]`.

{% include alert.md text='Sentiment analysis is an NLP method used to predict the subjective mood of text.
The model must be trained on existing annotated data, in this case online movie reviews which are an easy source of "labeled" data, and will provide probabilities the text would be categorized with various sentiments.
It will be most accurate for text that is similar to the training data, i.e. small chunks of modern English, *like a movie review*.' color="secondary" %}
