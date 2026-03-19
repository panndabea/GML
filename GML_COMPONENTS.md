# GML Component Proposals

Gyro Motion Language (GML) — structured proposals for eight motion primitives that translate continuous gyroscope data into meaningful shared digital experiences.

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

---

## Component 4: ANCHOR

### 1. Name
**ANCHOR**

### 2. Motion Description
Complete, deliberate stillness — the device held flat and motionless for a sustained period, as if pinning something to a surface.

| Attribute | Detail |
|-----------|--------|
| Direction | None — all axes at rest |
| Intensity | Near-zero movement across all axes (< 1° deviation) |
| Duration | Held for ≥ 3 seconds; brief pauses between gestures do not count |
| Rhythm | Pure stillness; even a single micro-adjustment resets the counter |

### 3. Detection Logic
- Sample all three gyroscope axes continuously at ≥ 50 Hz.
- Declare an Anchor state when total angular displacement across all axes stays below **1°** for **≥ 3 consecutive seconds**.
- Apply a short-window moving average to suppress ambient vibration and walking noise without masking genuine stillness.
- Score anchor quality on a 0–100 scale using the inverse of total angular deviation across the hold window — perfect stillness scores 100.
- Track release: the anchor state ends the moment cumulative displacement exceeds 2° in any axis.

### 4. Semantic Meaning
**Stability. Resolve. Groundedness. Certainty.**
Anchor represents a participant who has stopped processing and arrived at a conclusion — the physical posture of someone who has made up their mind and is holding firm. It is the counterweight to Groundswell: where Groundswell is momentum, Anchor is bedrock.

### 5. Mapping Logic
- Individual Anchor scores contribute to a **collective stability index** visible on the main display.
- The index reflects the proportion of participants currently holding still versus actively gesturing.
- High stability index following a period of debate signals that the room has reached natural resolution.
- Facilitators can use the stability index as a "readiness to decide" signal — when it peaks, the group is set.
- Sustained collective Anchor (>70% of participants, > 5 seconds) triggers a **resolution event**.

### 6. Individual vs Collective Effect

**Single user:**
A small crystalline shape appears on their screen, growing more defined and solid as the hold duration increases. The crystal fractures and dissolves the moment motion is detected.

**1,000 users simultaneously:**
The main display fills with crystals that gradually tessellate into a single unbroken surface. The more participants hold still, the more complete the surface becomes. At full resolution, the display shows a flawless solid plane — a striking visual metaphor for a room that has come to rest on a shared conclusion.

### 7. Experience Use Case
**"The Room Has Decided"** — After an extended debate at an all-hands meeting, the facilitator asks participants to hold still if they feel the discussion has reached a natural conclusion. The stability crystal on the main screen grows in real time as more people anchor. When the crystal completes, the facilitator calls the room — backed by unambiguous data that critical mass is ready to move on.

### 8. Visualization Idea
- Background: a dark textured stone surface.
- Each participant's anchor generates a small glowing crystal fragment at their position in the room map.
- Fragments remain perfectly still while the hold is active; any motion shatters them into particles.
- As collective stillness deepens, fragments migrate and bond, forming an ever-larger crystalline lattice.
- Resolution moment: the lattice clicks into a complete geometric form — a hexagonal tile pattern — and emits a single low resonant chime.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | An instantaneous freeze (device snapped to stillness from active motion) registers as a "hard stop" — high-urgency anchor, signaling interruption rather than conclusion |
| **Intensity** | Stricter stillness threshold (< 0.5°) scores as "deep anchor" — signals maximum certainty rather than settled agreement |
| **Synchronization** | If >80% of participants anchor within the same 2-second window, a "synchronized stillness" event fires — an exceptionally rare and powerful signal of simultaneous resolution |

### 10. Design Insight
Most engagement systems are biased toward action — they measure what people *do*. Anchor is designed around the insight that *stopping* is itself a signal of enormous value. In large-group facilitation, knowing when a room has genuinely resolved versus when participants have simply gone quiet from fatigue or social pressure is nearly impossible without data. Anchor makes the distinction legible: a room that is still because it has decided looks fundamentally different from a room that is drifting. The difficulty of maintaining perfect stillness also filters out passive non-engagement — holding an Anchor takes conscious effort, making it an active signal of resolution.

---

## Component 5: SURGE

### 1. Name
**SURGE**

