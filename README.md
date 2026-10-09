# Uzbek NLP Data Pipeline: Low-Resource Language Scraper

## Project Overview
This repository contains the foundational data engineering pipeline for a larger natural language processing (NLP) project focused on the Uzbek language. Because major AI models are heavily biased toward high-resource languages, this project aims to build a custom dataset from local news sources to eventually train a morphological analyzer and text classifier.

## The Problem
Uzbek is an agglutinative, low-resource language. Training effective AI models requires clean, normalized data, which is not readily available in massive open-source datasets. This scraper automates the collection of raw, localized text data to build that necessary corpus from scratch.

## Technologies Used
* **Python 3**
* **BeautifulSoup 4** (HTML parsing and DOM traversal)
* **Requests** (HTTP network requests)
* **JSON** (Data structuring and export)

## Pipeline Architecture
1. **Targeting:** The script sends header-authenticated GET requests to regional news platforms to retrieve raw HTML.
2. **Extraction:** It parses the DOM to isolate the `<p>` tags containing the core article text, stripping away navigation menus, advertisements, and irrelevant code.
3. **Exporting:** The cleaned text is mapped to its source URL and exported as a UTF-8 encoded `.json` file, safely preserving specific Uzbek typographic characters (like `o'` and `g'`) without encoding errors.

## Next Steps (Current Roadmap)
* **Phase 2 (Next):** Develop a Python data-cleaning pipeline to standardize the mix of Cyrillic and Latin scripts found in the raw dataset.
* **Phase 3:** Fine-tune a pre-trained multilingual foundation model (XLM-RoBERTa) using this curated dataset.
* **Phase 4:** Deploy the classification model via a lightweight web application.
