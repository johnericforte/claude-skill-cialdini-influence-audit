# Audit Rubric — Scoring Guidance

> Companion to `seven-principles.md` and `pre-suasion.md`. Defines how to score, when to recommend additions, and when to recommend RESTRAINT.

## Scoring scale

Each of the 7 principles is scored on a 3-level scale:

| Level | Meaning |
| ----- | ------- |
| **PRESENT** | The principle is clearly applied in the copy. The signal is specific, on-audience, and consistent with the principle's mechanic. |
| **WEAK** | The principle is attempted but the execution falls short (vague, off-audience, or not credibly executed). |
| **MISSING** | The principle is not applied anywhere in the copy. |

Pre-Suasion opener is scored on a parallel 3-level scale:

| Level | Meaning |
| ----- | ------- |
| **YES** | Opener channels attention to a concept that favors the request. |
| **WEAK** | Opener is present but channels attention loosely or to a partially-relevant concept. |
| **NO** | Opener channels attention to the sender / brand / irrelevant concept. No privileged moment created. |

## Evidence requirement

Every principle score MUST cite a specific line in the copy that justifies the rating. One sentence per principle.

Examples:

- **Reciprocity: PRESENT.** "I spent 30 minutes reviewing your pricing page yesterday" delivers a specific, named gift before the ask.
- **Authority: WEAK.** Sender signs as "Alex" with no title or credentials. Brand has no third-party validators on the page.
- **Scarcity: MISSING.** No constraint on supply, time, or eligibility named anywhere.

If a principle's score depends on context the user did not provide, ask a clarifying question rather than guessing.

## Anti-overstacking check

Cialdini's principles are tools, not a checklist. Stacking all 7 in the same piece of copy reads as MANIPULATION and erodes trust. The skill must check for overstacking before recommending additions.

### When to flag overstacking

If 5 or more of the 7 principles are PRESENT (strongly), the recommendation flips:

- DON'T recommend adding the missing principles
- DO recommend RESTRAINT — identify the 1-2 weakest applications and recommend cutting or softening them

### How overstacking shows up

- A landing page that pairs heavy Scarcity ("Only 3 spots left! Ends midnight!") with heavy Authority ("As featured in TechCrunch, Forbes, Wired") with heavy Social Proof ("Used by 50,000+ teams") with heavy Reciprocity ("Free 47-page guide!") with heavy Commitment (5-step funnel) — the audience reads "high-pressure manipulation" and bounces.
- A cold email that hits Authority + Social Proof + Reciprocity + Pre-Suasion in 4 sentences feels like a sales script, not a human.
- A pitch deck with every slide leaning on a different principle reads as performative.

### What restraint looks like

A high-trust piece of copy typically uses 2-4 principles strongly, lets 1-2 sit lightly, and leaves 1-2 unused. The unused ones leave headroom — the reader senses the seller is NOT pulling every available lever, which paradoxically increases trust.

## Top 3 Fixes — selection logic

Always output exactly 3 fixes, prioritized by impact-to-effort ratio.

### Selection rules

1. At least one fix MUST target a MISSING or WEAK principle.
2. If the audit triggers overstacking (5+ PRESENT), at least one fix MUST be a CUT (remove or soften an existing principle), not an ADD.
3. If Pre-Suasion opener scored WEAK or NO, at least one fix targets the opener.
4. Fixes are ordered: highest impact-to-effort first.

### Per-fix output format

Each fix includes:

- The principle it adds, strengthens, or cuts (one principle per fix)
- A before/after example using the user's actual copy where possible
- A one-sentence "Why" tied to the principle's mechanic

Example:

```
Fix 1: Add Reciprocity (give before asking).
  Before: "I noticed your company is in the SaaS space and thought you might be
          interested in our platform."
  After:  "I spent 30 minutes reviewing your pricing page yesterday. One thing
          stood out: your enterprise tier doesn't show a case study, which
          usually costs SaaS companies 12-18% on close rate at that price point."
  Why:    Opens with delivered value (a specific observation), creating an
          obligation to engage rather than asking for time first.
```

## What NEVER to do in fixes

- Fabricate customer counts, named entities, or social-proof claims. If a fix calls for Social Proof, ask the user to supply real numbers or label the example with `[NAMED CUSTOMER]` placeholders.
- Recommend FAKE Scarcity. If the user's offer doesn't have real supply or time constraints, do not invent them.
- Stack principles when overstacking is already triggered. The fix recommendation must reflect the anti-overstacking rule.
- Recommend Pre-Suasion openers that channel attention to manipulative concepts (fear-driven openers, fake urgency, manufactured anxiety). Pre-Suasion is about channeling EXISTING focus, not creating false focus.

## Confidence scoring (optional layer)

When the audit is run on copy where critical context is missing (audience unclear, sender unknown, copy type ambiguous), prepend the audit with a confidence note:

```
Audit confidence: MEDIUM. Audience profile not provided. Some principle
scores depend on assumptions about what the target audience values.
Recommend running the audience-profile research agent before relying on
the Top 3 Fixes.
```

Confidence levels: HIGH (all critical dimensions known), MEDIUM (1-2 dimensions assumed), LOW (3+ dimensions assumed; recommend pre-audit research before audit).
