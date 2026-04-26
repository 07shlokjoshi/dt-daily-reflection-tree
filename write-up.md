# Design Write-Up: Daily Reflection Tree

*DeepThought Fellowship Assignment — Part A*

---

## Why These Questions

The central design constraint was this: **a tired person at 7pm will not tolerate a survey**. Every question had to feel like it was *for* them, not *about* them. That meant each question needed to open something rather than test something.

### Axis 1 — Locus of Control

The opening question ("How was your day?") serves a dual purpose: it warms the session and routes the subsequent path. A "Productive" day and a "Frustrating" day are psychologically different starting points — not just emotionally, but in the kind of introspection that's useful. Someone on a good day can be asked "what made it happen?" and honestly attribute it outward or inward. Someone on a bad day needs a softer entry: "what was your first instinct?" before reaching the harder "did you have a choice?"

The two follow-up questions (A1_Q2 and A1_Q2B) were designed to surface *behavioral evidence*, not self-report. Asking "did you feel in control?" invites a curated answer. Asking "how did you handle a specific decision?" forces a concrete recall. Rotter's original locus scale worked through situational attribution; I tried to preserve that specificity.

### Axis 2 — Orientation (Contribution vs. Entitlement)

This axis was the hardest to design without moralizing. Entitlement is invisible to the person holding it — Campbell et al.'s research shows it's a stable trait precisely because it feels *warranted* to the entitlement-holder. So the questions can't name the behavior. They have to describe it neutrally enough that a genuinely entitled person will recognize themselves without shame.

The three questions approach this from different angles: what stood out (behavioral), what drove you underneath (motivational), and whether you acted without being asked (behavioral again, but discretionary). The third question — "did you do something helpful without being asked?" — is the crux. Organ's OCB research identifies *discretionary* effort as the marker of contribution orientation. If the answer is "yes, and I hoped someone would notice," that's entitlement wearing the costume of contribution.

### Axis 3 — Radius of Concern

Maslow's self-transcendence is often reduced to altruism, but the deeper insight is *contextual widening* — the shift from "what do I need?" to "what does this situation need from me?" The questions here don't ask "are you a good person?" They ask "when you picture the challenge, who's in the frame?"

The final question in this axis — "did you check in on someone today, not for a task, but as a person?" — was the one I disagreed most with the AI about. Claude initially suggested something more positive: "did you support a teammate?" I pushed back because *support* is task-contaminated. The question I landed on isolates purely human concern: not a deliverable, not a project, just a person. It's a harder question. That's why it's the last one.

---

## Branching Logic — Trade-offs

### Signal accumulation vs. single-answer routing

I chose **signal accumulation** over routing on a single answer. This means the dominant axis outcome is determined by the balance of 2–3 signals, not a binary single-answer branch. This is more robust: a person who gives a mixed signal on question 1 can still be routed correctly by their answer to question 2.

The trade-off is that pure single-answer routing is simpler to trace. With accumulation, you need to follow the signals across multiple nodes to understand why the decision node chose a path. I addressed this with the `comment` field on decision nodes in the JSON — a plain-English explanation of what each decision is measuring.

### Two high-path questions, two low-path questions (Axis 1)

Axis 1 has two distinct question sequences (HIGH and LOW) depending on the opening answer. This doubles the question count for Axis 1 but produces a more honest conversation. A frustrated person being asked "what made things go well?" would feel invalidated. A productive person being asked "what was your first instinct when things got hard?" feels irrelevant. The branching costs two nodes but earns a more trustworthy session.

### Why no branching in Axes 2 and 3

Axes 2 and 3 are linear (all users answer the same questions). This was a deliberate simplification. By the time the employee reaches Axis 2, the opening routing has done its job — the session has a tone. The questions in Axes 2 and 3 are calibrated to work for any person regardless of their Axis 1 result. Adding branching here would have increased complexity without improving insight.

---

## Psychological Sources

- **Rotter (1954)**: Internal vs. external locus. Questions designed to surface *behavioral attribution*, not self-assessed trait.
- **Dweck (2006)**: Growth vs. fixed mindset. Influenced the framing of "adjusted my approach" as an internal signal — agency isn't about succeeding, it's about adapting.
- **Campbell et al. (2004)**: Entitlement's invisibility to its holder. Informed the non-confrontational framing of the Axis 2 questions.
- **Organ (1988)**: OCB as *discretionary* effort. The "without being asked" question is drawn directly from this definition.
- **Maslow (1969)**: Self-transcendence as widening radius of concern, not just altruism. Influenced the "who comes to mind" framing — perspective is spatial before it is moral.
- **Batson (2011)**: Perspective-taking as cognitive, not emotional. This is why the Axis 3 questions ask *who you thought about*, not *how you felt about them*.

---

## What I'd Improve With More Time

1. **A mixed-signal reflection node.** When axis signals are tied (e.g., axis1:internal = 1, axis1:external = 1), the current tree defaults to the first matching route. A "mixed signal" reflection node would be more honest — acknowledging ambiguity rather than forcing a binary reading.

2. **Cross-axis interpolation in summaries.** The most interesting psychological insight lives at the *intersection* of axes. An internal-locus, entitlement-oriented person is a very different character from an external-locus, contribution-oriented one. The current summary treats axes independently. A more sophisticated tree would have composite summary templates.

3. **Longitudinal pattern nodes.** The tree currently has no memory of prior sessions. A stateful version could introduce a "pattern node" — a reflection type that surfaces when a user has shown the same dominant signal for three sessions in a row. That's where the real coaching value lives.

4. **An optional free-text capture** — not for routing (the product must stay deterministic), but as a journaling prompt at the very end. "One thing from today in your own words." No classification. Just a place to land.
