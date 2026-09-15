---
format: 2
name: ksor-restaurants
title: Askari's Restaurant Knowledge Base
description: Menu, dietary information, allergens, reservation policy, refund and cancellation policy, and operating hours for Askari's Restaurant.
toolchain:
  requires: ">=0.0.60"
  scaffolded: "0.0.60"
database:
  dsn_env: KSOR_DB_URL
# retrieval.vector_floor: NOT SET — abstention gate is OFF by design.
# Calibration attempted 2026-09-15 on generation 3 (19 in-corpus / 9 OOC queries)
# with ksor calibrate --queries-file / --ooc-file. The corpus does NOT separate:
# max OOC score 0.613 ("Can I order online for delivery?") >= min in-corpus 0.570
# ("What payment methods do you accept?"). Five OOC questions scored above the
# weakest in-corpus threshold, all legitimately near-miss restaurant questions
# that share menu/food/service vocabulary with our 7-document corpus. AURC 0.0784,
# zero-FA floor would leak 20.8% of OOC questions. This is expected for a small,
# narrow-domain corpus where embedding distance cannot reliably separate
# restaurant-adjacent questions from in-scope ones. Scope enforcement relies on
# the MCP server's declared instructions ("decline firmly — 'not in this corpus'
# is a correct answer") rather than a vector floor.
---

This record is authoritative for the menu, ingredient/allergen and dietary information, reservation policy, refund and cancellation policy, and operating hours for Askari's Restaurant — a single-location Pakistani/desi cuisine restaurant. Current versions only, customer-facing.

It does NOT cover pricing negotiations or catering/bulk-order quotes, supplier or inventory data, staff schedules or payroll, past/discontinued menu versions or seasonal menus that have expired, nutritional/calorie counts unless explicitly added, real-time table availability or live order status, or other branches' menus or policies if we later add locations.

When asked about something outside this scope, decline firmly — "not in this corpus" is a correct answer.

## Known Limitations

**Abstention floor: not calibrated.** This 7-document, single-restaurant corpus does not separate cleanly between in-corpus and out-of-corpus questions by embedding similarity — near-miss questions (e.g. "do you have a kids' menu?") scored 0.58–0.62, overlapping our weakest in-corpus scores (~0.57–0.59). Attempted twice with hand-written query files, not just generic auto-generated ones. Scope enforcement therefore relies on the connected agent reading this document's declared scope and exclusions, not a measured vector floor.
