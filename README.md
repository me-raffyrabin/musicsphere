# φ · Golden Lattice

A single-file, cinematic 3D visualizer that renders a **Fibonacci sphere lattice** built from the golden ratio (φ) and brings it to life with audio. Upload an MP3 and the sphere reacts in real time — frequency bands light up across its surface, vocals flare red, and the music's pitch balance steers the rotation.

No build step, no dependencies to install. Just open the HTML file.

---

## ✨ Features

- **Golden-ratio geometry** — points are distributed with the [Fibonacci sphere](https://en.wikipedia.org/wiki/Fibonacci_lattice) algorithm, each placed at the golden angle (≈137.5°) for the most even possible spread. A φ-indexed web connects them into a lattice.
- **Cinematic rendering** — ACES filmic tone-mapping, Unreal bloom, vignette, scanlines, exponential fog, and a starfield backdrop for depth.
- **Feed φ values** — type comma-separated numbers (or hit **Load φ Series**) to modulate frequency, harmonics, resonance, and lattice density. The φ power series (`1, 1.618, 2.618, 4.236…`) locks the harmonic factor to ≈1.618×.
- **MP3 spectrum mapping** — upload audio and a Web Audio FFT maps the live spectrum across the lattice (bass → one pole, treble → the other). Louder bins grow brighter, larger, and push outward.
- **Vocal highlight** — points in the vocal band (~300 Hz–3.4 kHz) flare a distinct **red** when active.
- **Pitch-driven rotation** — bass/mid/treble intensities derive a 360° heading that steers the spin axis and direction (bass-led = clockwise, treble-led = counter-clockwise), eased with inertia for a smooth, slow drift.
- **Dockable panel** — swipe the control panel right to tuck it away; a peek arrow brings it back.

---

## 🚀 Getting Started

```bash
# clone or download, then simply open the file in a browser
open index.html
```

Or double-click `index.html`. A modern desktop browser (Chrome, Edge, Firefox, Safari) is recommended.

> **Note:** the page loads [Three.js](https://threejs.org/) from a CDN, so an internet connection is required on first load.

---

## 🎛️ Controls

| Control | What it does |
|---|---|
| **Frequency (Hz)** | Speed of the golden-ratio standing wave that ripples the lattice. |
| **Lattice Density** | Number of points on the sphere (snaps to Fibonacci numbers when feeding values). |
| **Resonance** | Amplitude of the breathing wave. |
| **Cinematic Bloom** | Strength of the glow / bloom post-processing. |
| **Feed φ Values** | Inject comma-separated numbers to modulate frequency, harmonics & pulse. |
| **Load φ Series** | Auto-fills and injects the first 16 powers of φ. |
| **Upload MP3** → **Play / Pause** | Load and play an audio file to drive the spectrum + rotation. |
| **Auto-Orbit** | Toggle the slow camera orbit. |
| Drag / swipe | Orbit the camera. Swipe the panel **right** to dock it; click the `‹` arrow to restore. |

---

## 🔊 How the audio mapping works

1. The MP3 is decoded locally (via an object URL — **nothing is uploaded anywhere**) and routed through a Web Audio `AnalyserNode` running a 2048-point FFT.
2. Each frame, the frequency spectrum is read and mapped to the lattice points using a perceptual power curve, so bass spreads across more points and treble compresses.
3. Per-point amplitude drives brightness, size, and outward displacement in a custom GLSL shader.
4. The spectrum is also split into **bass / mid / treble** bands whose balance yields a heading that steers the rotation.

> This is a frequency-*band* visualization, not source separation — instruments overlapping the vocal range will also tint red. True vocal isolation would require a stem-separation model (e.g. Demucs/Spleeter) applied beforehand.

---

## 🛠️ Built With

- [Three.js](https://threejs.org/) (r160, via ES module CDN) — WebGL rendering
- `EffectComposer` + `UnrealBloomPass` — cinematic post-processing
- `OrbitControls` — camera interaction
- Web Audio API — FFT spectrum analysis
- Custom GLSL shaders — per-point audio-reactive points

Everything lives in one self-contained `golden-ratio-sphere.html` file.

---

## 📐 The golden ratio, briefly

φ = (1 + √5) / 2 ≈ **1.6180339887**

The golden angle, 360° / φ² ≈ **137.5°**, is the rotation that distributes points most evenly around a sphere — the same pattern seen in sunflower seeds and pinecones. That's what gives this lattice its organic, non-repeating structure.

---

## 📄 License

MIT — do whatever you like.
