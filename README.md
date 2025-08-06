# Website Summarizer

A simple Python module and Jupyter Notebook for scraping website content and generating summaries using the OpenAI API.

## Features

* Fetches and parses HTML content from any public website
* Extracts page title and visible text
* Generates AI-powered summaries via OpenAI's API
* Provides a helper function to render summaries in Jupyter Notebooks

## Requirements

* Python 3.8 or higher
* [requests](https://pypi.org/project/requests/)
* [beautifulsoup4](https://pypi.org/project/beautifulsoup4/)
* [python-dotenv](https://pypi.org/project/python-dotenv/)
* [openai](https://pypi.org/project/openai/)
* [ipython](https://pypi.org/project/ipython/)

## Installation

1. Clone the repository or download the files.
2. Create and activate a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate   # macOS/Linux
   venv\Scripts\activate    # Windows
   ```
3. Install dependencies:

   ```bash
   pip install requests beautifulsoup4 python-dotenv openai ipython
   ```
4. Create a `.env` file in the project root with your OpenAI API key:

   ```dotenv
   OPENAI_API_KEY=sk-proj-yourkeyhere
   ```

## Usage

### 1. Initialize environment and client

```python
from dotenv import load_dotenv
from openai import OpenAI
import os

load_dotenv(override=True)
openai = OpenAI()
```

### 2. Scrape a website

```python
from scraper import Website

site = Website("https://edwarddonner.com")
print("Title:", site.title)
print(site.text[:200], "...")  # Preview first 200 characters
```

### 3. Generate and display AI summary

```python
from scraper import summarize, display_summary

# Get raw summary string
summary_text = summarize("https://edwarddonner.com")
print(summary_text)

# Or render nicely in a Jupyter Notebook
display_summary("https://edwarddonner.com")
```

## File Structure

* `scraper.py` – Defines `Website`, `summarize`, and `display_summary` functions.
* `notebook.ipynb` – Example notebook demonstrating step-by-step use.
* `.env` – Stores `OPENAI_API_KEY` (not checked into version control).
* `requirements.txt` – Pin your dependencies here (optional).

## Troubleshooting

* **`NameError` for missing imports**: Ensure you've run `from dotenv import load_dotenv`, `import requests`, and `from bs4 import BeautifulSoup` before using those names.
* **Notebook package issues**: Use `%pip install ...` inside notebooks and restart the kernel after installations.
* **API key errors**: Confirm `.env` is in the correct directory and `OPENAI_API_KEY` is spelled correctly.

## Contributing

Contributions, issues, and feature requests are welcome! Please fork the repo and submit a pull request.

## License

This project is licensed under the MIT License. Feel free to use and modify as needed.