### 2. Motion Description
A sharp, fast upward snap of the device — the top edge pitching rapidly toward the ceiling and immediately returned to neutral — like a sudden raise of the hand or a burst of energy.

| Attribute | Detail |
|-----------|--------|
| Direction | Backward pitch (top edge up, device snaps rearward) |
| Intensity | High — angular velocity ≥ 120°/s, amplitude ≥ 25° |
| Duration | Brief — the snap completes in < 0.5 seconds |
| Rhythm | Impulsive, not sustained; a single explosive motion |

### 3. Detection Logic
- Monitor the pitch axis for a high-velocity backward snap event.
- Trigger detection when pitch angular velocity exceeds **120°/s** and total arc displacement reaches **≥ 25°** within a **500 ms window**.
- Confirm the gesture ends in a return to neutral (within ±10° of baseline) within 1.5 seconds to distinguish Surge from a drop or fumble.
- Debounce at 2 seconds to prevent multi-counting from device wobble after the snap.
- Compute a *surge score* (0–100) from peak angular velocity × snap amplitude — sharper, faster snaps score higher.

### 4. Semantic Meaning
**Excitement. Enthusiasm. Energy. Spontaneous affirmation.**
Surge is the physical equivalent of a quick hand-raise, a gasp, or a sudden burst of applause — an involuntary or semi-voluntary expression of positive energy in response to a stimulus. It captures the difference between measured approval and visceral excitement.

### 5. Mapping Logic
- Individual Surge events contribute to a **collective energy burst index**.
- Surges from multiple users within a tight time window are clustered into an **excitement spike** event.
- Spikes are timestamped and tied to the content moment on screen — creating an excitement timeline of the event.
- Unlike Groundswell (sustained conviction), Surge data is most valuable in aggregate: the facilitator sees *where* in the content the room erupted, not just *that* it did.
- Repeated Surges from a single user within a session generate an individual "energy profile" useful for breakout assignments.

### 6. Individual vs Collective Effect

**Single user:**
A bright flash of light expands outward from the center of their screen and fades in 0.3 seconds — immediate visual feedback confirming the gesture was read.

**1,000 users simultaneously:**
The main display fires a starburst animation — hundreds of individual flashes overlapping in a single frame. The density of the burst reflects the number of simultaneous Surges. A full-room Surge creates a white-out flash followed by a fade-down through gold to the baseline display — unmistakably electric.

### 7. Experience Use Case
**"Capture the Spark"** — During a product reveal at a company kickoff, the product team unveils a new feature. As the audience reacts, individual Surges are captured in real time and mapped to the reveal timeline. The post-event report shows the facilitator exactly which feature moment generated the most energy — far more precise than applause or a post-survey, and captured without any instructions to participants.

### 8. Visualization Idea
- Background: a dark field with a central pulse point.
- Each Surge fires a radial burst of light from that participant's position in the room map — sharp, fast, and brief.
- At low participation: isolated sparks scattered across the field.
- At high participation: bursts overlap into a supernova — the field saturates to white, then dims as energy dissipates.
- Clusters of Surges in the same content window leave a temporary "hot zone" glow that fades over 10 seconds.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | An extremely fast snap (> 200°/s) classifies as "explosive surge" — exceptional enthusiasm; visualized with a larger starburst radius and a distinct gold color |
| **Intensity** | A deeper snap (≥ 45° arc) registers as a "full surge" — weighted double in the excitement index |
| **Synchronization** | Surges from >60% of participants within a 1-second window trigger a "collective eruption" event — the rarest and highest-amplitude signal in the GML vocabulary |

### 10. Design Insight
Energy in a room is instantaneous and fleeting — it exists in a half-second and vanishes before it can be measured by any conventional tool. Surge is designed to capture that signal at the moment it occurs, creating a temporal map of excitement that reveals which moments in an experience actually land versus which ones a speaker only believes landed. The distinction between *perceived impact* and *measured impact* is often large, and Surge data makes the gap visible in a way that changes how presenters design and iterate on their content.

---

## Component 6: PULSE

### 1. Name
**PULSE**

### 2. Motion Description
A slow, rhythmic rocking of the device forward and back on the pitch axis — a gentle, repetitive nodding motion, like the physical echo of "yes, yes, yes."

| Attribute | Detail |
|-----------|--------|
| Direction | Pitch axis, alternating forward and backward |
| Intensity | Low to moderate — 8–20° amplitude per oscillation |
| Duration | Sustained for ≥ 3 oscillations (≥ 3 seconds) to register |
| Rhythm | Slow and regular — 0.5–1.5 Hz; deliberate, not frantic |

