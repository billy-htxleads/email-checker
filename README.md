# ACS Email Brand Checker

Paste an Eloqua drag-and-drop HTML export → get Slack-ready review comments checked against the New Brand Email Guidelines.

**Everything runs in the browser.** No server, no build step, nothing uploaded - safe to use with unreleased email content.

## Use it

Open `index.html` in any browser, or use the hosted version on GitHub Pages.

## What it checks

- **Images** - alt text required, .png/.jpg only
- **Colors** - every inline color vs. the brand palette, quoting the exact copy it's on, with near-miss typo detection (e.g. `#402BFD` → `#412BFD`)
- **Default colors** - copy falling back to the editor's default black (`#000000` on wrapper cells) gets an "update default text colors" comment; an off-brand `a { color }` rule in the stylesheet gets "update default link color"
- **Typography** - Arial only; sizes on the 12/14/16/20/22/24/36 scale, quoting the exact copy (body copy only, header/footer blocks are standard across emails)
- **Hyperlinks** - underlined + Chromium Blue `#412BFD`; every body-content link (text, image, and button) needs hover text (a `title` attribute); header/footer and social icon links are exempt
- **Buttons** - 30px corner radius and 10/30px inner padding (including asymmetric top/bottom)
- **Text boxes** - 20px left/right padding
- **Emojis** - flagged in bulleted lists

## What it deliberately ignores

- The "view online" header bar (boilerplate, we don't touch it) - the footer IS checked
- The canvas background behind the email and the social icons strip
- Row backgrounds fully covered by content cells with their own background
- Button/background color combos and outer padding - checked visually instead (approved variations aren't all in the guidelines)

Things that can't be derived from the HTML (subject line, preview text vs. ticket, sender/reply-to, email group, ad module sizing, logo placement) are shown as a manual reminder list.

## Updating the rules

All brand data lives at the top of the `<script>` in `index.html`: `PALETTE` and `TYPE_SCALE`. Edit and refresh.

`test/acs-sample.html` is a real export used as a test fixture (not committed).
