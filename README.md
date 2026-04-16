# LivingHome

A Pokémon living dex tracker — installable as a PWA, works offline, and syncs across devices via optional cloud sign-in. Built as a single HTML file with no framework dependencies.

🔗 **Live at:** https://prhaupt.github.io/livingdex/

---

## Features

### Dex Tracking
Track your catches across 15 separate dexes, each with per-box progress bars and an overall completion percentage:

| Dex | Coverage |
|-----|----------|
| HOME Living Dex | All 1,391 HOME-depositable Pokémon across 47 boxes |
| Shiny Living Dex | Same HOME list, shiny sprites, shiny-locked indicators |
| Sword & Shield | Base game, Isle of Armor, and Crown Tundra sections |
| Black & White | Full Unova dex |
| Black 2 & White 2 | Full B2W2 regional dex |
| X & Y | Full Kalos dex |
| Omega Ruby & Alpha Sapphire | Full Hoenn dex |
| Sun & Moon | Full Alola dex |
| Ultra Sun & Ultra Moon | Full USUM dex |
| Let's Go Pikachu & Eevee | Kanto dex |
| Brilliant Diamond & Shining Pearl | Full Sinnoh dex |
| Legends: Arceus | Full Hisui dex |
| FireRed & LeafGreen | Full Kanto dex |
| Scarlet & Violet | Full Paldea dex |
| Legends: Z-A | Full Kalos dex |

### Info Panel
Tap the ⓘ on any Pokémon (or long-press on mobile) to open a detail panel showing:
- Full evolution line with evolution conditions (level, friendship, item, trade, etc.)
- Shiny sprites when viewing from the Shiny dex
- Type badges
- Where to find it across modern games
- Direct link to PokémonDB

### Cloud Sync
Sign in with your email (magic link — no password needed) to sync your progress across devices via Supabase. Catches sync automatically when you open or close a dex, with a status indicator in the header.

### Other
- **Search** — filter by Pokémon name within any dex
- **Progress bars** — per-box and overall, updating live as you tap
- **Offline support** — works fully offline after first load (PWA service worker)
- **Installable** — on iPhone: Safari → Share → Add to Home Screen; on Android: browser menu → Install

---

## Usage

Open the URL in any browser. Tap or click a Pokémon to mark it as caught. Data is saved to your browser's localStorage automatically — no account required. Optionally sign in with your email to enable cross-device sync.

---

## Technical Notes

Everything lives in a single self-contained `index.html` with no build step and no framework. External dependencies at runtime:

- **PokémonDB** sprite CDN — for Pokémon images (normal and shiny)
- **PokeAPI** — evolution chain data, fetched on demand when the info panel opens
- **Supabase** — optional cloud sync (email magic link auth, `catches` table with RLS)

The PWA service worker caches the HTML for offline use. Sprites and evolution data are not cached (to keep storage usage low).

Local data is stored in `localStorage` per dex. Cloud sync performs a union merge — catches present on either side are kept, nothing is deleted from the other device.

---

## Data Sources

- Sprites: [PokémonDB](https://pokemondb.net)
- Evolution data: [PokeAPI](https://pokeapi.co)
- Location data: hand-curated static JSON covering Sun/Moon through Legends: Z-A
- Pokédex order: based on Pokémon HOME depositable list via [Serebii](https://serebii.net)

---

## License

MIT License

Copyright (c) 2026 Peter Haupt

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

## Disclaimer

This is an unofficial fan project and is not affiliated with, endorsed by, or connected to Nintendo, Game Freak, or Creatures Inc. in any way.

Pokémon and all related names, characters, and imagery are trademarks and © of Nintendo / Game Freak / Creatures Inc. Sprite images are sourced from [PokémonDB](https://pokemondb.net) and remain the property of their respective owners. This project does not distribute or host any Pokémon assets — all images are loaded directly from third-party CDNs at runtime.
