# Make + Gemini Reply Assistant

A prototype that turns customer messages into reply drafts for human review.
The draft goes back into Google Sheets, where a person can review it before
sending anything to a customer.

## Workflow

1. **Google Sheets — Watch New Rows** picks up a new customer message.
2. **Gemini — Generate a response** drafts a short reply. The prompt asks Gemini
   to match the customer's language and writing style, including French, Darija,
   or Arabizi, and to avoid inventing prices or appointments.
3. **Google Sheets — Update a Row** writes the draft back to the source row.

## Try it with sample data

1. Create a test sheet with `Customer message` and `Draft reply` columns.
2. In Make, connect Google Sheets and Gemini. Set up the three modules above.
3. Pass the message column to Gemini. In the final module, map the row number
   from the trigger and Gemini's draft text to `Draft reply`.
4. Run the scenario and add a fictional message, such as
   `Salam, wach katkhdmo nhar l7ed?`
5. Check that the draft appears on the same row and avoids claiming Sunday
   opening hours unless those hours were provided.

## Prototype status

The workflow ran end to end for one row. Two issues are documented:

| Observation | Next check |
| --- | --- |
| Make reported a successful update, but the reply cell on row 3 stayed empty. | Inspect the row number and reply field passed to the final module. |
| Make stopped one run after 10 minutes when Gemini returned no result. | Inspect the Gemini module output and repeat the test with fictional messages. |

Use fictional messages for testing and keep credentials in Make connections.

[Read the full project report in French](Rapport_Projet_Automatisation_Make_Gemini.pdf)
