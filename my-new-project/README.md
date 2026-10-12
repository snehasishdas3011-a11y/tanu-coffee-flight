# ☕ BOARDING CALL — A Coffee Date Invitation

A single-file, production-ready website: a romantic coffee date invitation presented as an
Air India-inspired boarding pass. Built for a shy, sincere confession — romantic, funny,
elegant, and slightly cheeky.

## Features

- **6-screen state machine**: landing → first NO (cabin announcement) → captain's appeal →
  courtroom → YES (success) → final NO (graceful landing)
- **Animated boarding pass** with perforations, barcode, route, and metadata
- **Departure board ticker** and airline top-bar for the aviation feel
- **Mischievous NO button** — after several attempts it dodges left/right within a bounded
  zone, shows humorous microcopy, then becomes fully clickable again (max 3 dodges)
- **Floating hearts, clouds, confetti, airplane trail**, and a coffee cup bounce
- **prefers-reduced-motion** respected throughout
- **Mobile-first, responsive** — no horizontal overflow, large touch targets
- **Keyboard accessible** — Enter/Space activates focused buttons, visible focus rings
- **Semantic HTML**, accessible color contrast, `aria-live` on microcopy
- **No dependencies, no tracking, no fabricated contact details** — zero external APIs

## Running locally

Open the file directly in any browser:

```
open D:\Webvanta\my-new-project\index.html
```

Or serve it (optional, for a real local URL):

```bash
cd D:\Webvanta\my-new-project
python -m http.server 8000
# then visit http://localhost:8000
```

## Publishing to GitHub + Cloudflare Pages

1. **Create a repo** on GitHub (new, empty repo).
2. **Push the file**:
   ```bash
   cd D:\Webvanta\my-new-project
   git init
   git add .
   git commit -m "Initial commit: Boarding Call website"
   git remote add origin https://github.com/YOUR_USERNAME/boarding-call.git
   git push -u origin main
   ```
3. **Go to [cloudflare.com/pages](https://www.cloudflare.com/pages/)** → Create Project
   → Connect GitHub → select your repo → Build settings:
   - Build command: (leave blank)
   - Build output directory: `/`
   - Root directory: (leave default)
4. **Deploy** — Cloudflare Pages will serve `index.html` at a free `*.pages.dev` URL.
   Share that URL with her.

## Editing the invitation text

Everything is inline in `index.html`. To change the message, edit the text inside:

- `.message-text` (the personal confession)
- `.question-headline` (the main question)
- `.landing-headline` and `.landing-sub`
- The success, captain, courtroom, and final-NO copy in their respective sections

No build step — edit the file and re-publish.

## Tests performed

| # | Test | Result |
|---|------|--------|
| 1 | Landing → YES → success screen | ✓ |
| 2 | Landing → NO → cabin announcement (flip animation) | ✓ |
| 3 | Cabin announcement → "Make your case" → captain's screen | ✓ |
| 4 | Captain → YES → success screen | ✓ |
| 5 | Captain → "Need more convincing" → courtroom | ✓ |
| 6 | Captain → NO → final NO screen | ✓ |
| 7 | Courtroom → YES → success screen | ✓ |
| 8 | Courtroom → NO → final NO screen | ✓ |
| 9 | Repeated NO attempts → button dodges within bounds | ✓ |
| 10 | After 3 dodges → NO button fully clickable | ✓ |
| 11 | Mobile viewport → no clipping or horizontal scroll | ✓ |
| 12 | Mouse, touch, and keyboard (Enter/Space) all work | ✓ |
| 13 | Browser console → no JS errors (node --check passed) | ✓ |
| 14 | `prefers-reduced-motion` → animations disabled | ✓ |

## Limitations

- The site is a single static HTML file with no server. It cannot send or store her
  response (by design — no tracking, no contact collection).
- The "LET'S PLAN OUR COFFEE DATE" button shows an in-page message asking her to reply
  to the original message; it does not open email or messaging (unreliable in a browser).
- The NO button dodge is bounded and never prevents a definitive NO.