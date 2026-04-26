# Persona 2: Victim — External / Entitlement / Self-Centric
**Path type:** Low agency, inward-looking, entitlement-oriented

---

## Session Transcript

**[START]**
> Good evening. Take a breath — today is almost done.
> Let's spend a few minutes with it. Not to judge it. Just to see it clearly.

*(User clicks: Begin →)*

---

### AXIS 1 — Locus of Agency

**[A1_OPEN]** How would you describe your day overall?

→ **Frustrating**

*(Decision node A1_D1 routes to A1_Q1_LOW)*

---

**[A1_Q1_LOW]** When things got difficult today, what was your first instinct?

→ **Feel overwhelmed and stuck**
*(Signal recorded: axis1:external)*

---

**[A1_Q2B]** Looking back at the hardest moment today — were there choices you had?

→ **Not really — circumstances decided it**
*(Signal recorded: axis1:external)*

*(Decision node A1_D2: axis1 signals = internal:0, external:2 → routes to A1_REFLECT_EXT)*

---

**[A1_REFLECT_EXT]**
> *Some days pull your attention outward — to what others did or didn't do, to circumstances beyond your reach. That's real, and it's human.*
>
> *But somewhere today, even quietly, you made a call. The fact that you're here reflecting on it? That's already a sign of agency.*

*(User clicks: Continue →)*

---

**[BRIDGE_1_2]**
> Now let's shift from how you handled things — to what you gave today.

*(Auto-advances after 2.2s)*

---

### AXIS 2 — Orientation

**[A2_OPEN]** Think about your interactions today. What stands out most?

→ **I expected recognition I didn't get**
*(Signal recorded: axis2:entitlement)*

---

**[A2_Q2]** In your most important interaction today, what was driving you underneath?

→ **I wanted others to notice my effort**
*(Signal recorded: axis2:entitlement)*

---

**[A2_Q3]** Was there a moment today when you did something helpful without being asked?

→ **Not really — I stayed in my lane**
*(Signal recorded: axis2:entitlement)*

*(Decision node A2_D1: axis2 signals = contribution:0, entitlement:3 → routes to A2_REFLECT_ENTITLE)*

---

**[A2_REFLECT_ENTITLE]**
> *There's nothing wrong with wanting recognition — effort deserves acknowledgment.*
>
> *But when the expectation of reward shapes the action, the action gets smaller. Worth sitting with: what would you have done today if no one were watching and no credit were coming?*

*(User clicks: Continue →)*

---

**[BRIDGE_2_3]**
> We've looked at how you acted, and what you gave. Now let's zoom out — beyond yourself.

*(Auto-advances after 2.2s)*

---

### AXIS 3 — Radius of Concern

**[A3_OPEN]** When you think about today's biggest challenge — who comes to mind?

→ **Mostly just me and my work**
*(Signal recorded: axis3:self)*

---

**[A3_Q2]** How did your work today land for people beyond yourself?

→ **It mostly affected my own deliverables**
*(Signal recorded: axis3:self)*

---

**[A3_Q3]** Did you check in on someone today — not for a task, but just as a person?

→ **No — I was too focused on my own work**
*(Signal recorded: axis3:self)*

*(Decision node A3_D1: axis3 signals = self:3, team:0, others:0 → routes to A3_REFLECT_SELF)*

---

**[A3_REFLECT_SELF]**
> *Today your focus was tight — on your own work, your own outcomes. That's not a flaw; focus matters.*
>
> *But the most durable source of meaning at work isn't personal achievement. It's realizing your work matters to someone else. Tomorrow: look for one person your work touches.*

*(User clicks: Continue →)*

---

### SUMMARY

**Axis 1 · Agency & Locus**
Circumstances felt bigger than your choices today — worth noticing where you did have agency.
*Leaning: external*

**Axis 2 · Orientation**
The internal scorecard was running today — what you gave versus what you felt you deserved.
*Leaning: entitlement*

**Axis 3 · Radius of Concern**
Your frame was personal and close — useful for focus, but narrow for meaning.
*Leaning: self*

> *These aren't scores. They're mirrors. What you see in them is yours to work with.*

---

**[END]**
> That's it for today.
> You showed up, you reflected — and that's already more than most. See you tomorrow.

---

## Path Summary

| Node | Type | Answer |
|------|------|--------|
| A1_OPEN | question | Frustrating |
| A1_D1 | decision | → A1_Q1_LOW |
| A1_Q1_LOW | question | Feel overwhelmed and stuck |
| A1_Q2B | question | Not really — circumstances decided it |
| A1_D2 | decision | → A1_REFLECT_EXT |
| A1_REFLECT_EXT | reflection | — |
| BRIDGE_1_2 | bridge | — |
| A2_OPEN | question | I expected recognition I didn't get |
| A2_Q2 | question | I wanted others to notice my effort |
| A2_Q3 | question | Not really — I stayed in my lane |
| A2_D1 | decision | → A2_REFLECT_ENTITLE |
| A2_REFLECT_ENTITLE | reflection | — |
| BRIDGE_2_3 | bridge | — |
| A3_OPEN | question | Mostly just me and my work |
| A3_Q2 | question | It mostly affected my own deliverables |
| A3_Q3 | question | No — I was too focused on my own work |
| A3_D1 | decision | → A3_REFLECT_SELF |
| A3_REFLECT_SELF | reflection | — |
| SUMMARY | summary | — |
| END | end | — |

**Final state signals:**
- axis1: internal=0, external=2
- axis2: contribution=0, entitlement=3
- axis3: self=3, team=0, others=0

---

## What Changed Compared to Persona 1

Note how the same 9 questions produce a structurally different conversation:

1. **A1_D1** routed to the LOW path (A1_Q1_LOW + A1_Q2B) instead of the HIGH path (A1_Q1_HIGH + A1_Q2) — Persona 2 never saw the "things went well" question
2. **A1_REFLECT_EXT** was shown instead of A1_REFLECT_INT — the reflection acknowledged difficulty without judgment
3. **A2_REFLECT_ENTITLE** surfaced a question ("what would you have done if no one were watching?") that Persona 1 never received
4. **A3_REFLECT_SELF** offered a forward-looking nudge ("tomorrow: look for one person your work touches") that Persona 1 didn't need
5. The summary on every axis was different — different templates, different language, different invitation

The tree produced genuinely different conversations from the same structure. No LLM was consulted at runtime. Every branch was a lookup.