### 3. Detection Logic
- Sample the pitch axis for rhythmic oscillation in the 0.5–1.5 Hz range.
- Apply a band-pass filter to isolate the target frequency range and separate Pulse from TREMOR (higher frequency) and casual device handling.
- Detect when the filtered signal sustains ≥ 3 complete forward-back cycles at amplitude ≥ 8° within a 6-second window.
- Compute a *pulse coherence score* based on regularity of the cycle — even, metronomic oscillation scores higher than erratic rocking.
- Track onset and offset; score includes total number of complete cycles in a session.

### 4. Semantic Meaning
**Agreement. Affirmation. Active listening. Ongoing support.**
Pulse is the device equivalent of nodding — an ambient, continuous signal of engagement and assent rather than a single point-in-time vote. It captures the difference between "I agree" (a moment) and "I am with you throughout this" (a posture). It represents active listening made visible.

### 5. Mapping Logic
- Individual Pulse scores feed a **collective resonance index** displayed as a live background rhythm on the main screen.
- The resonance index reflects how many participants are actively nodding along — a real-time measure of sustained engagement and agreement.
- When resonance is high, the facilitator knows the room is tracking; when it drops, attention or agreement may have broken.
- Pulse data is particularly valuable layered against content: dips in resonance on specific slides or statements identify points of friction or lost attention.
- Extended simultaneous Pulse from >65% of participants generates a **resonance lock** event — collective attunement.

### 6. Individual vs Collective Effect

**Single user:**
A soft oscillating waveform appears at the bottom of their screen, pulsing in sync with their nodding rhythm — a quiet, affirming reflection of their engagement.

**1,000 users simultaneously:**
The main display shows a shared waveform that sums all individual pulses. When participants pulse in rhythm, the shared waveform amplifies into a clean, large-amplitude sine wave — a visual manifestation of collective resonance. Participants who notice their rhythm syncing with the display are drawn into deeper engagement.

### 7. Experience Use Case
**"The Room Is With You"** — During a long keynote, the speaker can glance at the resonance index in real time to gauge whether the audience is actively following along or drifting. A live coaching prompt for the speaker shows when resonance dips below threshold, triggering a cue to re-engage. Post-event, the resonance timeline reveals which sections of the talk held the audience versus which lost them — a data layer unavailable to any public speaker today.

### 8. Visualization Idea
- Background: a calm horizontal water surface viewed from the side.
- Each participant's pulse generates a small wave originating at their position.
- At low participation: individual waves, isolated, crossing without amplification.
- At high collective pulse: waves align in phase and constructively interfere — the surface transforms into a powerful, synchronised swell with a dominant frequency matching the average pulse rate of the room.
- Resonance lock: the surface locks to a single clean waveform; color shifts from neutral blue to warm amber.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | Faster pulsing (> 2 Hz) tips into affirmation urgency — registering as emphatic agreement or impatience; visualized as a compressed, choppy waveform |
| **Intensity** | Larger amplitude oscillations (> 25°) score as "strong pulse" — active, emphatic nodding rather than ambient agreement |
| **Synchronization** | When >75% of participants pulse within 0.2 seconds of the same phase, a "phase sync" event fires — the display briefly renders a single perfect sine wave across the full screen, visible to all |

### 10. Design Insight
Sustained agreement is invisible in every existing group engagement tool. A vote captures agreement at one moment; Pulse captures the *duration and depth* of agreement across a continuous passage of content. The design insight is that facilitators and speakers need to know not just *if* the room agreed but *how long* and *through which parts* of the content — and that a body gesture requiring no conscious thought is the right instrument for capturing that signal. Pulse also introduces a social synchrony dynamic: when participants notice their waveforms merging on the main display, they experience the room as a unified entity rather than isolated individuals — a powerful group cohesion effect.

---

## Component 7: PIVOT

### 1. Name
**PIVOT**

### 2. Motion Description
A sharp, deliberate 90° rotation of the device around its yaw axis — held flat, snapped a quarter-turn clockwise or counter-clockwise and held in the new orientation — the physical gesture of turning a corner.

