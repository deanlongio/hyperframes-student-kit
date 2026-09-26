> Updated: the same 12 legacy projects have now also been removed from the main
> GitHub checkout at Dean's request. Both checkouts are cleaned. Earlier statements
> below about retaining main-checkout examples are historical. Git history remains;
> no archive copy was made. See the main checkout's MAIN-CHECKOUT-CLEANUP.json.

# Resource audit — 26 September 2026

Current decision: remove optional legacy productions from Dean's local production
workspace to save space. The useful skills, 406-card library, scene templates and
test fixtures stay. On Dean's subsequent authorization, all 12 legacy project
folders listed below were deleted locally after dependency checks and reference
updates. About 300 MB (286 MiB) of allocated files were removed; actual free-space
change can differ. No local archive copy was made. The main GitHub checkout's
example folders and Git history were not deleted.

The inventory below records the pre-cleanup state. Its original archive advice is
superseded by this removal decision. See LOCAL-CLEANUP.json for the exact scope.

## What is here

`video-projects/` contains 12 tracked teaching projects plus Dean's untracked/ignored
projects (`dean-furniture`, `krav maga drill #1`, and `demo`). Do not classify personal
projects as legacy just because their names lack a brand prefix.

| Resource | Observed size / role | Recommendation |
| --- | --- | --- |
| `aisoc-app-release` | 24.4 MiB; editable app-release composition | Optional product-launch technique reference; archive complete folder |
| `aisoc-hype` | 22.5 MiB; editable promotional sequence | Optional hype/promo reference; archive complete folder |
| `aisoc-lesson-5-1` | 58.2 MiB; presenter/educational overlays | Optional speech/teaching reference; archive complete folder |
| `may-shorts-6`, `may-shorts-18`, `may-shorts-19` | 61.5 MiB combined; legacy short-form compositions | Archive if not maintaining the old examples; preserve paths or update legacy skill links |
| `claude-edit-intro`, `clickup-demo`, `first-agent-promo`, `golden-ratio-demo`, `hyperframes-sizzle`, `linear-promo-30s` | Remaining six tracked demos | Optional camera, layout, product/demo and motion references; archive after dependency review |
| `style-library/` | 406 cards: 106 Vox-inspired and 300 Kallaway; about 4.4 MiB allocated | Keep; strongest reusable source of layout/motion options |
| `style-templates/` | Two scene templates; about 80 KiB allocated | Keep; graph-paper background and glass/presenter layout |
| `examples/showcase/` | Three finished MP4s; about 99 MiB allocated | Optional reference viewing; no editable source included and not required by skills |
| Root `assets/` and `DESIGN.ais-example.md` | AIS logo, background, guide and colour tokens | Legacy identity examples only; keep with archived references, never use as Dean's default brand |
| `examples/starter`, `examples/short-form`, `examples/editing` | Starter and synthetic validation fixtures | Keep; used by project creation or tests |
| `.claude/skills/` and `.agents/skills/` | Canonical skills and generated Codex mirror | Both needed by current routing; intentional duplication |
| `AGENTS.md` and `CLAUDE.md` | Same standing guide for two runtimes | Intentional duplication; maintain together |
| `node_modules/`, package files, scripts | Local runtime and toolchain | Keep; not redundant reference footage |

The 12 tracked project directories total approximately 285.7 MiB of logical file
sizes at audit time. The three AIS-named projects account for about 105.1 MiB.
These are inventory sizes, not promised disk savings: cloud placeholders,
compression and Git history affect actual reclaimed space. Deleting tracked files
from the checkout would not remove their historical copies from Git.

## Why archive instead of deleting individual videos

The HTML, timestamps and assets in a legacy production form a working example.
Removing only its MP4s leaves broken playback even though the editing skills still
work for new projects. These productions provide examples of techniques, but the
card catalog already exposes reusable layouts without needing the old recordings.
Archive a whole project with its dependencies, or keep just selected references
and explicitly label them as non-renderable source examples.

This is a dependency and resource-role audit, not a frame-by-frame quality ranking
or byte-for-byte duplicate-media scan. A filename containing AIS does not by itself
prove redundancy. Library cards are draft assets: lint/render/inspect chosen cards
with the actual brand, copy and aspect ratio before use.

## Dependencies to handle if removal is approved

- `.claude/skills/short-form-video/SKILL.md` and its mirror reference May Shorts 18/19.
  This is the legacy maintenance skill, not the route for new reels.
- `.claude/launch.json` opens `video-projects/claude-edit-intro`; change its target
  before archiving that project. No launcher configuration was changed here.
- `docs/superpowers/` contains historical Linear/sizzle plans with old paths.
- `scripts/preflight-all.mjs` scans the current project directories dynamically;
  it does not require a fixed list of the 12 examples. The May Shorts 19 path in
  `scripts/preflight.mjs` is only a usage comment.
- `scripts/new-video.mjs` copies `examples/starter`, not an AIS project. Current
  test fixtures do not require legacy production recordings.
- A static scan found no local file references from library card HTML into the
  legacy project folders, and no missing local dependencies in that card scan.
  The glass scene template intentionally needs a user-supplied `assets/source.mp4`.
- README/showcase documentation describes the three finished example exports;
  update those links if removing them. Preserve attribution/licence notices for
  any retained third-party resources.

If approved later, move the complete legacy set to an archive outside the active
project tree, update the affected paths, then rerun skill-link checks and preview
any retained example. No need to delete them to improve future editing behavior:
brand routing now explicitly prevents their identity from leaking into new work.

## Changes made from this session

Curated the existing `short-form-edit` skill instead of creating a competing skill.
Added agency / Krav Maga / per-client brand routing, speech / nonverbal / hybrid
modes, complete movement and readable overlay checks, truthful drill terminology,
and a separate ending review for action, text and music. Established a private brand
library with an approved Krav Maga direction and an agency profile whose missing
visual identity is explicitly recorded. No logo, agency colour palette or client
identity was invented. See `brands/README.md` for where to save assets.

Validation: both edited skills passed the skill-creator validator; the generated
Codex mirror contains 95 synchronized files with zero discrepancies. Checked links
in the edited entrypoints and walkthrough; AGENTS.md and CLAUDE.md match. The initial curation did not remove media; the later authorized local cleanup
is recorded below. No renders or publication were performed during curation.

## Completed local cleanup and reference handling

The local launcher now opens the retained `video-projects/demo`. The legacy May
Shorts skill treats those examples as optional; the self-contained guidance stays.
Local README, migration notes and standing guides reflect the cleanup. `agent.md`
references Dean's retained furniture project and generic project paths, not the
removed examples. Historical Linear planning documents remain historical records,
not required runnable instructions. Main-checkout source skills receive the curated
updates separately; local production deletions must not be copied there as a patch.

“Archive” means retain a recoverable copy elsewhere; moving files elsewhere on the
same disk does not save space. No archive is needed for these optional examples
because their tracked source still exists in the main checkout and Git history.
The 99 MB showcase exports remain optional references and were outside this
12-folder cleanup. No private footage or reference renders were deleted.
