# brochure-generator

An AI-powered tool that automatically generates a professional company brochure by scraping a website and using OpenAI's GPT model to summarize relevant content for prospective clients, investors, and recruits.

## What it does

1. Takes a company name and website URL as input
2. Scrapes the website and extracts all links
3. Uses GPT to identify relevant pages (About, Careers, Company pages)
4. Fetches content from those relevant pages
5. Generates a polished markdown brochure using GPT
6. Streams the output word by word in real time via a Gradio UI

## Tech Stack

- Python
- OpenAI API (gpt-5-nano)
- Gradio
- Jupyter Notebook
- requests + BeautifulSoup for web scraping
- python-dotenv for API key management

## Project Structure
brochure-generator/
├── brochure.ipynb    # Main notebook
├── .env              # API keys (not committed)
└── README.md

## Setup

1. Clone the repository
```bash
git clone <your-repo-url>
cd brochure-generator
```

2. Install dependencies
```bash
uv add openai gradio python-dotenv requests beautifulsoup4
```

3. Add your OpenAI API key to a `.env` file
OPENAI_API_KEY=sk-proj-your-key-here

4. Run the notebook in Jupyter or Cursor

## Usage

```python
# Streaming brochure in notebook
stream_brochure("Anthropic", "https://www.anthropic.com/")

# Or use the Gradio UI — enter company name and URL, get brochure streamed in markdown
```

## Key Concepts

- **Link filtering** — GPT filters out irrelevant links (Terms of Service, Privacy, emails) and keeps only brochure-relevant pages
- **Structured JSON output** — `response_format={"type": "json_object"}` forces GPT to return valid JSON for link selection
- **Streaming** — uses `stream=True` with `yield` to render output progressively
- **Gradio UI** — `gr.Interface` with a Markdown output component renders the brochure with full formatting