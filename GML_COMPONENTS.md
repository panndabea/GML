# GML Component Proposals

Gyro Motion Language (GML) — structured proposals for three new motion primitives that translate continuous gyroscope data into meaningful shared digital experiences.

---

## Component 1: GROUNDSWELL

### 1. Name
**GROUNDSWELL**

### 2. Motion Description
A slow, sustained forward tilt of the device — as if leaning into something with conviction.

| Attribute | Detail |
|-----------|--------|
| Direction | Forward pitch (device tilts away from user, top edge down) |
| Intensity | Moderate to high — past a 15° threshold |
| Duration | Held for 2–8 seconds; brief dips do not count |
| Rhythm | Continuous hold, not pulsed; a deliberate lean |

### 3. Detection Logic
- Monitor the pitch axis of the gyroscope continuously.
- Detect when the forward pitch angle exceeds **15°** and is held for **≥ 1.5 seconds**.
- Weight the signal by *hold duration*: longer holds produce a stronger contribution score.
- Discard noise below a 5° dead-zone to prevent false triggers from casual device handling.
- Track release: once the device returns to neutral, the contribution decays over 3 seconds (so momentum is not lost instantly).

### 4. Semantic Meaning
**Momentum. Commitment. Forward pressure.**
A Groundswell represents a user leaning *into* a direction, idea, or proposal — the physical embodiment of "I'm with this." It signals conviction rather than passive agreement.

### 5. Mapping Logic
- Each user's hold angle and duration contribute a **momentum score** (0–100).
- The score drives a shared "pressure bar" on the main screen — the collective lean of the room.
- The longer and deeper the lean, the higher the pressure.
- A sudden release from many users simultaneously registers as a "break" — a notable signal that consensus collapsed.

### 6. Individual vs Collective Effect

**Single user:**
A small glowing particle floats forward on their device screen, tracking with their lean angle. The particle fades when they release.

**1,000 users simultaneously:**
The shared display fills with a wave of particles all surging forward, forming a visible tide. A rumble animation shakes the display border when critical mass (>60% of users) sustains the lean for >3 seconds — the "groundswell moment." The room visually and audibly tips, making collective momentum undeniable.

### 7. Experience Use Case
**"Back This Strategy"** — During a company townhall, the CEO presents three strategic options. Attendees lean their devices forward to push momentum behind their preferred option. Each option has its own pressure bar. The crowd watches, in real time, which option is generating the deepest and most sustained collective lean — not just quick votes, but held conviction.

### 8. Visualization Idea
- Background: a dark ocean surface viewed from above.
- Each user's lean generates a ripple that propagates outward.
- At low participation: scattered ripples, calm sea.
- At high collective lean: the ripples merge into a single dominant wave that sweeps across the screen from one edge to the other.
- Intensity of the wave (height, color saturation) reflects average lean depth.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | A fast snap-forward (jerk) registers as a sharp "push" — high urgency, brief duration, used for sudden emphasis rather than sustained momentum |
| **Intensity** | A 30°+ deep lean counts double; signals extreme conviction vs. mild agreement |
| **Synchronization** | If 70%+ of users reach the threshold within a 2-second window, a "synchronized surge" event fires — a rare, high-drama moment rendered as a shockwave on the main display |

### 10. Design Insight
Voting is binary. Groundswell is *analog*. It captures the difference between clicking "agree" and actually leaning in — a physical metaphor that audiences recognize immediately without instruction. In large rooms, watching the wave form in real time creates social proof dynamics that amplify genuine conviction and expose weak consensus that "show of hands" voting would mask.

---

## Component 2: TREMOR

### 1. Name
**TREMOR**

### 2. Motion Description
Rapid, low-amplitude side-to-side shaking of the device — the physical expression of tension, uncertainty, or high-stakes nervousness.

| Attribute | Detail |
|-----------|--------|
| Direction | Lateral (roll axis), oscillating left-right |
| Intensity | Low amplitude (5–20° per oscillation) but high frequency (3–7 Hz) |
| Duration | Typically 2–10 seconds; sustained tremoring is meaningful |
| Rhythm | Irregular, organic micro-oscillations — not metronomic |

