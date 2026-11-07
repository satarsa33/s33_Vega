# S33 - Vega

An **8-voice polyphonic synthesizer** in the style of the early 1980s (Juno-106 / Jupiter-8 family), part of the S33 family: a fixed panel of faders, no cables, instant sound.

Made for **Chrome on the Mac** with a MIDI keyboard. It is a **PWA** in a single HTML file, with no dependencies (the panel fonts come from Google Fonts and fall back to system fonts offline).

> A personal project of the S33 family. The full user manual, in Italian, is in [MANUALE.md](MANUALE.md).

---

## Features

- 8 voices in one AudioWorklet: band-limited DCO (saw, pulse with PWM, sub, noise), 4-step HPF, 24 dB resonant ladder VCF with envelope polarity, VCA env/gate, ADSR, LFO with delay
- Stereo **chorus I / II / I+II** (Juno-style)
- **Arpeggiator** (up, down, up & down, random; 1–3 octaves; hold) and **Poly / Unison / Mono** with detune and glide
- **Memory**: factory bank A, user banks B–D, write protection for unsaved sounds, save/load to file, MIDI Program Change 0–31
- **Juno-106 import**: `.106` libraries and `.syx` patch dumps, with a browsable library
- Board-ready: inside the **S33 - Board** it uses the shared audio engine and MIDI, and its arpeggiator follows the Clock

## Quick start

1. Open `index.html` in **Chrome**.
2. Press **POWER** and allow MIDI access.
3. Play the MIDI keyboard, the on-screen keys or the computer keys (A–K, Z/X octave, Space sustain).

### Install as an app

```bash
cd "v8 (1.1.1)"
python3 -m http.server 8000
# open http://localhost:8000 in Chrome → ⋮ menu → Install S33 - Vega
```

Browser storage is per address: banks opened as a file, from `localhost` or from GitHub Pages are kept separately. Use **SAVE FILE / LOAD FILE** to move them.

## Folder structure

```
index.html              the synth
manifest.webmanifest    PWA manifest
sw.js                   service worker (offline cache)
icons/                  icon.svg, 192/512, maskable, apple-touch, favicon
README.md               this file
MANUALE.md              user manual (Italian)
```

After publishing a new version, change `VERSIONE` in `sw.js`.

## Use

Personal project, free to study and modify. No warranty of any kind. Juno-106 patch files are not included: load your own.
