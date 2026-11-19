# S-3340 · Semi-modular synthesizer simulator

*English · [Italiano](README.it.md)*

A browser simulator of an analog semi-modular synthesizer laid out like the Behringer Crave: 3340 oscillator, ladder filter, 32-step sequencer and Poly Chain up to 16 voices. It runs on computers, tablets and phones, and also **offline** as an installed app.

> Unofficial project, not affiliated with Behringer / Music Tribe. "Behringer" and "Crave" are trademarks of their respective owners and are mentioned only to describe the instrument the layout is based on. Graphics, code and sounds are original.

> The interface is in English, with an **IT** button in the header to switch to Italian (the choice is remembered). Panel labels use the same names as the hardware.

## Features

- **3340 VCO**: reverse sawtooth and pulse with adjustable width (PULSE WIDTH), FM, width modulation, slight analog drift.
- **Mixer** oscillator / noise, with external audio input.
- **4-pole ladder filter (24 dB/octave)**: low-pass and high-pass, resonance up to self-oscillation.
- **Envelope** Attack / Decay / Sustain with SUSTAIN ON/OFF switch, and **VCA** in ENV or always-open mode (drone).
- **LFO** triangle / square with selectable destinations.
- **Full patch bay** with internal connections (normalizations): a cable in an input jack replaces the internal connection.
- **32-step sequencer**: gate 1–8, rest, accent, glide, ratchet, swing, live recording, 8 banks × 8 patterns.
- **Arpeggiator**, HOLD, live transposition.
- **Poly Chain**: 1 to 16 voices.
- **Sequencer settings**: tempo input (1PPS, 2PPQ, 24/48 PPQN, CV), assign out, clock type and clock edge.
- **MIDI** in/out via Web MIDI (channel, THRU, note output, MIDI clock output with start/stop).
- **On-screen keyboard** and computer keyboard (A W S E D F …, Z/X for octave, space = PLAY).
- **Factory presets**, each with its own example pattern, and **user presets**, with export and import of the **whole session**.

## Ranges (from the official specifications)

| Parameter | Range |
|---|---|
| Oscillator | 8.18 Hz – 8.37 kHz, FREQUENCY ±1 octave |
| Pulse width | 5–95 % |
| LFO | 0.1–350 Hz |
| Cutoff | 20 Hz – 20 kHz |
| Attack / Decay | 2 ms – 3 s / 2 ms – 5 s |
| Sustain, ENV out | 0–8 V |
| Glide | 0–2 s |
| Inputs / outputs | ±5 V; gate 0/+5 V |
| Trigger inputs (PLAY/STOP, RESET, HOLD, ENV GATE, TEMPO as clock) | active above 3.2 V |

Values not given in the specifications (sequencer tempo 40–240 BPM, swing, knob curves) are the author's choices.

## Quick start

1. Open the page and tap **▶ Switch on** (browsers only enable audio after a tap).
2. Pick a sound from the **PRESET** menu, then play the keyboard at the bottom or press **PLAY/STOP** to hear the preset's pattern.
3. To patch a cable, tap an **output** and then an **input**. Tapping an input that is already patched removes the cable.
4. The **?** button opens the guide with every key combination.

## Presets and sessions

From the **PRESET** menu:

| Menu item | What it does |
|---|---|
| ＋ Save current sound… | Saves knobs, switches, cables and voices under a name (also with the SAVE button); optionally the working pattern too |
| ★ name | Recalls one of your presets |
| ✕ Delete «name» | Deletes the loaded preset |
| ⇩ Export session | Creates `S3340-sessione.json` with your presets, the current sound, tempo, all 64 patterns and the settings |
| ⇧ Import session or presets | Adds the presets in the file and, if you confirm, restores the session |

Every factory preset carries an example pattern. Loading the preset puts the pattern into the working pattern (press PLAY/STOP to hear it); saved banks are never touched. If the working pattern has unsaved changes, the simulator first asks whether to replace it or load the sound only.

Sequencer **patterns** have their own memory (8 banks × 8 patterns), as on the hardware: hold **SHIFT + PLAY for 2 seconds**, choose the pattern with the pads (PATTERN + pad for the bank) and confirm with **SHIFT + REC**.

Everything is stored in the browser. The online version and the installed offline version have separate memories: use Export and Import to move between them.

## Offline use (iPhone, iPad, Android)

The simulator is a PWA: after the first visit it also works without a connection.

- **iPhone / iPad (Safari)**: open the page, tap Share → **Add to Home Screen**.
- **Android (Chrome)**: menu ⋮ → **Install app**.

After updating the files on GitHub, open the app once while online to download the new version.

## Publishing on GitHub Pages

1. Upload the contents of this folder to the repository (it must be **public**, unless your plan allows Pages on private repositories).
2. Settings → **Pages** → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. After a couple of minutes the page is available at the address shown by GitHub.

## Files

| File | Contents |
|---|---|
| `index.html` | The complete simulator (interface, audio engine, embedded fonts) |
| `sw.js` | Service worker for offline use |
| `manifest.webmanifest` | Installable app data |
| `icon-*.png` | App icons |
| `OFL-*.txt` | Licenses of the Barlow and JetBrains Mono fonts (SIL Open Font License) |
| `README.md`, `README.it.md` | This guide in English and Italian |

## Compatibility

- Audio: recent Chrome, Edge, Firefox and Safari (AudioWorklet, with an automatic fallback when unavailable).
- MIDI: Chrome and Edge on computers and Android. Safari and every browser on iPhone/iPad do not support Web MIDI.

## Technical notes

The audio engine runs in an AudioWorklet at the full sample rate: polyBLEP anti-aliased oscillators, zero-delay-feedback (ZDF) ladder filter with saturation, exponential envelopes, patch bay processed sample by sample.
