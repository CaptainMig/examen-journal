# Examen — Daily Decision Journal

**Live:** [examen-journal.vercel.app](https://examen-journal.vercel.app)

The *examen* is a centuries-old daily practice of review — recollect,
discern, resolve. This app rebuilds it as a decision instrument.

You record a decision, your gut read, and seven measurements of the
situation. The NERVA kernel weighs them, applies the brakes, and
returns one of five verdicts: **Commit · Hold · Wait · Consult ·
Toxic**. Later, when the check-in date arrives, you score what
actually happened. The point is not the verdict — it is the record.

## How a reading works

The written decision is a label; the kernel never reads your words.
It reads the sliders:

| Axis | Question it asks |
|---|---|
| Evidence (E) | Which way do the facts lean? |
| Provenance (P) | How verified are those facts — hearsay to firsthand? |
| Uncertainty (H) | How legible is the situation? |
| Interference (Φ) | How emotionally charged are you right now? |
| Stakes (S) | How much does this matter? |
| Blast radius (B) | How many others bear the cost? |
| Time pressure (T) | How fast is the window closing? |

The kernel **multiplies, it does not average** — one weak measurement
caps the whole reading. Strong evidence from an unverified source
stays weak. It is a brake, not an oracle. The "held down by" line in
the instrument names whichever measurement is doing the holding.

Four structural rules can override the base verdict: **One-Way Brake**
(irreversible + insufficient confidence → Consult), **Desolation**
(never make a change while the inner weather is bad — Ignatian in
origin), **Blast Consult** (others bear the cost → they get a voice),
and **Urgency Escalation** (when waiting is itself a decision).

## Kernel — NERVA v11.1

Runs the NERVA mixed-state kernel: effective evidence `E·P`, coherence
`C = (1−H)(1−γΦ)`, mixed-state radius `r = C·|E·P|`, von Neumann
entropy from the Bloch eigenvalues. Raw telemetry (r mixed, S_vN) is
displayed untouched.

**v11.1 is a consumer calibration of NERVA v11** — the reference math
is unchanged in [nerva-v10](https://github.com/CaptainMig/nerva-v10).
Delta: decision-confidence readout softened to `rMixed^0.72`;
`commitBase` 0.55 → 0.42, `commitSlope` 0.25 → 0.20; the Desolation
rule acts on Φ directly (it was unreachable under the strict curve).
These constants are **provisional pending scored outcomes** — the
app's own falsification loop (fifty scored outcomes) is the
calibration instrument. Every logged entry carries its
`kernelVersion` so records stay honest across revisions.

## Architecture

One file. `index.html` — vanilla JS, no framework, no build step, no
dependencies beyond Google Fonts.

**Privacy is structural, not promised:** entries live only in the
browser's localStorage on the device (`examen_v1`). No server, no
account, no analytics on entries. Nothing leaves the device — which
also means clearing site data deletes the journal, and devices do
not sync.

`examen_capture.html` and `examen_console.html` are the original
capture/console pair, kept for continuity; `/console` routes to the
console.

## Status

Private beta ahead of an App Store build (Capacitor wrap: native
storage, check-in notifications, export). A Starpoint LLC project.
