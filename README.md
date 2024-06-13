# Actor - Eksi Sozluk Scraper
Ekşi Sözlük, a vibrant community-driven platform, lacks a robust and freely accessible API. To bridge this gap, we present the Ekşi Sözlük Scraper, designed to facilitate seamless data extraction and analysis from this popular Turkish platform.


- **Flexible Keyword Search**: Effortlessly search for any keyword and retrieve relevant entries. Refine your search with options like author name, specific date ranges, and sorting orders to pinpoint the information you need.

- **User-Centric Scraping**: Dive deep into users' contributions by scraping entries made by specific individuals, gaining insights into their perspectives and contributions.

- **Entry and Topic Scraping**: Fetch content from specific entries or gather entries related to specific topics or issues, enabling comprehensive research and analysis.

- **Customizable Search Parameters**: Tailor your search with parameters such as start date, end date, nice-only entries, and search sort order for a personalized scraping experience.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex-support/eksisozluk-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Eksi Sozluk that should be visited. Required fields are:

- `startUrls`: (Optional) (Array) List of Eksi Sozluk URLs. You should only provide a topics, issues, users or entries URLs.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `searchKeyword`: (Optional) (String) Keyword that you want to search on Eksi Sozluk.

- `searchAuthor`: (Optional) (String) Keyword that you want to search by author name on Eksi Sozluk.

- `searchStartDate`: (Optional) (String) The start date you can type when you want to search any date range on Eksi Sozluk.

- `searchEndDate`: (Optional) (String) The end date you can type when you want to search any date range on Eksi Sozluk.

- `isSearchNiceOnly`: (Optional) (Boolean) If you want to search nice only, you can set ```true```. Default setting is ```false```.

- `searchSortOrder`: (Optional) (String) The search sort order you can type when you want to sort the results. The default setting is ```Date```.

    * ```Date```: Sorts from new to old.
    * ```Count```: Sorts from most to least.
    * ```Topic```: Sorts alphabetically.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detailed requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.01-0.15 compute units.

### Eksi Sozluk Scraper Input example

```json
{
    "startUrls": [
        "https://eksisozluk.com/biri/elmyra",
        "https://eksisozluk.com/basliklar/gundem",
        "https://eksisozluk.com/istanbul--32102",
        "https://eksisozluk.com/entry/21381787"
    ],
    "maxItems": 20,
    "searchKeyword": "eksi",
    "searchAuthor": "ssg",
    "searchStartDate": "26-07-2013",
    "searchEndDate": "30-07-2013",
    "isSearchNiceOnly": true,
    "searchSortOrder": "Date",
    "proxy":{
        "useApifyProxy": true
    }
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Eksi Sozluk Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Eksi Sozluk actor.

## Scraped Eksi Sozluk Properties

The structure of each item in Eksi Sozluk looks like this:

### Item Detail

```json
{
	"type": "entry",
	"issueUrl": "https:/www.eksisozluk.com/eksi-sozluk-hakkindaki-akademik-calismalar--2131734",
	"entryId": "110286085",
	"authorId": "8097",
	"authorName": "ssg",
	"authorUrl": "https:/www.eksisozluk.com/biri/ssg",
	"authorAvatar": "https://img.ekstat.com/profiles/ssg-638271629469815122.jpg",
	"issueTitle": "ekşi sözlük hakkındaki akademik çalışmalar",
	"entryUrl": "https:/www.eksisozluk.com/entry/110286085",
	"content": "web-based macroseismic intensity study in turkey: entries in ekşi sözlük, deniz ertuncay, laura cataldi, and giovanni costa, 2020 <a rel=\"nofollow noopener\" class=\"url\" target=\"_blank\" href=\"https://gc.copernicus.org/preprints/gc-2020-31/\">https://gc.copernicus.org/preprints/gc-2020-31/</a>",
	"date": "16.07.2020 21:19",
	"favoriteCount": "17"
}
```

## Contact

Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
