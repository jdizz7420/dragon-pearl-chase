# Dev Log

A running history of Dragon's Pearl Chase — what changed in each version and
why, so the game's evolution (and the reasoning behind it) is easy to show off.

## Format

Each entry: version, date, what changed, and the decision(s) behind it.
Newest at the top.

---

## v0.4 — 2026-07-12

- Fixed silent sound effects on iPhone: the Web Audio `AudioContext` was
  created on the Play tap but never explicitly `resume()`d. **Why:** iOS
  Safari frequently leaves a freshly-created (or backgrounded) context
  "suspended" even inside a genuine tap, unlike desktop browsers, which
  silently dropped every beep (pearl pickup, bonk, level-up chime,
  celebration fanfare) with no error. `audio()` now resumes the context
  whenever it's found suspended, self-healing on every beep call.

## v0.3 — 2026-07-11

- Added a celebratory animation between finishing a level and the Dragon Fact
  card: confetti bursts and rains down, a rotating gold starburst, and a
  bouncy "Level N Complete!" title with a cheerful chime, then it
  auto-advances into the fact. **Why:** the cut from gameplay straight to a
  text card felt flat; kids should get a real payoff for finishing a level.
- Moved the "Read to me" button below "Keep flying!" on the Dragon Fact card
  so the primary action is on top. **Why:** requested for clearer visual
  hierarchy.
- Replaced the "Read to me" narration with pre-recorded audio clips (one per
  fact, generated offline with the free, open-source Kokoro TTS model),
  falling back to the browser's speech synthesis only if a clip fails to
  load. **Why:** the default browser voice was robotic and inconsistent
  across devices; pre-rendering keeps narration natural-sounding while
  preserving the game's fully-offline, zero-dependency design (an
  ElevenLabs-based alternative was evaluated but its free tier blocks API
  access to voices, so Kokoro was used instead).

## v0.2 — 2026-07-10
**Commit:** `9264159` — Add level-complete celebration animation

- Added a celebration animation that plays when a level is completed.

## v0.1 — 2026-07-10
**Commit:** `bedb876` — Add Dragon's Pearl Chase game

- Initial build: single self-contained `index.html`, no dependencies, no
  build step. **Why:** needs to run offline in the Silk browser on a Kindle
  Fire tablet with zero setup.
- Drag-to-fly controls, pearl collection, Nián monster to dodge, increasing
  difficulty per level. **Why:** simple, forgiving mechanics for ages 5–8.
- Dragon Facts card between levels with a "Read to me" TTS button. **Why:**
  the game should teach the cultural meaning of the Chinese dragon, not just
  be an arcade loop, and pre-readers need it read aloud.
- Three selectable dragons (Jade, Opal, Blossom), choice remembered. **Why:**
  a small personalization touch for replay value.
- Everything drawn with Canvas/inline SVG, sound via Web Audio API. **Why:**
  keeps the game asset-free and fully offline.
