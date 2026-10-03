# Photo stop-motion, visual memes, and seamless loops

Use when the brief calls for animating supplied photographs, a repeated gesture,
or an infinite-loop reel. Preserve the user's chosen joke and current revision.
The principles below generalize; the birthday cake example does not prescribe
its palette, length, exposure rate, or font for other videos.

Stop motion and repeated gestures do not by themselves imply a seamless-loop
style. Apply the seam and cyclic-audio guidance below only when the brief calls
for an intentional loop. Otherwise, choose music phrasing, overlays, and an
ending to suit the edit; music does not need to loop.

## Let the action explain the joke

- Distinguish the Instagram post caption from burned-in video text. A supplied
  caption does not automatically need to appear on screen.
- Start with the gesture. Add only the words or symbols needed to recognize it.
  A visual meme may need two digits instead of an explanatory headline. Do not
  force an intro, CTA, end card, artificial suspense, or three speech-led opening
  variants onto an already specified simple loop.
- Interpret “less text” as reducing reading load, not necessarily removing every
  useful symbol. If the user later restores a small element, retain the accepted
  loop, framing, music, and restraint while curating that element.
- Attach labels to the action when that improves comprehension: put a digit near
  its matching held object, change its position and tilt with the pose, and keep
  it clear of the face, hands, and object surface. Use colour with a visible role
  (for example, matching the object's colour). “Gen Z” is not a requirement for
  slang paragraphs, random stickers, or visual clutter.

## Build a readable photo cycle

Inspect the poses before deciding the order. Identify opposing gesture states
and useful intermediate poses; choose a small coherent subset when other camera
angles or reaction shots interrupt the requested motion. Record selected and
omitted photos with their reasons. Do not claim every supplied photo was used
unless the selected timeline confirms it.

Align a stable landmark such as the face or torso across the photos, then verify
the entire moving gesture. A face-aligned crop can still cut off an outstretched
hand or object. Inspect both extremes at native size and phone size; widen the
crop when needed. Preserve originals and record crop coordinates.

Use frame-aligned exposure durations. Hard pose swaps and repeated photos are
intentional for requested stop motion; they override aesthetic defaults for
smooth entrances, transitions, and unique B-roll scenes. Keep HyperFrames timing,
clip classes, synchronous paused timelines, and finite-duration contracts.
Use pose anchors in the plan; mark transcription and speech checks inapplicable.

## Design the seam, not just the last frame

Choose a cyclic pose order that preserves the direction and rhythm of the
gesture on replay. Matching first and last images alone can create a double hold.
When useful, split one normal exposure between the end and start. For example,
at 24fps, a six-frame exposure can become three closing frames plus three opening
frames: replay still shows that pose for six frames, not twelve. This is an
example, not a required frame rate or duration.

Include overlays in the seam design. Digit positions, rotations, shadows and
animation phase must agree across the closing/opening exposure. Avoid a one-time
entrance or outro fade in a continuous loop. Treat the seam as an ordinary motion
beat instead of adding an ending pause.

For an intentional seamless loop, make the music cyclic too: select whole
musical phrases and align the returning
downbeat. For locally synthesized music, wrap note tails into the beginning;
for an existing track, use a suitable musical edit and audition the seam. An
intro/outro fade or zero padding can make each restart obvious. Preserve audio
headroom and measure the final encoded mix, since AAC can change true peaks.

## Verify the delivered loop

- Inspect contiguous decoded frames spanning end → beginning, in addition to
  the ordinary sequence and each extreme pose. Check cadence, crop, label
  placement, and any one-frame flash or text glitch.
- Review at least two consecutive repeats with sound when that modality is
  available. If it is unavailable, record frame-strip and signal-analysis limits;
  neither waveform continuity nor successful playback is a listening pass.
- First/last pixel differences can reveal a mismatch, but compression causes
  small differences even for the same source pose. Do not turn a numerical score
  into proof of a perceptually seamless loop. Player/platform latency is separate
  from the encoded seam.
- If fast capture produces a demonstrated one-frame artifact, retry screenshot
  capture (for supported CLI versions, `--experimental-fast-capture=false`) and
  inspect the same encoded window. Do not disable fast capture universally.
- Keep one current authoring path. Archive obsolete generators with their
  revisions so a rebuild cannot silently restore removed text or an old ending.
  Store reusable lessons without copying private photos, absolute personal media
  paths, credentials, or renders into the skill library.
