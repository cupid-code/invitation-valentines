# Template 02 — Amour Carnival (Envelope-Based Date Invitation)

An elegant, animated date invitation with an envelope opening mechanic, escalating "No" reactions, a tear effect on final rejection, and a golden ticket voucher on acceptance.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Single-file page (HTML + Tailwind CSS + JS inline) |
| `config.json` | Customizable data: theme, texts, images, date options |

## How to Customize

Edit `config.json` to personalize for each customer:

```json
{
  "theme": "blush",
  "invitation": { ... },
  "images": { ... },
  "formOptions": { ... }
}
```

### Config Fields

| Field | Description |
|-------|-------------|
| `theme` | Background theme: `"blush"`, `"rose"`, `"crimson"`, or `"midnight"` |
| `invitation.title` | Main headline (e.g., "Will you be my Valentine?") |
| `invitation.subtitle` | Subtext below the headline |
| `invitation.yesButtonText` | Text on the Yes button |
| `invitation.noButtonText` | Text on the No button |
| `invitation.finalNoMessage` | Message shown after final rejection (heartbreak) |
| `images.click1` | Image shown on 1st No click |
| `images.click2` | Image shown on 2nd No click |
| `images.click3` | Image shown on 3rd No click |
| `images.click4` | Image shown on 4th No click |
| `images.final` | Image shown in the heartbreak final state |
| `images.knockoutTimeMs` | How long each reaction image displays (ms) |
| `formOptions.places` | Array of place options for the date planner |
| `formOptions.vibes` | Array of vibe/mood options for the date planner |

### Themes

| Theme | Description |
|-------|-------------|
| `blush` | Soft warm white with red accents (default) |
| `rose` | Light pink romantic feel |
| `crimson` | Warm red tones, passionate |
| `midnight` | Dark purple/indigo with purple accents |

## User Flow

```
Page Load
  → Envelope in center with "Yes!" and "No" buttons
  → Headline: customizable invitation text

Click Yes (or click envelope):
  → Envelope opens with animation
  → Modal appears with "Hooray!" message
  → Step 1: Pick date/time
  → Step 2: Pick location (from list, shuffle, or custom)
  → Step 3: Pick vibe (from list, shuffle, or custom)
  → Golden Ticket voucher generated with all selections
  → "Redeem Your Magic" button

Click No sequence:
  Click 1 → Reaction image 1 + envelope shakes + No shrinks + Yes grows
  Click 2 → Reaction image 2 + more shrink/grow
  Click 3 → Reaction image 3 + more shrink/grow
  Click 4 → Reaction image 4 + more shrink/grow
  Click 5 → Envelope tears apart + final heartbreak image + message
           → Resets after 5 seconds
```

## Technical Notes

- Uses **Tailwind CSS via CDN** (no build step)
- Uses **Google Material Symbols** for icons
- Uses **Playfair Display** + **Be Vietnam Pro** fonts
- All animations are CSS-based (no JS animation libraries)
- No scrolling — `overflow: hidden` on html/body
- Config loaded via `fetch('config.json')` with fallback defaults
- Theme applied from config only (no UI theme picker)

## Deployment

Serve the folder with any static file server:

```bash
# Local testing
npx serve cupid_code/date-invitations/template-02

# GitHub Pages
# Push to repo and enable Pages — works as-is
```

No build step, no backend required. Tailwind is loaded via CDN.

## For New Customers

1. Copy this entire folder
2. Rename to `customer-{name}/` or use UUID prefix
3. Edit `config.json` with their details and preferred theme
4. Replace image URLs with custom reaction images
5. Customize places/vibes arrays for their date preferences
6. Deploy