| Attribute | Detail |
|-----------|--------|
| Direction | Yaw axis, 90° clockwise or counter-clockwise |
| Intensity | Moderate to high — rotation completes in 0.3–1.0 seconds |
| Duration | New orientation held for ≥ 1.5 seconds after rotation completes |
| Rhythm | Decisive snap-and-hold; not a slow drift or a full spin |

### 3. Detection Logic
- Monitor the yaw axis for a rapid angular displacement event.
- Detect Pivot when yaw displacement reaches **80–100°** (within ±10° tolerance) in a **≤ 1 second** window.
- Confirm the hold: yaw velocity must fall below **10°/s** for **≥ 1.5 seconds** after the snap, confirming the new orientation is intentional.
- Track rotation direction: clockwise Pivot vs. counter-clockwise Pivot carry distinct semantic weight.
- Reject false positives from partial turns (< 70°) and full spins (> 120° in the detection window).

### 4. Semantic Meaning
**Reframing. Course correction. Change of mind. New perspective.**
Clockwise Pivot: *decisive shift* — I am changing my position and committing to a new direction.
Counter-clockwise Pivot: *stepping back to reconsider* — I am withdrawing from a previous position to re-examine.
Pivot is the motion of someone who has genuinely updated their thinking rather than simply gone quiet. It signals cognitive flexibility and willingness to shift, not just passive drift.

### 5. Mapping Logic
- Pivot events contribute to a **collective reframe index** — the proportion of participants who have Pivoted within a given content window.
- Clockwise Pivots increment a **shift score**; counter-clockwise Pivots increment a **reconsider score**.
- The ratio of shift to reconsider tells the facilitator whether the room is committing to a new direction or retreating to earlier ground.
- A Pivot immediately following a period of high Groundswell is a particularly powerful signal: the room was leaning hard in one direction and then visibly changed course.
- When >50% of participants Pivot in the same direction within a 5-second window, a **collective reframe** event fires.

### 6. Individual vs Collective Effect

**Single user:**
Their device screen shows an arrow that snaps to the new orientation and locks — a crisp, satisfying visual confirmation of the direction change. The arrow fades after 5 seconds.

**1,000 users simultaneously:**
The main display shows a field of arrows, each representing a participant. As Pivots occur, arrows snap to new orientations in real time. When a collective reframe event fires, all arrows animate in unison to the new direction — a visually arresting demonstration of a room turning the corner together.

### 7. Experience Use Case
**"The Room Has Shifted"** — During a strategic planning session, a proposal has been met with sustained Groundswell. A new piece of information is introduced. The facilitator watches in real time as Pivot events accumulate — arrows across the display snapping to new orientations — and can call the moment the room has genuinely reframed rather than simply gone quiet. The Pivot timeline becomes an audit trail of when and why the group changed direction.

### 8. Visualization Idea
- Background: a compass rose on a dark field.
- Each participant's resting orientation is represented by a small directional marker at their position.
- A Pivot snaps the marker to the new bearing with a sharp click animation.
- At low participation: isolated snaps, independent reorientations.
- At collective reframe: all markers rotate in the same direction simultaneously, the compass rose at the center rotates to match, and a clean directional beam projects from the center in the new bearing.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | A very fast snap (< 0.2 seconds) registers as "hard pivot" — signals abrupt, emphatic change rather than considered reframing |
| **Intensity** | A 180° rotation (half-turn) classifies as "full reversal" — the strongest possible reframe signal; rare and treated as a distinct event type |
| **Synchronization** | Synchronized Pivots from >60% of participants within 2 seconds fire a "collective turn" event — one of the most narratively powerful signals in the GML vocabulary |

### 10. Design Insight
Facilitation tools are good at capturing opinions but terrible at capturing *opinion change*. Most post-event surveys measure final position, not the journey — and most live tools have no mechanism at all for detecting when minds shift. Pivot is built around the insight that the *moment of reframing* is often the most valuable data point in a meeting: it tells you what information or argument actually changed the room, not just what the room believed at the end. This temporal precision — knowing not just *that* the room shifted but *exactly when* — creates a new category of facilitation intelligence.

---

## Component 8: CASCADE

### 1. Name
**CASCADE**

### 2. Motion Description
A slow, progressive deepening of the forward pitch tilt — the device beginning at a shallow angle and tilting ever further forward in a smooth continuous arc, as if pouring something out in increasing volume.

