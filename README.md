# Brochure Generator

An AI-powered tool that automatically generates a professional company brochure by scraping a website and using OpenAI's GPT model to summarize relevant content for prospective clients, investors, and recruits.

## What it does

1. Takes a company name and website URL as input
2. Scrapes the website and extracts all links
3. Uses GPT to identify relevant pages (About, Careers, Company pages)
4. Fetches content from those relevant pages
5. Generates a polished markdown brochure using GPT
6. Streams the output word by word in real time (like ChatGPT)

## Tech Stack

- Python
- OpenAI API (GPT-4o-mini)
- Jupyter Notebook
- `requests` + `BeautifulSoup` for web scraping
- `python-dotenv` for API key management

## Project Structure

```
brochure-generator/
├── brochure.ipynb       # Main notebook
├── scraper.py           # Website scraping utilities
├── .env                 # API keys (not committed)
└── README.md
```

## Setup

1. Clone the repository
```bash
git clone <your-repo-url>
cd brochure-generator
```

2. Install dependencies
```bash
uv init
uv add openai python-dotenv requests beautifulsoup4
```

3. Add your OpenAI API key to a `.env` file
```
OPENAI_API_KEY=sk-proj-your-key-here
```

4. Run the notebook in Jupyter or Cursor

## Usage

```python
# Basic brochure (waits for full response)
create_brochure("Anthropic", "https://www.anthropic.com/")

# Streaming brochure (word by word output)
stream_brochure("Anthropic", "https://www.anthropic.com/")
```

## Key Concepts

- **Link filtering** — GPT filters out irrelevant links (Terms of Service, Privacy, emails) and keeps only brochure-relevant pages
- **Structured JSON output** — `response_format={"type": "json_object"}` forces GPT to return valid JSON for link selection
- **Streaming** — uses `stream=True` with `update_display()` to render output progressively in Jupyter