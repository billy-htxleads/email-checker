# ACS Email Brand Checker

Paste an Eloqua drag-and-drop HTML export → get Slack-ready review comments checked against the New Brand Email Guidelines.

**Everything runs in the browser.** No server, no build step, nothing uploaded — safe to use with unreleased email content.

## Use it

Open `index.html` in any browser, or host it on GitHub Pages:

1. Push this repo to GitHub
2. Repo → Settings → Pages → Source: **Deploy from a branch** → `main` / root
3. Open `https://<user>.github.io/email-checker/`

## What it checks

- **Images** — alt text required, .png/.jpg only
- **Colors** — every inline/`<style>` color vs. the brand palette, with near-miss typo detection (e.g. `#402BFD` → `#412BFD`)
- **Text with no color set** — flags text that will fall back to the client default
- **Typography** — Arial only; sizes on the 12/14/16/20/22/24/36 scale
- **Hyperlinks** — underlined + Chromium Blue `#412BFD`
- **Buttons** — 30px radius, 10/30px inner padding (incl. asymmetric top/bottom), approved fill + background + text-color combinations, outer padding
- **Text boxes** — 20px left/right padding
- **Emojis** — flagged in bulleted lists

Things that can't be derived from the HTML (subject line, preview text vs. ticket, sender/reply-to, email group, ad module sizing, logo placement) are shown as a manual reminder list.

## Updating the rules

All brand data lives at the top of the `<script>` in `index.html`: `PALETTE`, `TYPE_SCALE`, and `BUTTON_COMBOS`. Edit and refresh.

`test/acs-sample.html` is a real export used as a test fixture.
