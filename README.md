# Daily Reflection Tree
**DeepThought Fellowship Assignment — Part A + B**

A deterministic end-of-day reflection tool. No LLM at runtime. Every path is a lookup.

---

## Repository Structure

```
/tree/
  reflection-tree.json     ← Part A: the full tree (25 nodes)
/agent/
  index.html               ← Part B: single-file web agent
/transcripts/
  persona-1-victor.md      ← Victor path: internal / contribution / others
  persona-2-victim.md      ← Victim path: external / entitlement / self
write-up.md                ← Design rationale (2 pages)
README.md                  ← This file
```

---

## Part A: Reading the Tree

`/tree/reflection-tree.json` is a self-contained JSON file. To trace any conversation path:

1. Start at node `"id": "START"`
2. Follow the `"next"` field to move between nodes
3. At `"type": "decision"` nodes, evaluate `"routes"` top-to-bottom — the first matching condition wins
4. At `"type": "question"` nodes, the selected option's `"signal"` is accumulated in state
5. At `"type": "summary"`, use `summaryTemplates` with the dominant pole per axis

**Condition syntax:**

| Pattern | Meaning |
|---------|---------|
| `answer(NODE_ID)=Val1\|Val2` | Previous answer at NODE_ID equals Val1 or Val2 |
| `dominant(axis1)=internal` | axis1 internal signal count > external |
| `dominant(axis3)=team\|others` | axis3 dominant is either team or others |

**Signal accumulation:**

Every question option has an optional `"signal"` field. When selected, it increments the corresponding counter:

```
axis1:internal   → state.axis1.internal++
axis2:entitlement → state.axis2.entitlement++
```

At decision nodes using `dominant()`, the pole with the higher count wins.

**Text interpolation:**

Curly-brace placeholders are replaced at render time:

```
{A1_OPEN}        → user's answer at node A1_OPEN
{A1_Q2}          → user's answer at node A1_Q2
{axis1.summary}  → summaryTemplates.axis1[dominant('axis1')]
```

---

## Part B: Running the Agent

The agent is a single HTML file. It tries to fetch the tree from `../tree/reflection-tree.json`. If that fails (e.g. opened directly from the filesystem), it falls back to an embedded copy.

**Option 1 — Python (no install needed):**
```bash
cd reflection-project
python3 -m http.server 8080
# open http://localhost:8080/agent/index.html
```

**Option 2 — Node.js:**
```bash
npx serve reflection-project
# open the URL shown in terminal, then navigate to /agent/
```

**Option 3 — Open directly:**
Just open `agent/index.html` in a browser. The inline fallback activates automatically.

---

## Node Count

| Type | Count | IDs |
|------|-------|-----|
| start | 1 | START |
| question | 9 | A1_OPEN, A1_Q1_HIGH, A1_Q1_LOW, A1_Q2, A1_Q2B, A2_OPEN, A2_Q2, A2_Q3, A3_OPEN, A3_Q2, A3_Q3 |
| decision | 4 | A1_D1, A1_D2, A2_D1, A3_D1 |
| reflection | 6 | A1_REFLECT_INT, A1_REFLECT_EXT, A2_REFLECT_CONTRIB, A2_REFLECT_ENTITLE, A3_REFLECT_SELF, A3_REFLECT_OTHER |
| bridge | 2 | BRIDGE_1_2, BRIDGE_2_3 |
| summary | 1 | SUMMARY |
| end | 1 | END |
| **Total** | **25** | |

*(Note: question count shows 11 unique question nodes; 9 are reachable per session since A1 branches HIGH or LOW)*

---

## Possible Conversation Paths

| A1_OPEN | A1 route | A1 dominant | A2 dominant | A3 dominant |
|---------|----------|-------------|-------------|-------------|
| Productive/Mixed | HIGH path | internal → REFLECT_INT | contribution → REFLECT_CONTRIB | self/team/others → either A3 reflect |
| Tough/Frustrating | LOW path | external → REFLECT_EXT | entitlement → REFLECT_ENTITLE | self/team/others → either A3 reflect |

Maximum possible unique paths through the tree: **8** (2 A1 routes × 2 A2 outcomes × 2 A3 outcomes).

Every path ends at SUMMARY → END. Every path is fully deterministic.

---

## Design Principles

- **No LLM at runtime.** The agent makes zero API calls. All intelligence is in the tree structure.
- **No free text.** Every question has fixed options. No NLP, no classification.
- **Same answers → same path.** The engine is pure lookups and tallies.
- **Reflections don't moralize.** Entitlement reflections invite curiosity, not shame. External-locus reflections acknowledge difficulty before noting agency.
- **Bridges earn their transitions.** Each bridge explicitly names what just happened and what comes next — the axes are a sequence, not three separate quizzes.
