# BBC Most Popular News Scrapper

Build a console application that scrapes the [BBC news homepage](http://www.bbc.co.uk/news/)
and returns a JSON array of the most popular shared articles table.

Only the Shared section is to be scraped.
Additionally you need to follow each link and get the size of the linked HTML (no assets) and
the word (from the article) with the highest number of usages (excluding the, a, is, and or I)

Each element in the JSON array should container ‘href’, ‘title’, ‘size’ and ‘most_used_word’
keys corresponding with the most popular shared list.

Example JSON:
```javascript
{
    "results": [
        {
            "title":"Thousands join central London protest",
            "href":"http://www.bbc.co.uk/news/uk-england-london-29919083",
            "size": "90.6kb",
            "most_used_word": "dog"
        },
        {
            "title":"Doughnut burger busts day's calories",
            "href":"http://www.bbc.co.uk/news/health-30000934",
            "size": "87kb",
            "most_used_word": "burger"
        }
    ]
}
```
