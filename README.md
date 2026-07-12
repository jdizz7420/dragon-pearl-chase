# 🐉 Dragon's Pearl Chase

A cheerful, kid-friendly arcade game for ages 5–8 that also teaches the cultural
significance of the Chinese dragon. Built as a single self-contained `index.html`
with **no dependencies and no build step** — it runs offline in any modern browser,
including the Silk browser on Amazon Fire tablets.

## How to play

- **Drag your finger** (or click and drag) to fly the dragon around.
- **Collect the golden pearls** ✨ to score points and grow longer.
- **Dodge the Nián monster** — a little mischief-maker to avoid.
- Fill the pearl goal to finish a level. Each level gets a bit harder (more Nián,
  moving faster).

## Learn as you play

Between every level, a **Dragon Facts** card appears with a short, kid-friendly
lesson about Chinese dragons and traditions, each with its own illustration and a
**Read to me** button that plays pre-recorded narration (browser text-to-speech
is used only as an automatic fallback) for pre-readers:

Friendly Dragons · Rain Bringers · The Glowing Pearl · The Dragon Dance ·
The Nián Monster · Made of Many Animals · The Emperor's Symbol ·
Year of the Dragon · Guardian Dragons

## Pick your dragon

Three dragons to choose from (your choice is remembered):

- **Jade** — the classic green Chinese dragon
- **Opal** — an iridescent teal-to-purple dragon
- **Blossom** — a pink dragon

## Run it

Just open `index.html` in a browser. That's it.

Or serve it locally:

```bash
python3 -m http.server 4599
# then visit http://localhost:4599/
```

### Playing on a Kindle Fire tablet

1. Copy `index.html` to the tablet (USB, email, or a shared folder).
2. Open the Silk browser and go to `file:///sdcard/Download/index.html`.
3. Use the browser menu to **Add to Home screen** for an app-like icon that works
   offline.

## Notes

- Almost everything is drawn with the HTML5 Canvas and inline SVG — the only
  bundled assets are the 9 small narration clips in `audio/`.
- Sound effects use the Web Audio API. The Dragon Facts narration is
  pre-generated once (offline, with the open-source [Kokoro](https://huggingface.co/hexgrad/Kokoro-82M)
  TTS model) and shipped as small MP3s, so "Read to me" sounds natural and
  still works with no internet connection. If a clip ever fails to load, it
  falls back to the browser's built-in speech synthesis automatically.

---

🤖 Built with [Claude Code](https://claude.com/claude-code)
