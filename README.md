# Sales Outreach Automation

LangGraph-based automation that researches leads from your CRM, qualifies them, and drafts outreach emails, reports, and call scripts.

Built around a sample agency (`ElevateAI Marketing Solutions` in `/data`), but you can swap that out for your own product or services.

## What it does

1. Pulls new leads from HubSpot, Airtable, or Google Sheets
2. Researches each lead (LinkedIn, website/blog, social, recent news)
3. Qualifies them against criteria you can change in the prompts
4. For qualified leads, generates:
   - research reports (saved locally + Google Docs)
   - a personalized outreach email
   - an interview/call script
5. Updates the CRM with status and report links

Example outputs are in `/reports`. Workflow details are in [`docs/system-workflow.md`](docs/system-workflow.md).

## Stack

- Python 3.9+
- LangGraph / LangChain
- Google Gemini (default LLM; OpenAI also supported)
- HubSpot, Airtable, or Google Sheets for leads
- Serper (search), RapidAPI LinkedIn scraper, Google Docs/Gmail APIs

## Setup

```bash
git clone <your-repo-url>
cd sales-outreach-automation-langgraph
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
```

Fill in `.env` with your keys. See `.env.example` for what’s needed.

You’ll typically need:

| Service | Used for |
|---|---|
| Gemini (or OpenAI) | LLM + embeddings |
| Serper | web search |
| RapidAPI LinkedIn | profile data |
| Google APIs | Docs, Sheets, Gmail |
| HubSpot / Airtable / Sheets | lead source |

Google API setup: [Gmail Python quickstart](https://developers.google.com/gmail/api/quickstart/python) (enable Docs/Sheets/Gmail as needed).

## Run

By default `main.py` uses Airtable. Switch to Sheets or HubSpot in that file if you prefer.

```bash
python main.py
```

## Customize

- replacing agency/product copy and case studies in `/data`
- adding your own CRM loader
- changing lead statuses and CRM field names
- editing qualification / email / report prompts

