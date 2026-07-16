# PokéVault

Pokémon TCG collection tracker — a single-file web app. Search any card by name or by its printed number (e.g. `113/084`), add the printings you own, and watch current market prices, 30-day movement, per-card trend sparklines, and your total collection value.

**Live demo:** https://arthurfachel.github.io/pokevault/

## Features

Card search hits the free [TCGdex](https://tcgdex.dev) API — up to date with new sets, no API key, and market pricing embedded in every card — with the legacy [pokemontcg.io](https://pokemontcg.io) API as fallback (it no longer receives new sets). You can also search by the number printed on the card (`113/084`, `TG13/TG30`): the app finds every set with that printed total and shows all matches so you pick yours. Each card in the collection shows the current market price — TCGplayer (USD), with Cardmarket (EUR) as fallback — the priced variant (Holofoil, Reverse Holo, …), a ▲/▼ 30-day badge, a price-trend sparkline, quantity controls and subtotal. The header ledger tracks total collection value, estimated 30-day change, and card counts, with sorting by value, biggest mover, name, or recently added. Includes a demo mode with sample data for when the APIs are unreachable.

## How it works

- **Current price:** TCGplayer market price per variant (USD); falls back to Cardmarket trend (EUR). Both arrive embedded in TCGdex card responses.
- **30-day change:** estimated from Cardmarket's `avg1` vs `avg30` sale averages (holo-aware), since TCGplayer exposes no history.
- **Sparkline:** plots Cardmarket's `avg30 → avg7 → avg1 → trend` points per card.
- **Number lookup:** `113/084` → matches sets whose printed total is 84, then fetches card 113 from each candidate set.

No build step, no dependencies — open `index.html` in a browser, or serve it statically.

## Deploy (GitHub Pages)

Settings → Pages → *Deploy from a branch* → `main`, `/ (root)`.

## Notes

Prices are indicative market data, not appraisals. Very recent releases may not have pricing until the marketplaces list them. TCGdex is a free community-maintained API with no key required. This project is unaffiliated with Nintendo, The Pokémon Company, TCGdex, TCGplayer, or Cardmarket.
