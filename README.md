# PokéVault

Pokémon TCG collection tracker — a single-file web app. Search any card, add the printings you own, and watch current market prices, 30-day movement, per-card trend sparklines, and your total collection value.

**Live demo:** https://arthurfachel.github.io/pokevault/

## Features

Card search hits the free [pokemontcg.io](https://pokemontcg.io) API (every printing, newest sets first). Each card in the collection shows the current market price — TCGplayer (USD), with Cardmarket (EUR) as fallback — the priced variant (Holofoil, Reverse Holo, …), a ▲/▼ 30-day badge, a price-trend sparkline, quantity controls and subtotal. The header ledger tracks total collection value, estimated 30-day change, and card counts, with sorting by value, biggest mover, name, or recently added. Includes a demo mode with sample data for when the API is unreachable.

## How it works

- **Current price:** `tcgplayer.prices[variant].market` (USD); falls back to `cardmarket.prices.trendPrice` (EUR).
- **30-day change:** estimated from Cardmarket's `avg1` vs `avg30` sale averages (reverse-holo aware), since TCGplayer's API exposes no history.
- **Sparkline:** plots Cardmarket's `avg30 → avg7 → avg1 → trend` points per card.

No build step, no dependencies — open `index.html` in a browser, or serve it statically.

## Deploy (GitHub Pages)

Settings → Pages → *Deploy from a branch* → `main`, `/ (root)`.

## Notes

Prices are indicative market data, not appraisals. The free API is rate-limited (~1,000 requests/day without a key) and occasionally slow. This project is unaffiliated with Nintendo, The Pokémon Company, TCGplayer, or Cardmarket.
