# English Lexicon Crosswords

A static, local-first crossword-style Progressive Web App built from the Eastern Armenian Crossword Game technical specification and adapted for English vocabulary practice.

## Package

- App name: English Lexicon Crosswords
- Content version: v1
- Target language: English
- Difficulty range: Upper intermediate, advanced, and extremely advanced
- Total puzzles: 35
- Total answer words: 420
- Words per puzzle: 12
- Support clue: optional extra hint, hidden until the player clicks **Extra hint**

## Files

```text
EnglishAdvancedCrosswordGame-v1/
  .nojekyll
  index.html
  manifest.webmanifest
  service-worker.js
  README.md
  data/
    puzzles.json
  icons/
    icon-192.png
    icon-512.png
```

## Gameplay

Players click a clue or a tile, then type directly into the crossword grid.

Core behaviors:

- Typed letters are entered directly into tile inputs.
- Clicking a clue highlights the corresponding word.
- Clicking a tile selects a word that passes through that tile.
- Correct completed words turn green.
- Incorrect letters appear in red.
- Already-correct filled cells are skipped automatically while typing through a word.
- The **Extra hint** button reveals an additional clue, not the answer.
- Progress is saved locally in the browser with `localStorage`.

## Deployment

Upload the contents of this folder to the root of a static host such as GitHub Pages, Netlify, Cloudflare Pages, or Vercel.

For GitHub Pages:

1. Create a repository.
2. Upload the contents of this folder to the repository root.
3. Go to **Settings → Pages**.
4. Choose **Deploy from a branch**.
5. Select the `main` branch and `/ root`.
6. Open the GitHub Pages URL.

After meaningful updates, increment the service worker cache name in `service-worker.js` and open the app with a cache-busting query such as:

```text
?v=v2
```

## Notes for future editing

Puzzle data is embedded directly in `index.html` and also copied to `data/puzzles.json`. Keep both in sync if editing manually, or refactor the app to load the JSON at runtime.

## v2 phone/tablet display update

This package has been updated so the crossword board is easier to use on phones and tablets:

- The rendered board is cropped to the smallest rectangle containing answer cells, removing unused outer grid space.
- Tile size is calculated from the current viewport so the full board fits without horizontal dragging.
- Mobile styling uses tighter spacing, smaller grid gaps, and touch-friendly clue cards.
- The service worker cache name has been incremented to help browsers pick up the new files after deployment.
