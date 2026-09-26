# Video brand library

Choose the brand separately from the video format. An agency reel, martial-arts reel,
or client reel can use speech, silent performance, product footage, or a mixture.

| Work | Brand home | Current status |
| --- | --- | --- |
| DEANLONG.io agency / digital marketing and growth | `brands/deanlong-io/BRAND.md` | Business purpose known; visual identity not supplied |
| Dean's Krav Maga | `brands/krav-maga/BRAND.md` | Dark cinematic direction and accepted reel recorded |
| Each client | `brands/clients/<client-slug>/BRAND.md` | Separate identity per client; start from `_template/BRAND.md` |

In each brand home save:
- `BRAND.md`: approved name, colours with hex codes, typography, tone, motion,
  intro/outro rules, sound, reference links, and what remains undecided.
- `assets/logos/`: exact SVG and transparent PNG variants; label light/dark usage.
- `assets/fonts/`: supplied licensed font files and usage notes.
- `assets/references/`: approved example frames, reels, or a text file of links.
- `assets/audio/`: approved music/stings plus licence/source and permitted uses.
- `assets/brand-guide.pdf`: the original guide, if available.

Create asset subfolders only when adding files. A reference is inspiration unless
explicitly approved as the identity. Never invent a missing logo or treat AIS
teaching assets as one of these brands. The agency display name is DEANLONG.io, as corrected by Dean.

Brand profiles and client assets stay local and ignored by Git. The reusable
blank template and this guide can be tracked. Do not put client files in the template.

Each `video-projects/<slug>/DESIGN.md` records the chosen brand path, profile date,
content mode (speech / nonverbal / hybrid), audience, objective, and project-specific
overrides. Copy the actual used brand assets into the project's `assets/brand/`
and snapshot the used rules in DESIGN.md so future profile changes do not change
old renders. The current brief overrides a saved profile; a saved profile overrides
library colours and starter examples. Never blend client and agency branding by default.