### 3. Detection Logic
- Sample the roll axis at high frequency (≥ 50 Hz).
- Apply a band-pass filter isolating oscillations in the **3–7 Hz range** to separate tremor from intentional shaking or walking noise.
- Detect tremor when the filtered signal exceeds a **5° amplitude** for **≥ 1 second**.
- Compute a *tremor intensity score* (0–100) from average amplitude × frequency within the detection window.
- Distinguish from a single shake event (which is faster, higher-amplitude, and briefer) by requiring multiple reversals within the window.

### 4. Semantic Meaning
**Tension. Stakes. Anxiety. Risk awareness.**
Tremor captures the physical manifestation of being on edge — the body's way of signaling that something matters, that outcomes are uncertain, or that a decision feels heavy. It is not negative; high collective tremor signals that the room recognizes real stakes.

### 5. Mapping Logic
- Individual tremor intensity feeds into a **collective tension index** displayed as a ambient "pressure" layer on the main screen.
- The index rises as more users tremor and falls as they still.
- When tension crosses a threshold, the facilitator receives a signal that the room needs acknowledgment — a data-driven cue to pause, address concerns, or reframe.
- Optionally: tension scores can be tied to specific content moments (e.g., when a financial risk slide appears), creating a timeline of where the room felt most exposed.

### 6. Individual vs Collective Effect

**Single user:**
Their device screen shows a subtle background pulse — like a heartbeat — that mirrors their tremor frequency. A soft amber glow confirms the system is reading their tension.

**1,000 users simultaneously:**
The main display shows a "tension field" — a heat-map overlay where dense clusters of tremoring users light up as hot zones. If the entire room tremors in the same window, the display shifts to a deep amber/red and a low-frequency audio tone builds underneath the event audio — unmistakable and visceral.

### 7. Experience Use Case
**"Risk Barometer"** — An executive team presents a high-stakes restructuring plan to 800 employees. As each phase is revealed, the live display shows the collective tension index in real time. A sudden spike when "role eliminations" is mentioned gives leadership unambiguous, unfiltered emotional data from the room — data they could never get from a post-event survey. The tension index becomes a live accountability mechanism.

### 8. Visualization Idea
- Background: a calm dark field with subtle grid lines.
- Individual tremor generates a localized "interference pattern" — concentric rings radiating from each device's position in the room map.
- At low tension: sparse rings, isolated, fade quickly.
- At high collective tension: rings overlap and constructively interfere, creating Moiré patterns that pulse across the entire display — visually representing the resonance of shared anxiety.
- Color gradient: calm blue → tense amber → critical red.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | Higher frequency (>7 Hz) tips into "alarm" territory — a different semantic layer suggesting panic rather than tension |
| **Intensity** | Higher amplitude oscillation elevates the tremor from background anxiety to active distress; triggers a facilitator notification |
| **Synchronization** | Synchronized tremor from >50% of attendees within the same 3-second window fires a "collective dread" event — a rare signal that should never be ignored in the debrief |

### 10. Design Insight
Most audience engagement tools ask people to rate their feelings after the fact, when memory is already distorted. Tremor captures affective state *in the moment* without requiring conscious action — the participant doesn't press "I feel anxious," they simply feel anxious and the system reads it. This is interaction design that works with the body instead of competing with the mind. The ethical dimension (passive capture of emotional signals) is also the design challenge: the experience must make consent and transparency central.

---

## Component 3: ORBIT

### 1. Name
**ORBIT**

### 2. Motion Description
A slow, deliberate circular rotation of the device — held flat, rotated clockwise or counter-clockwise as if stirring something — representing active alignment, synthesis, and convergence.

| Attribute | Detail |
|-----------|--------|
| Direction | Yaw axis rotation (device held flat, rotating around its vertical axis) |
| Intensity | Moderate — one full revolution takes 3–6 seconds |
| Duration | Sustained circular motion for ≥ 3 seconds to register |
| Rhythm | Smooth and continuous, not jerky; irregular stops break the orbit |

