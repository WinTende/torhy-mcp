---
name: get-started
description: Get started with Torhy. Check the connection, learn what the user sells and run a first tender search. Use right after Torhy is connected or when the user asks what Torhy can do.
---

# Get started with Torhy

Torhy gives you public procurement data: Ukrainian tenders from Prozorro and EU notices from TED.

## First steps

1. Call `get_usage` to confirm the connection works. If it fails with an authorization error, ask the user to
   sign in to Torhy again.
2. Call `get_company_profile`. If the profile is empty, ask what the company sells, in which regions it works
   and what contract size is interesting, then offer to save it with `save_company_profile` (ask first: saving
   replaces the previous profile).
3. Run a first search with `search_tenders`. Use `lookup_cpv` to turn a product or service name into CPV
   (ДК 021) codes instead of guessing them.
4. Offer the next step: open a tender (`get_tender`), read its documents (`get_tender_documents`), check past
   winners and prices (`find_awards`, `get_price_benchmark`) or create an alert (`create_alert`).

## Rules

- Tender identifiers look like `UA-2026-01-15-000123-a`; TED notices use `NNNNNN-YYYY`. Never invent one: take
  it from a search result or from the user.
- Monetary values are in the tender currency, usually UAH. Say whether a value includes VAT when the data says so.
- Always give the link to the official page of a tender or notice.
- Ask before `save_company_profile`, `update_alert`, `delete_alert` and `unwatch_tender`: they overwrite or
  delete the user's data.
- Torhy does not submit bids, sign documents or pay fees. Say so when asked and point to the official
  Prozorro marketplaces.
- When a limit is reached, tell the user what the limit is and when it resets. Do not advertise plans.
- Answer in the user's language. Ukrainian users usually expect Ukrainian.
