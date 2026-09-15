# restaurant-ksor

**restaurant-ksor** is a demo Knowledge System of Record (KSoR) for a restaurant, built with [@panaversity/ksor](https://github.com/panaversity/ksor). It holds governed, versioned, human-approved documents — menu, dietary/allergen info, reservation policy, refund policy, and hours — published as both a browsable website for people and a citable MCP server for AI agents.

## Documents

This record contains 7 documents:

1. **[welcome.md](knowledge/welcome.md)** — Introduction and navigation
2. **[menu.md](knowledge/menu.md)** — Full menu with prices and ingredients
3. **[allergens-and-dietary.md](knowledge/allergens-and-dietary.md)** — Allergen and dietary information for every dish
4. **[policies/reservations.md](knowledge/policies/reservations.md)** — Reservation policy and deposit terms
5. **[policies/refunds-and-cancellations.md](knowledge/policies/refunds-and-cancellations.md)** — Refund and cancellation terms
6. **[hours-and-location.md](knowledge/hours-and-location.md)** — Operating hours and location
7. **[faq.md](knowledge/faq.md)** — Frequently asked questions

## Setup

```sh
npm install           # Install dependencies (once)
npm run dev           # Start the dev site at http://localhost:3000

# For the MCP server (requires Postgres + embedding provider key):
npm run provision     # Apply schema and grants (once)
npm run refresh       # Build, ingest, and activate the latest generation
npm run serve         # Start the MCP server at http://127.0.0.1:8080/mcp
```

See [AGENTS.md](AGENTS.md) for full setup instructions including database configuration.

## Known Limitations

**Abstention floor: not calibrated.** This 7-document, single-restaurant corpus does not separate cleanly between in-corpus and out-of-corpus questions by embedding similarity — near-miss questions (e.g. "do you have a kids' menu?") scored 0.58–0.62, overlapping our weakest in-corpus scores (~0.57–0.59). Attempted twice with hand-written query files, not just generic auto-generated ones. Scope enforcement therefore relies on the connected agent reading this document's declared scope and exclusions, not a measured vector floor.

## License

This project was scaffolded with `ksor init` version 0.0.60.
