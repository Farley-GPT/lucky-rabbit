# Make a Wish to the Lucky Rabbit 🐇

A static wish portal by **Brandon Farley** (GLITCHMADE). Someone finds a card, scans the
QR code, lands here, makes a wish, and leaves with a gold-sealed plaque. Free forever.
No accounts, no tracking, no backend — a wish never leaves the visitor's browser.

## Publish it on GitHub Pages

1. Create a new **public** repository on GitHub (e.g. `lucky-rabbit`).
2. Upload everything in this folder (`index.html`, `assets/`, this README, `.nojekyll`).
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. Your portal address becomes:
   `https://<your-github-username>.github.io/lucky-rabbit/`
5. Card links can carry a number, e.g. `https://<you>.github.io/lucky-rabbit/?card=047` —
   the page shows "Found Card № 047" and prints it on the plaque.

**Lock this URL before printing any QR codes** — a printed code can't be edited later.

## Turn on the tip jar

Open `index.html`, find `SITE CONFIG` near the top of the script at the bottom, and paste
your links between the quotes:

```js
const DONATE = {
  paypal:  "https://www.paypal.com/paypalme/yourname",
  venmo:   "https://venmo.com/u/yourname",
  cashapp: "https://cash.app/$yourname"
};
```

Any button left empty doesn't appear. Save, commit, done — Pages redeploys itself.

## One page, one QR code (the current design)

Everything lives on the home page (`index.html`). The printed cards all carry the
**same single QR code**, pointing at this page — the card's printed number does the
identifying. A finder scans, lands here, scrolls **The Whole Trail**, and taps their
card's number (or types it into the jump box).

- **Card № 000 — the Doorkeeper.** The page opens greeted by the Original Rabbit
  (the `assets/aura-lucky-rabbit.jpg` portrait). She exists only here, never in
  print. Anyone can wish with her as witness.
- **Cards № 001–192.** Tapping one swaps the greeter to **that card's own Aura
  image** (all 192 live in `assets/cards/`, numbered in the cut-sheet order;
  `assets/cards/manifest.json` maps each number back to its original image
  filename), shows **her note for that card** — every card gets its own
  combination of greeting + blessing + name ("Aura, the Silver Rabbit"); cards
  № 000 and № 001 are hand-written, and any card can be hand-written by adding
  it to `HANDWRITTEN` in `index.html` — and makes her the witness on the
  downloadable plaque.
- Direct links still work for sharing: `?card=047` opens the page already
  greeted by that rabbit.
- **The locked cabinet.** The № 001–192 previews start tucked behind a pair of
  cabinet doors in The Whole Trail. A round gold heart latch (with a keyhole
  while locked) jiggles when tapped, plays Aura's giggle (`assets/giggle.mp3`),
  and opens the cabinet; tapping again tucks them away. The number jump box
  works either way, and the donation section lives below the cabinet, always
  visible.

Earlier prototypes (the v1 single-wish page and the separate `card.html` design)
are kept in `versions/` for reference; the live tree is the merged page.

## How it works

- Wish flow: write a wish ("for me" or "for someone else") → music-box chime (synthesized
  in the browser, no audio files) + sparkle burst → the wish is sealed on a plaque.
- The plaque downloads as a PNG drawn on a canvas — the keepsake is the product.
- Privacy is the design: there is no server, so wishes cannot be collected, read, or
  leaked. The page says so, because it's true.

## Upgrades (October 2026)

- **Faster page.** The card pictures and the giggle are no longer packed inside
  `index.html` (it went from ~4.8 MB to ~80 KB). Pictures load from `assets/cards/`
  only when they're shown.
- **Every card is hand-written.** All 193 notes now live in `HANDWRITTEN` in `index.html`.
- **Share this rabbit.** Uses the phone's share sheet, or copies a `?card=NNN` link.
- **Collector's trail.** The page remembers which rabbits you've met (on your device only,
  in `localStorage`) and shows "met X / 193". Meet all 193 for a secret note from Aura.
- **Today's rabbit.** A featured card that changes each day (the same for everyone).
- **Moon and seasons.** A gold glow near the full moon, plus Halloween, winter, Valentine
  and clover-week tints.
- **Plaque choices.** Gold, rose or night-sky frames; tall (1200×1500) or square (1080×1080).
  Long wishes shrink to fit.
- **Friendly card lookup.** Numbers outside 0 to 192 show a gentle message instead of jumping.
- **Optional music.** Drop a quiet looping track at `assets/music.mp3` and a small
  "♪ Music" toggle appears (off by default). With no file, the toggle stays hidden.
- **Link previews.** Open Graph / Twitter tags so shared links show Aura.

Still true: no accounts, no server, no analytics. Nothing typed leaves the browser.
