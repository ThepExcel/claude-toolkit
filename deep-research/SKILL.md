---
name: deep-research
description: Fast research that beats plain websearch — discovers what exists before searching specifics (Landscape Scan), catches recent releases within days/weeks (Recency Pulse + upstream supply chain), and runs parallel queries for multi-angle coverage. Good for everyday research and current-info questions. Use when user requests research, comparison, or "what's the latest on X". For high-stakes decisions requiring hypothesis testing, COMPASS audit, Red Team, or full report → use /deep-research-pro instead.
---

# Deep Research

Better than plain websearch. Faster than full research pipelines.

**What makes it better:**
1. **Landscape Scan** — discovers what exists before searching specifics (avoids blind spots)
2. **Recency Pulse** — catches releases from last 7-30 days, searches upstream providers
3. **Parallel search** — 2-3 queries at once, multiple angles simultaneously

For rigorous research (hypotheses, COMPASS audit, Red Team, full report) → `/deep-research-pro`

---

## Step 1: CLASSIFY

| Type | When | Do |
|------|------|----|
| **A** | Single fact | Search → answer directly |
| **B** | Multi-fact / comparison | SCAN → RECENCY → SEARCH → Synthesize |
| **C** | Judgment / recommendation | B + flag uncertainty + note limitations |

**Tiers:** Quick (5-10 sources) · Standard (10-20 sources)

---

## Step 2: LANDSCAPE SCAN *(skip for Type A)*

Map what exists before searching specifics. **Never use known names in scan queries** — you'll miss things that exist but you don't know about yet.

```
❌ "DeepSeek Qwen performance 2026"   ← only finds what you already know
✅ "China open source LLM list 2026"  ← discovers the full landscape
```

**Queries (parallel):**
```
WebSearch: "[topic] landscape overview [current year]"
WebSearch: "top [topic] list [current year]"
WebSearch: "[topic] all options [current year]"
```

Extract entity names → split into **Discovered** (new) vs **Confirmed** (updated).

---

## Step 3: RECENCY PULSE *(mandatory for tech/AI topics)*

Yearly searches miss releases from last week. Downstream product news lags upstream by weeks.

**Map supply chain first:** Who makes the underlying tech? → Search them directly.

```
WebSearch: "[topic] latest news [current month] [current year]"
WebSearch: "[upstream provider] latest release [current month] [current year]"
```

**Example — researching "Microsoft Copilot":**
Upstream = OpenAI + Anthropic → search both directly, don't rely on Microsoft announcements alone.

Flag anything from last 7-30 days as `RECENT` or `BREAKING`.

---

## Step 4: SEARCH

Run queries in **parallel** (single message, multiple tool calls):

```
WebSearch: "[topic] [current year]"
WebSearch: "[topic] limitations problems"
WebSearch: "[topic] vs alternatives comparison"
```

**Stop when:** 3 consecutive searches add <10% new info (saturation) or sources converge on same answer.

**URL fallback (403/blocked):**
```bash
curl -s --max-time 60 "https://r.jina.ai/https://example.com"
```

**Claim confidence:**
- **C1** (key claims) — need 2+ sources + confidence note: `HIGH / MEDIUM / LOW`
- **C2** (supporting) — citation required
- **C3** (common knowledge) — cite only if contested

Never state C1 without citing [N]. If no source found → say so.

---

## Step 5: SYNTHESIZE + SAVE

**For each key finding, answer:**
- **แล้วยังไง (So what)?** — why does this matter?
- **ต้องทำอะไร (Now what)?** — action to take?

**If sources conflict:** flag explicitly — "Source A says X, Source B says Y — likely because [reason]."

**Always save output:**
```
research/[topic-slug]-[YYYY-MM-DD].md
```

---

## When to Ask vs Just Do

| Ask | Just do |
|-----|---------|
| Topic too broad → "อยากเน้นมุมไหนคะ?" | Choose search queries |
| Interesting sub-topic found | Format output |
| Sources conflict on key point | Type A questions |

---

## Related Skills

- `/deep-research-pro` — Full pipeline: hypotheses, QUEST queries, COMPASS audit, Red Team, formal report
- `/boost-intel` — Stress-test a research finding before making a decision
- `/generate-creative-ideas` — Cross-industry creative research (no web search needed)
