- Overview of collections as data
- Introduce OpenRefine:
    - [About Refine](https://evanwill.github.io/clean-your-data/1-about.html)
    - [Messy data](https://evanwill.github.io/clean-your-data/2-messy.html)
    - [Install](https://evanwill.github.io/clean-your-data/3-start.html)
- Introduce APIs:
    - [Intro](https://evanwill.github.io/hey-api/content/0-intro.html)
    - [URLs](https://evanwill.github.io/hey-api/content/1-urls.html)
    - Chronam with [GET](https://evanwill.github.io/hey-api/content/2-get.html)
- OpenRefine + APIs

-------------

contentdm: 

- search
- get item metadata


chronam: 

https://chroniclingamerica.loc.gov/search/pages/results/?state=Idaho&dateFilterType=range&date1=05%2F13%2F1919&date2=05%2F17%2F1919&sequence=1&rows=20&format=json

paste into refine import url 
parse json option

- join multi-valued subject
- throw out extra rows
- throw out extra columns
- fix date

-------

refine fetch accept headers
https://github.com/LibraryOfCongress/data-exploration/blob/master/ChronAm%20API%20Samples.ipynb
https://libraryofcongress.github.io/data-exploration/requests.html

https://evanwill.github.io/_drafts/notes/open-refine-metadata.html

cdm api, `/bl/dmwebservices/`
https://www.oclc.org/support/services/contentdm/help/customizing-website-help/other-customizations/contentdm-api-reference.en.html
