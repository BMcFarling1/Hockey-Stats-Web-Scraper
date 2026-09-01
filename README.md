# Hockey Data Scraper & Aggregator (C++ / libcurl)

A fast, lightweight C++ web scraping application that queries paginated historical NHL statistics (1990–2011) via HTTP requests, parses raw HTML streams, cleans string records, and exports formatted CSV data for statistical analysis.

## Overview

This tool automates multi-page data extraction from `scrapethissite.com` without relying on high-level Python libraries (like BeautifulSoup or Scrapy). Built natively in C++, it handles HTTP lifecycle management, dynamically parses table cells, strips whitespace formatting errors, and outputs clean structured datasets.

## Key Technical Features

* **HTTP Session Management:** Utilizes `libcurl` to handle network calls and buffer streams across 24 paginated endpoints cleanly.
* **Custom HTML Parsing Logic:** Implements manual substring matching (`std::string::find`) to isolate table rows (`<tr>`) and target data cells (`<td>`) without extra overhead.
* **Edge-Case & Dynamic Style Handling:** Detects variations in CSS classes (e.g., dynamic conditional classes like `.text-danger` vs `.text-success` for team differentials and win percentages).
* **Data Sanitization:** Trims leading/trailing whitespace, newline characters, and HTML formatting bugs using C++ standard algorithms before file IO.
* **File I/O Stream:** Generates a structured output file (`hockey_data.txt`) formatted for downstream data parsing or relational database insertion.

## Prerequisites & Dependencies

* **C++ Compiler:** Supporting C++11 or higher (`g++` / `clang++`)
* **libcurl Development Library:**
  * Ubuntu/Debian: `sudo apt-get install libcurl4-openssl-dev`
  * macOS: `brew install curl`

## Build and Execution

## Output Format
Team Name, Year, Wins, Losses, Win Pct, Goals For (GF), Goals Against (GA), Goal Differential

Compile the code with `libcurl` linked:

```bash
g++ -std=c++11 -o hockey_scraper main.cpp -lcurl
./hockey_scraper
