# Standard Mode: Enhanced Research Pipeline

## Contents
- [Phase 0: CLASSIFY](#phase-0-classify)
- [Phase 1: SCOPE](#phase-1-scope)
- [Phase 1.5: HYPOTHESIZE](#phase-15-hypothesize)
- [Phase 2: PLAN](#phase-2-plan)
- [Phase 2.5: PLAN PREVIEW](#phase-25-plan-preview)
- [Phase 3: RETRIEVE](#phase-3-retrieve)
- [Phase 3.5: GAP ANALYSIS](#phase-35-gap-analysis)
- [Phase 4: TRIANGULATE](#phase-4-triangulate)
- [Phase 5: SYNTHESIZE](#phase-5-synthesize)
- [Phase 6: RED TEAM](#phase-6-red-team)
- [Phase 6.5: SELF-CRITIQUE](#phase-65-self-critique)
- [Phase 7: PACKAGE](#phase-7-package)
- [Quality Checklist](#quality-checklist)

---

## Phase 0: CLASSIFY

**Objective:** Route questions to appropriate process intensity

| Type | Characteristics | Process |
|------|-----------------|---------|
| **A: LOOKUP** | Single fact, known source | WebSearch → Answer. 1-2 min. |
| **B: SYNTHESIS** | Multi-fact aggregation | 3 phases. 10 min. |
| **C: ANALYSIS** | Judgment needed | 6 phases. 20-30 min. |
| **D: INVESTIGATION** | Novel/conflicting | Full pipeline + Red Team. 45-60 min. |

**Gate**: Classification explicit before proceeding.

---

## Phase 1: SCOPE

**Objective:** Define research boundaries and success criteria

| Input | Description |
|-------|-------------|
| **Core question** | One-sentence research question |
| **Decision/use-case** | What will this inform? |
| **Audience** | Executive / Technical / Mixed |
| **Scope** | Geography, timeframe, in/out of scope |
| **Constraints** | Banned sources, required sources |
| **Definition of Done** | Measurable completion criteria |

**Gate**: Scope + definition of done explicit.

---

## Phase 1.5: HYPOTHESIZE

**Objective:** Transform research into hypothesis testing

1. Generate 3-5 testable hypotheses
2. Assign prior probability: High (70-90%) / Medium (40-70%) / Low (10-40%)
3. Design research to CONFIRM or DISCONFIRM each
4. Track probability shifts as evidence accumulates

**Requirements:**
- At least 3 hypotheses before Phase 2
- Include at least one contrarian hypothesis
- Track probability shifts in final report

**Gate**: 3+ hypotheses generated.

---

## Phase 2: PLAN

**Objective:** Create intelligent research roadmap

1. Identify 5-10 primary sources
2. List 5-10 secondary/backup sources
3. Create 10-15 search query variations
4. Plan triangulation approach

**Search Query Patterns:**

| Pattern | Example |
|---------|---------|
| Category + timeframe | "AI coding assistants December 2025" |
| Comparison + latest | "Claude vs GPT comparison 2025" |
| Limitations + problems | "[topic] limitations challenges" |
| Academic | "[topic] research paper arxiv" |

**Gate**: Each subquestion has 3+ queries and 2+ source classes.

---

## Phase 2.5: PLAN PREVIEW

**Objective:** User validation before executing (Deep+ tier only)

Present plan and ask: **"ต้องการปรับแผนก่อนเริ่มไหมคะ?"**

| User Response | Action |
|---------------|--------|
| "proceed" / "ไปเลย" | Execute as planned |
| Adds/removes subquestion | Adjust plan |
| No response (30s) | Proceed with original |

**Gate**: User confirms OR timeout.

---

## Phase 3: RETRIEVE

**Objective:** Collect information using PARALLEL execution

### Parallel Execution (MANDATORY)

```
[Single message with multiple tool calls]
WebSearch: "[topic] 2025 state of the art"
WebSearch: "[topic] limitations challenges"
WebSearch: "[topic] vs alternatives comparison"
Task(agent): Academic paper analysis
```

### Backtrack Protocol

**When:** 3+ consecutive searches yield <10% new info

```
1. STOP current path
2. LOG: "⚠️ Dead-end: [query] → [reason]"
3. PIVOT: Alternative angle/terminology
4. RESUME with new queries
```

### URL Fetching

**Primary:** `WebFetch` tool

**Fallback (if 403/blocked):** Jina AI Reader
```bash
curl -s --max-time 60 "https://r.jina.ai/https://example.com/page"
```

**Gate**: Each subquestion has ≥3 sources and ≥1 high-quality.

---

## Phase 3.5: GAP ANALYSIS

**Objective:** Identify gaps, generate refined queries

After initial retrieval, assess:
- ✅ Questions answered
- ⚠️ Questions partially answered
- ❌ Questions unanswered
- Claims needing more evidence

**Iteration Rules:**
- Quick tier: 0-1 iterations
- Standard: 1-2 iterations
- Deep: 2-3 iterations
- Exhaustive: Until diminishing returns

**Gate**: Gap analysis completed; follow-up queries executed.

---

## Phase 4: TRIANGULATE

**Objective:** Validate information, assign claim types

### Claim Taxonomy

| Type | Requirements |
|------|--------------|
| **C1 Critical** | Quote + 2+ independent sources + confidence + reasoning |
| **C2 Supporting** | Citation required |
| **C3 Context** | Cite if contested |

### Confidence Reasoning (Required for C1)

```markdown
**Claim:** [Statement]
**Confidence:** HIGH/MEDIUM/LOW/SPECULATIVE
**Reason:** [Why this level]
**What would raise/lower:** [Evidence needed]
**Sources:** [1][2][3]
```

### Confidence Levels

| Level | Criteria |
|-------|----------|
| **HIGH (90%+)** | 3+ sources agree, large samples, replicated |
| **MEDIUM (60-90%)** | Single strong OR multiple weaker |
| **LOW (30-60%)** | Preliminary, expert opinion |
| **SPECULATIVE (<30%)** | Single weak, theoretical |

**Gate**: All C1 claims verified or marked unverified.

---

## Phase 5: SYNTHESIZE

**Objective:** Generate insights with Implications Engine

For every major finding, answer:

| Question | Purpose |
|----------|---------|
| **SO WHAT?** | Why does this matter? |
| **NOW WHAT?** | What action to take? |
| **WHAT IF?** | If trend continues/reverses? |

**Output format:**
```markdown
**ผลกระทบ (Implications):**
- **แล้วยังไง:** [Significance]
- **แล้วต้องทำอะไร:** [Action]
- **ถ้าเป็นอย่างนี้ต่อ:** [Scenario]
```

**Gate**: Every recommendation links to C1/C2 claims.

---

## Phase 6: RED TEAM

**Objective:** Find counter-evidence (Devil's Advocate)

**Deploy when:** Type D investigation OR user requests

Search for:
1. Data contradicting main findings
2. Case studies where approach FAILED
3. Expert opinions that DISAGREE
4. Methodological weaknesses
5. Edge cases where conclusions don't hold

**Requirements:**
- Present counterarguments at their STRONGEST
- Include "What would change our mind" triggers
- Section title: "ข้อจำกัดและหลักฐานที่ขัดแย้ง"

---

## Phase 6.5: SELF-CRITIQUE

**Objective:** Review quality before packaging

### Checklist

- [ ] Every C1 has citation + confidence
- [ ] Quotes are verbatim
- [ ] Evidence supports conclusions
- [ ] HIGH claims have 3+ sources
- [ ] All hypotheses have outcomes
- [ ] Red Team section present

### Common Issues

| Issue | Fix |
|-------|-----|
| Overclaiming | Add qualifiers, lower confidence |
| Missing nuance | Add "however" or "in some cases" |
| Stale citation | Flag or find newer source |
| Vague recommendation | Make actionable with details |

**Gate**: High-priority issues resolved.

---

## Phase 7: PACKAGE

**Objective:** Deliver professional research report

### Progressive Assembly

1. Executive Summary → Write
2. Hypothesis Results → Append
3. Introduction → Append
4. Findings (each with implications) → Append
5. Red Team / Limitations → Append
6. Recommendations → Append
7. Bibliography (ALL entries) → Append

### Anti-Truncation Rules

**FORBIDDEN:**
- "Content continues..."
- "Due to length..."
- Bibliography ranges "[8-75]"

**REQUIRED:**
- Complete each section fully
- Every citation [N] has full entry

---

## Quality Checklist

Before delivery:
- [ ] Every C1 has citation + confidence + reasoning
- [ ] C1 claims have 2+ independent sources
- [ ] Contradictions acknowledged
- [ ] Sources recent (<3 months for AI/tech)
- [ ] No unsupported claims
- [ ] Implications for each finding
- [ ] Red Team section included
- [ ] Self-critique completed
- [ ] Gap analysis performed
- [ ] Hypothesis outcomes reported
