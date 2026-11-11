# Make + Gemini: AI-assisted customer reply workflow

A no-code automation that reads a customer message from Google Sheets, asks Google Gemini to draft a polite reply, and writes it back to the sheet. A human reviews the reply before it is sent.

## How it works
Google Sheets (Watch New Rows) → Gemini (Generate a response) → Google Sheets (Update a Row)

## Tools
- Make (free plan)
- Google AI Studio, Gemini 3.8 Flash
- Google Sheets

## Design choices
- The system prompt asks the model to reply in the customer's language and writing style (Darija, French, Arabizi), keep answers short, and never invent prices or appointments.
- All test messages are fictional.

## Status
Prototype. The full chain worked end to end for one row.

## Known issues
- Row 3: Make reports a successful write, but the target cell stays empty (cause not found yet).
- One run was stopped by Make after 10 minutes because a Gemini call returned no result.

## What I learned
- A spreadsheet ID is not the file name.
- Map a specific field, not a whole bundle.
- Prompts should forbid inventing facts such as prices.

## Security notes
- No API keys are stored in this repository.
- Screenshots in the report have personal identifiers masked.

## Full report
See the `docs` folder (French).
