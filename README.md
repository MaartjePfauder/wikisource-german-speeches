# wikisource-german-speeches

## German Speeches Corpus — Web Scraping Assignment

### Overview

This repository contains the materials for my web-scraping assignment, in which I created a small text corpus from German speeches hosted on Wikisource.
All speeches were sourced from: https://en.wikisource.org/wiki/Category:German_speeches

The goal was to select a website, inspect its HTML structure, scrape text data using requests and BeautifulSoup, clean the text using regular expressions, extract metadata, and save the results in a CSV corpus.

### Corpus Description

The corpus consists of speeches listed in the Wikisource German speeches category.
For each speech, the dataset includes:

* title — the title as listed on the category page
* date — year or date extracted from the title using regex
* url — link to the original Wikisource page
* text — the cleaned speech content (main corpus column)

All entries are stored in german_speeches.csv.

### Data Extraction Process

#### 1. Inspecting the HTML
From viewing the page source, I identified the relevant elements:
- Speech links appear inside `<div id="mw-pages"> … <li><a>…</a></li> … </div>`
- Speech text is located under `<div class="mw-parser-output"><p>…</p></div>`

#### 2. Scraping
I used:
- requests to download pages
- BeautifulSoup to parse the HTML
- A loop to collect text from `<p` tags

#### 3. Cleaning (using regular expressions)

I applied regex to:
- remove citation markers such as [1] → \[\d+\]
- collapse whitespace → \s+
- extract the dates

### File Formats

german_speeches.csv contains one row per speech, with:
- text (main content column)
- metadata columns: title, date, url

scrape_wikisource_german_speeches.ipynb contains all scraping, parsing, cleaning, and saving code

### Terms & Conditions for Scraping

Before scraping, I reviewed Wikisource robots.txt and the Wikimedia Foundation Terms of Use.

robots.txt disallows scraping of backend paths (e.g., /w/, search pages) but does not restrict access to article pages or category pages, which are publicly accessible.

According to the Wikimedia Terms of Use, content may be reused as long as licensing requirements are followed (Wikisource hosts public domain and CC BY-SA material).

Because I only accessed publicly available article pages, respected rate-limits, and preserved attribution (via url and title), I can assume that this scraping activity is permitted.
