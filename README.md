# Rates API docs for docs.termina.com (Mintlify)

Drafts to add the business electricity rates API to the Termina docs, written so AI agents can find it, understand it and use it correctly.

## What's here

| File | Goes to | Purpose |
| --- | --- | --- |
| `openapi-rates.yaml` | docs repo root | OpenAPI 3.1 spec for `GET /v1/rates` (validated). Mintlify builds the API reference from it |
| `rates/overview.mdx` | `rates/` | What the API answers, coverage, FAQs |
| `rates/quickstart.mdx` | `rates/` | First request, reading `summary`, re-costing, paging |
| `rates/ai-agents.mdx` | `rates/` | **The key page for agents**: connect (MCP or REST), recommended flow, presenting results accurately, handing off to switch, citing |
| `rates/locations.mdx` | `rates/` | NMI, postcode, network, city, state; split postcodes |
| `rates/methodology.mdx` | `rates/` | How plans and benchmarks are costed; data sources |
| `rates/buying-group-and-public-plans.mdx` | `rates/` | Offer sources, fee, promise, plan IDs, customer type |
| `rates/errors-and-warnings.mdx` | `rates/` | Every error and warning code, and what to do |
| `rates/networks-and-cities.mdx` | `rates/` | Every slug, generated from the API's own data files |
| `api-reference/rates/get-rates.mdx` | `api-reference/rates/` | Reference page generated from the spec |
| `docs.json.snippet.json` | merge into `docs.json` | Navigation for the new pages |
| `index-additions.mdx` | merge into `index.mdx` | Homepage now introduces both APIs; two new FAQs |
| `termina-com-llms-txt-additions.md` | termina.com `/llms.txt` | Points agents from the main site to the rates API |

## Before publishing

1. **Deploy rates API update 7.** These docs describe its `summary` block, benchmark labels, per-network stats, masked buying group rows, and the fixed `page_url` (most specific page: network, city, then state). The live API is on an earlier version.
2. **Fill the placeholders** (search for `[`):
   - `[MCP server URL]` and the tool name `[get_business_electricity_rates]`
   - `[Termina sign-up URL]` for handing off to switch
   - `[CONFIRM: basis and duration]` of the 50% fee
   - `[approved promise wording]` (legal)
   - `[CONFIRM: conditional discounts]` in the methodology
3. **Decide on API keys.** The docs say "no API key". If you add keys later, update the overview, quickstart and FAQs.
4. **Legal:** confirm redistributing Consumer Data Right plan data through a public API is allowed.

## Why each part helps agents find and use the API

- **Descriptions are answer sentences.** Mintlify uses each page's `description` in `llms.txt` and in search snippets, so each one says what the page answers in plain terms ("Compare Australian business electricity rates for any postcode…").
- **The OpenAPI spec is detailed.** Agents read field descriptions to decide how to call an API and interpret it. Every parameter has a range, default and example; every field says what it means and when it's null.
- **One page tells agents exactly what to do.** `rates/ai-agents.mdx` gives the flow, the presentation rules (name the source, state usage, GST and date, relay warnings) and an example answer, which makes correct citation the easy path.
- **Question-shaped FAQs** match how people and agents ask ("Is there an API for Australian business electricity rates?").
- **Both directions are linked:** the main site's `llms.txt` points to the docs, the docs point to the rates pages via `page_url`, and every rates page should link "Get these rates as JSON" and "For developers and AI agents".

## Also worth fixing in the existing docs

- The intro repeats "No model training. No infrastructure. One endpoint." three times.
- Stray backslashes (`\\`) in the card descriptions.
- The quickstart calls `api.termina.io/v1/extract`, but the OpenAPI spec documents `/api/v2/public/bills/upload/`. Agents will try whichever they read first, so they need to match.

## After publishing

- Submit the MCP server to the MCP Registry and the Claude and ChatGPT directories.
- Check `https://docs.termina.com/llms.txt` lists the new pages with their descriptions.
- Track API and MCP calls by referrer and user agent, to see which agents arrive and from where.
