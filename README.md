# GML

**Gyro Motion Language (GML)** — a framework that translates continuous gyroscope data (tilt, rotation, movement patterns) into meaningful shared digital experiences at scale.

## Motion Primitives

Twelve distinct gestures turn every smartphone into an expressive instrument. The animations below show exactly how each movement should be performed.

<table>
<tr>
<td align="center" width="200">
  <img src="docs/animations/groundswell.svg" alt="GROUNDSWELL animation" width="160"/><br/>
  <strong>GROUNDSWELL</strong><br/>
  <sub>Lean top edge forward · hold ≥ 1.5 s</sub><br/>
  <sub><i>Conviction · Momentum</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/tremor.svg" alt="TREMOR animation" width="160"/><br/>
  <strong>TREMOR</strong><br/>
  <sub>Shake rapidly left–right · 3–7 Hz</sub><br/>
  <sub><i>Tension · Risk awareness</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/orbit.svg" alt="ORBIT animation" width="160"/><br/>
  <strong>ORBIT</strong><br/>
  <sub>Hold flat · rotate in a slow circle</sub><br/>
  <sub><i>Alignment · Synthesis</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/anchor.svg" alt="ANCHOR animation" width="160"/><br/>
  <strong>ANCHOR</strong><br/>
  <sub>Hold completely still · ≥ 3 s</sub><br/>
  <sub><i>Resolve · Groundedness</i></sub>
</td>
</tr>
<tr>
<td align="center" width="200">
  <img src="docs/animations/surge.svg" alt="SURGE animation" width="160"/><br/>
  <strong>SURGE</strong><br/>
  <sub>Snap phone upward sharply · &lt; 0.5 s</sub><br/>
  <sub><i>Excitement · Energy</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/pulse.svg" alt="PULSE animation" width="160"/><br/>
  <strong>PULSE</strong><br/>
  <sub>Nod forward and back · 0.5–1.5 Hz</sub><br/>
  <sub><i>Agreement · Active support</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/pivot.svg" alt="PIVOT animation" width="160"/><br/>
  <strong>PIVOT</strong><br/>
  <sub>Snap 90° yaw rotation · hold 1.5 s</sub><br/>
  <sub><i>Reframing · Course correction</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/cascade.svg" alt="CASCADE animation" width="160"/><br/>
  <strong>CASCADE</strong><br/>
  <sub>Tilt ever deeper forward · 3–10 s ramp</sub><br/>
  <sub><i>Escalation · Building pressure</i></sub>
</td>
</tr>
<tr>
<td align="center" width="200">
  <img src="docs/animations/lean.svg" alt="LEAN animation" width="160"/><br/>
  <strong>LEAN</strong><br/>
  <sub>Tilt left edge down · hold ≥ 1.5 s</sub><br/>
  <sub><i>Scepticism · Weighing options</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/bank.svg" alt="BANK animation" width="160"/><br/>
  <strong>BANK</strong><br/>
  <sub>Tilt right edge down · hold ≥ 1.5 s</sub><br/>
  <sub><i>Confidence · Commitment</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/veer.svg" alt="VEER animation" width="160"/><br/>
  <strong>VEER</strong><br/>
  <sub>Twist phone left · hold ≥ 1.5 s</sub><br/>
  <sub><i>Redirection · Dissent</i></sub>
</td>
<td align="center" width="200">
  <img src="docs/animations/sweep.svg" alt="SWEEP animation" width="160"/><br/>
  <strong>SWEEP</strong><br/>
  <sub>Twist phone right · hold ≥ 1.5 s</sub><br/>
  <sub><i>Clearance · Decisive action</i></sub>
</td>
</tr>
</table>

## Full Component Reference

See [GML_COMPONENTS.md](./GML_COMPONENTS.md) for the complete structured specification of all twelve motion primitives including detection logic, semantic meaning, and visualization ideas.

| Component | Axis | Threshold | Meaning |
|-----------|------|-----------|---------|
| **GROUNDSWELL** | Pitch forward | 15° · hold ≥ 1.5 s | Momentum, conviction, forward pressure |
| **TREMOR** | Roll lateral | 5° amplitude · 3–7 Hz | Tension, stakes, risk awareness |
| **ORBIT** | Yaw circular | 270° arc · 3–6 s/rev | Alignment, synthesis, convergence |
| **ANCHOR** | All axes | &lt; 1° deviation · ≥ 3 s | Stability, resolve, groundedness |
| **SURGE** | Pitch backward | ≥ 120°/s · &lt; 0.5 s | Excitement, enthusiasm, energy |
| **PULSE** | Pitch oscillation | 8–20° · 0.5–1.5 Hz | Agreement, affirmation, active support |
| **PIVOT** | Yaw snap | 80–100° · hold 1.5 s | Reframing, course correction, change of mind |
| **CASCADE** | Pitch deepening | +25° over 3–10 s | Escalation, urgency, building pressure |
| **LEAN** | Roll left | 15° · hold ≥ 1.5 s | Scepticism, weighing options, lateral consideration |
| **BANK** | Roll right | 15° · hold ≥ 1.5 s | Confidence, commitment, decisive lean |
| **VEER** | Yaw left | 40–60° · hold ≥ 1.5 s | Redirection, dissent, counterpoint |
| **SWEEP** | Yaw right | 40–60° · hold ≥ 1.5 s | Clearance, decisive action, moving forward |
