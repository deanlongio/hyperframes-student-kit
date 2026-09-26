# Reels and YouTube Shorts

Use `short-form-edit` for speech, nonverbal or hybrid reels, YouTube Shorts, or
short advertisement. It defaults to 1080x1920. Request a separately composed
1920x1080 version when needed; a center crop is not a second composition.

## Start

Run `npm run new-video -- my-reel`, then ask Codex (`$short-form-edit`) or Claude
Code (`/short-form-edit`) to edit your local recording into that project. State
the audience, intended action, target duration, and any brand preferences.
The starter is landscape; the skill must set the reel's composition dimensions,
layout, and metadata to 1080x1920 before authoring. Keep all source footage and
outputs inside the new project.

1. Select the owner and brand from [the brand library](../brands/README.md).
   Record that profile and campaign-specific overrides in the project DESIGN.md.
2. Inspect the source and choose speech, nonverbal or hybrid editing. For retained
   speech, follow `agent.md` and its OpenVox-first procedure; reuse valid transcripts.
   For silent footage, use visual action anchors and skip voice services.
3. Establish a truthful opening, complete action/argument and deliberate ending.
   Nonverbal reels need a concise intro and closing overlay or end frame.
4. Build purposeful cuts, captions where relevant, brand-aware overlays and sound.
   Keep the performer/product and outcome visible. Do not inherit AIS branding.
5. Validate, preview, render a draft and inspect the encoded video. Review the final
   2–3 seconds separately: action, text reading time, final frame and music release.
6. Resolve problems, export a new final version and record verification evidence.
   Listen when an audio-capable review surface is available; disclose any limit.

See [tools and provider setup](TOOLS-AND-API-KEYS.md). New private footage stays in
its own project. The reusable card library does not need legacy production videos;
see [the resource audit](RESOURCE-AUDIT.md) for retention recommendations.

## Validate from the repository root

```sh
npm run validate:short-form -- video-projects/my-reel
npm run validate:footage -- video-projects/my-reel
node scripts/preflight.mjs video-projects/my-reel
```

The first validator reads `assets/plan.json`, `assets/transcript.json`, and
`assets/edit-decisions.json`. The second reads the plan and, for moving footage,
`assets/footage-ledger.json`, checks hashes, and confirms referenced files exist.
Follow the [plan schema](../.claude/skills/short-form-edit/references/plan-schema.md).
Use the [reference worksheet](../.claude/skills/short-form-edit/references/reference-analysis.md)
when analyzing a supplied reference video.

Try the synthetic fixture without a recording or API key:

```sh
npm run validate:short-form -- examples/short-form
npm run validate:footage -- examples/short-form
npm test
```

The fixture contains invented words and timing data, not a rendered reel.
Validators check structure and declared timing. They do not prove a compelling
hook, factual claims, rights to footage, correct visual cropping, or audible sync.
The skill's quality gates require watching and listening to the actual output.
