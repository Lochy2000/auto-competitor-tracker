# Business Process Blueprint: Autonomous Competitor Intelligence Agent

## 1. Objective & Business ROI
Manual competitive analysis takes marketing and product teams an average of 4–6 hours per week. This automation reduces that time to zero by autonomously tracking competitor movements, synthesizing raw data into executive summaries, and delivering structured data payloads to internal tools.

## 2. Process Flow (Step-by-Step)
1. **Trigger:** A scheduled cron timer kicks off the workflow weekly, or an ad-hoc Webhook receives a specific competitor target payload.
2. **Data Ingestion:** The workflow fetches the target's public web data using an HTTP request or specialized scraping API.
3. **Guardrail Check:** Ensure the fetched payload contains text data and did not hit a CAPTCHA or 403 Forbidden block.
4. **AI Transformation:** A Large Language Model parses the raw data against a strict system prompt to identify specific business movements (pricing changes, feature drops, positioning shifts).
5. **Data Structuring:** The LLM enforces a strict JSON schema output.
6. **Downstream Delivery:** The workflow transforms the JSON into an HTML email summary for executives and simultaneously pushes the raw structured data to a database (Airtable/PostgreSQL) via API.

## 3. Boundary Conditions & Error Handling
* **Empty Payload:** If the scraper returns no text, the workflow must halt and log an alert, rather than sending empty data to the LLM (saving API costs).
* **AI Hallucination Guardrail:** The system prompt explicitly instructs the LLM to output `"no_change_detected"` rather than guessing or fabricating updates if no meaningful differences are found.
