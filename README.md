# Termina docs (docs.termina.com)

Mintlify documentation for Termina's bill extraction API and business electricity rates API.

- `docs.json`: site settings and navigation. Every page listed must exist at that exact path (without `.mdx`).
- `openapi.yaml`: bill extraction API spec. `openapi-rates.yaml`: rates API spec.
- Preview locally: `npm i -g mint` then `mint dev`. Check for broken links: `mint broken-links`.
