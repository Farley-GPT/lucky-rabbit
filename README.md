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

## How it works

- Wish flow: write a wish ("for me" or "for someone else") → music-box chime (synthesized
  in the browser, no audio files) + sparkle burst → the wish is sealed on a plaque.
- The plaque downloads as a PNG drawn on a canvas — the keepsake is the product.
- Privacy is the design: there is no server, so wishes cannot be collected, read, or
  leaked. The page says so, because it's true.