### 3. Detection Logic
- Monitor the yaw axis for sustained angular velocity in a consistent rotational direction.
- Confirm a circular pattern by checking that the yaw rate stays within **±20% of a target angular velocity** for at least **270° of arc** (three-quarters of a revolution).
- Differentiate clockwise from counter-clockwise rotation (separate semantic meanings).
- Penalize drift: if the device's axis tilts more than 30° from horizontal during the gesture, it does not count (user must be intentionally holding the device flat).
- Score orbits by completeness (partial vs. full revolution) and smoothness (standard deviation of angular velocity).

### 4. Semantic Meaning
**Alignment. Synthesis. Integration. Building consensus.**
Clockwise orbit: *gathering in* — I am synthesizing, integrating, pulling threads together.
Counter-clockwise orbit: *expanding out* — I am generating, exploring, opening up possibilities.
Orbit is the motion of a conductor, a stirrer, a connector — someone actively working to unify rather than push in a single direction.

### 5. Mapping Logic
- Each user's orbit contributes to a **coherence field** — a measure of how aligned the group's processing is.
- Clockwise orbits increase the coherence score; counter-clockwise orbits increase an **exploration score**.
- The ratio of coherence to exploration tells the facilitator whether the group is ready to converge (high coherence) or still needs divergent thinking time (high exploration).
- If >80% of orbiting users are rotating in the same direction simultaneously, a **phase lock** event fires — a powerful collective signal of unified intent.

### 6. Individual vs Collective Effect

**Single user:**
A luminous ring appears on their screen, spinning in the direction of their orbit. The ring's brightness and thickness grow with smoothness and completion of each revolution.

**1,000 users simultaneously:**
The main display shows hundreds of orbiting rings, each representing a user. When orbits begin aligning in the same direction, the rings migrate toward the center of the display and begin forming a single large composite ring — a visual representation of emerging consensus. When phase lock is reached, the rings merge into one brilliant circle with a resonant audio tone — an unmistakable shared moment of alignment.

### 7. Experience Use Case
**"Build the Synthesis"** — After a 45-minute breakout session where teams have generated divergent ideas, the facilitator asks everyone to "orbit" — rotate their device — when they feel ready to start synthesizing. The screen shows the ratio of clockwise (converge) to counter-clockwise (still exploring) orbits in real time. The facilitator can see exactly when the room has shifted from generative to integrative mode, and times their intervention accordingly instead of guessing.

### 8. Visualization Idea
- Background: deep space with a central attractor point.
- Each user's orbit creates a particle that traces a circular path around the attractor.
- Clockwise orbits: warm gold particles. Counter-clockwise: cool cyan particles.
- As more users orbit and their directions converge, the particle trails become brighter and tighter — eventually forming a coherent ring around the attractor.
- Phase lock moment: the ring becomes solid, pulses once, and the attractor at the center flares — a visual "big bang" of shared alignment.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | Fast orbits (< 2s per revolution) register as "agitation" — the gesture's meaning shifts from synthesis to urgency/impatience; visualized as unstable ellipses instead of clean circles |
| **Intensity** | A wobbly, imprecise orbit scores lower on coherence; a smooth, even orbit scores higher — quality of motion maps to quality of engagement |
| **Synchronization** | Exact synchronization (same angular position at the same time) across users creates a "resonance wave" — rings pulse together — a highly rare and valuable group signal |

### 10. Design Insight
Most group tools measure agreement (thumbs up/down) but not *readiness to converge* — which is a completely different and more valuable signal in facilitation. Orbit is designed around the insight that synthesis is a *process*, not a moment, and that groups often fail not because they lack good ideas but because someone pushes for closure before the room is ready. Orbit makes collective readiness legible, giving facilitators a live instrument instead of intuition. The circular motion is also universally legible — it takes less than 3 seconds to demonstrate, with zero verbal instruction needed.
