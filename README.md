# LivingDex Tracker

A personal Pokémon HOME LivingDex tracker — single HTML file, no backend, no account required.

## Features

- **HOME Tab** — all 1,391 HOME-depositable Pokémon across 47 boxes, matching HOME's box layout
- **Galar Regional Tab** — Sword & Shield base game (400), Isle of Armor (110), and Crown Tundra (74) in separate sections
- **Info Panel** — tap the ⓘ on any Pokémon to see:
  - Evolution line with conditions (friendship, items, trade, level etc.)
  - Where to find it across modern games (Sun/Moon through Legends: Z-A)
  - Direct link to PokémonDB
- **Search & filter** — search by name, filter by caught/missing
- **Progress tracking** — per-box progress bars, overall completion percentage
- **Offline** — works fully offline after first load (PWA)
- **Install on iPhone** — open in Safari → Share → Add to Home Screen

## Usage

Open the URL in any browser. Click/tap a Pokémon to mark it as caught. Data is saved to your browser's localStorage — it persists between sessions on the same device.

## Data Sources

- Sprites: [PokémonDB](https://pokemondb.net)
- Evolution data: [PokeAPI](https://pokeapi.co)
- Location data: hand-curated static table covering Sun/Moon through Legends: Z-A
- Pokédex order: based on Pokémon HOME depositable list via [Serebii](https://serebii.net)

## Known Issues / TODO

- Eternal Floette sprite needs updating once PokémonDB adds a Gen 9 HOME sprite
- Location data for some less common Pokémon may be incomplete — contributions welcome

## Technical Notes

Everything is a single self-contained HTML file (`index.html`) with no external dependencies except:
- PokémonDB sprite CDN (for images)
- PokeAPI (for evolution chain data, fetched on demand when opening the info panel)

The PWA service worker caches the HTML file for offline use. Sprites and evolution data require a network connection on first view but are not cached (to keep storage usage low).

## Disclaimer

This is a personal fan project. Pokémon and all related names are trademarks of Nintendo / Game Freak / Creatures Inc. Sprite images belong to their respective owners.
