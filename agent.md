# Dean's Hyperframe navigation and voice preferences

These are Dean's standing preferences for this project. Read this file before any
voice-related task. AGENTS.md and CLAUDE.md link here for agent discovery.

## Navigation

- This GitHub checkout is the source of truth for reusable skills. The separate
  Hyperframe Project folder is the local production workspace.
- GitHub destination: https://github.com/deanlongio/hyperframes-student-kit.
  Only change Dean's repository; the original upstream is read-only.
- Read credentials from the active checkout's ignored `.env`; never print, commit,
  or copy secrets. The production workspace may link to the main checkout's file.
- Store the ElevenLabs key in `ELEVENLABS_API_KEY`. OpenVox defaults to
  `OPENVOX_BASE_URL=http://127.0.0.1:8000/v1`; verify local authentication if needed.
- Keep the main checkout and production workspace in place; repository renaming
  does not require renaming either local directory.
- New projects: `npm run new-video -- my-video`; keep media, transcripts and renders
  in that project's ignored folder. Use docs/WORKFLOW.md and docs/PROMPTS.md.
- This file overrides inherited provider defaults in docs/TOOLS-AND-API-KEYS.md.
- Edit canonical `.claude/skills/`, then run `npm run sync:skills` and
  `npm run check:skills`; keep the production workspace's skill copy synchronized.

## Provider order for all voice work

1. For transcription, speech generation, narration, or other voice-related work,
   ask Dean to manually enable the OpenVox server before attempting the workflow.
   If Dean has already confirmed it is enabled for the current workflow, do not
   ask again. Do not launch or enable the server yourself.
2. Try OpenVox first and discover its actual capabilities. Reuse existing valid
   audio and transcripts when appropriate.
3. Only use ElevenLabs as backup after no suitable OpenVox capability works for
   the requested task (unsupported capability, unavailable server after the
   manual-enable opportunity, or failed valid model/voice attempts).
   A temporary 429 is not evidence that OpenVox cannot work: retry as below.
4. Explain local unavailability and continue in text mode when the server is
   unavailable. For a voice deliverable that still needs completion, ElevenLabs
   is Dean's authorized backup. Honor any task-specific local-only constraint.
5. OpenVox transcription is available through `POST /audio/transcriptions`
   with multipart `file`, `model=whisper-large-v3-turbo`, `language=auto`,
   and `response_format=verbose_json` (Dean supplied this contract).
   Preserve the returned timestamp precision; never invent word timestamps if
   only segment timestamps are returned. Keep existing valid transcripts for comparison.
6. `npm run transcribe` and `scripts/transcribe-elevenlabs.mjs` call ElevenLabs
   directly. Use them only after the OpenVox-first checks; adding provider variables
   to `.env` does not automatically reroute these scripts.

## OpenVox speech API procedure

All paths below are relative to `http://127.0.0.1:8000/v1`.

1. Start with `GET /models` to discover available model IDs.
2. Before the first speech request for a selected model, call
   `POST /models/{model}/load` to warm it.
3. Call `GET /models/{model}/languages` to discover valid language codes.
4. Call `GET /models/{model}/voices?language={code}` to select a compatible voice.
5. Reuse that exact language code in the speech request body so synthesis and
   voice selection stay aligned. Do not assume example IDs are installed.
6. For a complete file, call `POST /audio/speech` with `model`, `input`,
   `language`, `voice`, and `response_format: "wav"`. Save the returned audio
   to a new local WAV file in the relevant project's assets or renders folder.
7. Add `play: true` when local playback is wanted; the server still returns audio.
8. Optional model controls go under `parameters`: `speed`, `temperature`,
   `top_p`, `repetition_penalty`, `cfg_weight`, and `exaggeration`.
   Use only controls supported by the selected model.
9. For incremental playback set `stream: true` and parse SSE events named
   `response.created`, `audio.chunk`, and `response.completed`.
10. Decode `audio.chunk.data.audio` from base64 WAV bytes before playback.
11. On HTTP 429, wait and retry; only one generation or preload job can run at
    once. Respect Retry-After if supplied, use bounded backoff, and report a
    persistent busy state rather than looping forever or immediately falling back.
12. If a requested voice is missing, fetch voices again for the same model and
    language and choose a valid replacement. Never guess a voice ID.
13. If the server is unavailable, explain that local voice output is currently
    unavailable and keep responding in text; apply the fallback policy above.

Example only — discover and validate the model, language and voice first:

```json
{
  "model": "kokoro",
  "input": "Your spoken reply text here",
  "language": "en",
  "voice": "af_bella",
  "response_format": "wav",
  "play": true,
  "parameters": {"speed": 1.0, "temperature": 0.7, "top_p": 0.9}
}
```

For streaming, use a discovered compatible model (the supplied example was
`chatterbox-turbo-small`), a validated language and voice, the desired input,
and `stream: true`.

Add speech to responses when voice is requested or the workflow calls for audible
feedback. The written response remains authoritative. Audio is additional output,
not a substitute for accuracy. Do not generate unsolicited speech for routine text
work. This setup task does not itself request speech or a live API call.

## Authoritative skill checkout

Maintain reusable skills in this main checkout and sync the production copy after
reviewing existing changes. Keep machine-specific capability logs, private voice
IDs, footage, renders and credentials local. Legacy-project removal was explicitly
authorized in both checkouts; do not infer permission to delete other projects.
Commit or push only when requested.
