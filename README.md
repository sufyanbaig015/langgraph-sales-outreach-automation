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

## Stack

- Python 3.9+
- LangGraph / LangChain
- Google Gemini (default LLM; OpenAI also supported)
- HubSpot, Airtable, or Google Sheets for leads
- Serper (search), RapidAPI LinkedIn scraper, Google Docs/Gmail APIs