| Attribute | Detail |
|-----------|--------|
| Direction | Forward pitch, monotonically increasing angle |
| Intensity | Starts low (≥ 5°) and deepens continuously; must reach ≥ 30° at peak |
| Duration | The deepening phase spans 3–10 seconds; sustained acceleration required |
| Rhythm | Smooth and unidirectional — pauses or backward corrections break the cascade |

### 3. Detection Logic
- Monitor the pitch axis for a sustained, monotonically increasing forward tilt.
- Confirm Cascade when forward pitch increases by at least **25°** over a **3–10 second window** without any backward correction > 3°.
- Compute a *cascade rate* (degrees per second) — the rate of increase captures the urgency of the escalation.
- Distinguish from Groundswell (which is a held steady angle) by requiring continuous angular increase rather than a static hold.
- Score Cascades by total arc depth and smoothness of the ramp — deeper, smoother ramps score higher.
- Track the peak angle; Cascades that reach ≥ 45° are classified as "critical cascade."

### 4. Semantic Meaning
**Escalation. Building urgency. Mounting pressure. Unstoppable momentum.**
Cascade is not a steady lean (Groundswell) — it is a lean that keeps growing. It represents a participant who started with moderate feeling and found that feeling deepening as the content continued — the physical manifestation of "this keeps getting bigger." It captures escalating commitment rather than sustained commitment.

### 5. Mapping Logic
- Individual Cascade scores feed an **escalation index** tracked against the content timeline.
- The rate of change of the index is as important as its level: a rapidly steepening cascade means the room's feeling is accelerating, not just present.
- Facilitators receive a warning signal when the escalation index rises faster than a configurable rate threshold — useful for surfacing topics that are getting out of hand before they reach crisis.
- Cascade data layered with Tremor data creates a powerful composite picture: a room that is both escalating and tremoring is in a high-stakes, high-urgency state that demands immediate facilitation attention.
- When >55% of participants enter critical cascade simultaneously, a **collective escalation** event fires.

### 6. Individual vs Collective Effect

**Single user:**
A rising tide graphic appears on their screen — a bar that fills upward continuously as long as their tilt is deepening. The fill rate matches their cascade rate; a deep, fast cascade fills the bar dramatically.

**1,000 users simultaneously:**
The main display shows a rising-water animation: the collective cascade level fills the screen from the bottom upward. The speed of the rise reflects the average cascade rate across all active participants. At collective escalation, the water reaches the top of the screen and overflows into a cascade animation — a visually arresting representation of a room that has reached a tipping point.

### 7. Experience Use Case
**"Measure the Boiling Point"** — During a town hall where a controversial policy change is being introduced slide by slide, Cascade data shows in real time whether audience feeling is intensifying as more details are revealed. A facilitator watching the escalation index can intervene — add context, open a Q&A, or change the framing — before collective feeling tips past the critical threshold rather than discovering the temperature only in a post-event survey.

### 8. Visualization Idea
- Background: a cross-section of a vessel being filled from above.
- Each participant's cascade rate is rendered as a stream pouring into the vessel from their position.
- At low cascade participation: thin trickles, vessel mostly empty.
- At high cascade participation: thick streams converge, vessel fills rapidly.
- Critical cascade moment: vessel overflows and the excess streams off the sides of the screen in a dynamic cascade animation — the origin of the name.
- Color shifts from cool blue (early, mild) to deep orange (critical) as the vessel fills.

### 9. Variations

| Variable | Effect |
|----------|--------|
| **Speed** | A very rapid deepening (> 8°/s) classifies as "flash cascade" — urgency is extreme; the vessel fills at an alarming rate and the facilitator receives an immediate alert |
| **Intensity** | Reaching ≥ 60° of forward pitch marks a "maximum cascade" — the participant's device is nearly face-down; an exceptional signal of extreme urgency |
| **Synchronization** | When >70% of participants are in active cascade simultaneously and their rates are converging, a "cascade lock" event fires — the collective escalation has achieved a self-reinforcing character and is highly unlikely to reverse without direct intervention |

### 10. Design Insight
There is a meaningful difference between a room that feels strongly and a room that is feeling more strongly with every passing moment. Existing tools capture the first; Cascade is designed to capture the second. The rate of change of collective feeling is often more actionable than its absolute level: a room at moderate intensity with a steep upward slope is more urgent than a room at high intensity that has stabilized. Cascade gives facilitators a first derivative of group emotional state — a signal that is invisible to every conventional engagement tool but that experienced facilitators learn to feel intuitively in the room. GML makes that intuition measurable.
