# claude-skill-cialdini-influence-audit

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Built for Claude](https://img.shields.io/badge/Built%20for-Claude-D97757)](https://claude.com)
[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](#)

> A Claude skill that audits persuasive copy (landing page, email, sales sequence, cold pitch) for missing influence principles using Robert Cialdini's seven principles from Influence (1984/2016) and Pre-Suasion (2016). Returns a per-principle audit with prioritized fixes.

You drop your copy into Claude. The skill scores each of the 7 principles as PRESENT, WEAK, or MISSING, audits the opener for Pre-Suasion attentional channeling, and returns a Top 3 Fixes block you can ship the same day.

This skill audits copy. It does not generate copy from scratch. If you want a generator, look elsewhere.

---

## Why this skill exists

Cialdini's seven principles of influence are taught everywhere, but most online tools that mention them are generators or shallow checklists. They build copy from a blank page, or they list the 7 principles without telling you which ones your existing copy already uses, which are weak, and which are missing.

This skill is audit-first. You bring an existing piece of copy. The skill scores each principle on a three-level scale (PRESENT / WEAK / MISSING) with one-line evidence per principle. It also audits the opener using the Pre-Suasion lens: is the first sentence channeling attention toward concepts that favor the request, or is it wasting the privileged moment?

It includes an anti-overstacking check: when 5 or more principles are already strongly present, the skill flips its recommendation from "add more" to "RESTRAINT: cut the weakest application." Stacking all 7 reads as manipulation. The audit catches that before you ship.

---

## Install

Skills do not sync across surfaces (per [Anthropic's Agent Skills docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview#cross-surface-availability)). Install on each surface where you want to run this skill.

### Claude Code (CLI)

Two paths. Use git clone today; the plugin marketplace listing is pending Anthropic approval.

**Option A: git clone (works today).** Clone the repo and load it with the `--plugin-dir` flag:

```bash
git clone https://github.com/johnericforte/claude-skill-cialdini-influence-audit.git ~/claude-plugins/cialdini-influence-audit
claude --plugin-dir ~/claude-plugins/cialdini-influence-audit
```

To verify the plugin loaded, run `/help` in Claude Code. You should see `cialdini-influence-audit:audit` listed.

**Option B: Plugin marketplace (pending Anthropic approval).** Once the listing lands:

```
/plugin install cialdini-influence-audit
```

### claude.ai (web) / Claude Desktop

ZIP the `skills/audit/` directory and upload it via **Settings → Features → Skills** on claude.ai. The skill syncs to Claude Desktop through your account. Requires a Pro, Max, Team, or Enterprise plan with code execution enabled. See [Anthropic's docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for plan requirements and limits.

### Invocation (Claude Code)

Once loaded in Claude Code, invoke the skill with the plugin-namespaced name:

```
/cialdini-influence-audit:audit
```

### Optional dependency: `humanizer`

The skill works best with the [`humanizer`](https://github.com/blader/humanizer) skill installed for the final pass on the audit's "After" copy. The first time you invoke this skill, it will check for `humanizer` and OFFER to install it for you (with your explicit approval). You can accept, decline, or install it manually:

```bash
git clone https://github.com/blader/humanizer.git ~/.claude/skills/humanizer
```

`humanizer` is a standalone skill (not a plugin), so it installs to the standard `~/.claude/skills/` directory.

If you decline, the skill ships the audit without the humanizer pass and labels it accordingly.

---

## Quick start

Once installed, invoke the skill via Claude:

```
Use the cialdini-influence-audit:audit skill on this cold email:

"Hi [First Name],
I noticed your company is in the SaaS space and thought you might be
interested in our platform. We help companies like yours scale their
operations through our innovative solution.

Would you be open to a 15-minute call this week to discuss?

Best, Alex"

Audience: B2B SaaS founders. Goal: book a demo. Skip pre-audit research; I know my audience.
```

Claude will:

1. Confirm copy type (cold email) and input format (pasted text)
2. Skip the pre-audit research mode (you opted out)
3. Score each of the 7 principles as PRESENT / WEAK / MISSING with one-sentence evidence
4. Audit the Pre-Suasion opener
5. Run the anti-overstacking check
6. Output a Top 3 Fixes block with before/after examples
7. Optionally invoke the `humanizer` skill on the "After" copy if you have it installed

---

## Demo

### Before (the input you give Claude)

> "Hi [First Name],
> I noticed your company is in the SaaS space and thought you might be interested in our platform. We help companies like yours scale their operations through our innovative solution.
> Would you be open to a 15-minute call this week to discuss?
> Best, Alex"

### After (the audit Claude returns)

**Principle Audit Block:**

- Reciprocity: MISSING. The email asks for time without offering anything first.
- Commitment / Consistency: MISSING. No reference to anything the prospect has said, done, or committed to.
- Social Proof: MISSING. "Companies like yours" is generic; no named customers or specific results.
- Authority: WEAK. "Alex" with no title, company, or credential.
- Liking: WEAK. Generic opener signals templated outreach, not genuine attention.
- Scarcity: MISSING. No reason "this week" matters more than next month.
- Unity: MISSING. No in-group identity established.

**Pre-Suasion Opener Audit:**

- Verdict: WEAK. The opener channels attention to the SENDER ("our platform") instead of the prospect's existing focus.

**Top 3 Fixes:**

1. **Add Reciprocity (give before asking).**
   - Before: "I noticed your company is in the SaaS space and thought you might be interested in our platform."
   - After: "I spent 30 minutes reviewing your pricing page yesterday. One thing stood out: your enterprise tier doesn't show a case study, which usually costs SaaS companies 12-18% on close rate at that price point."

2. **Add Authority (establish credentials and named work).**
   - Before: "Best, Alex"
   - After: "Best, Alex Chen. I run pricing audits for SaaS companies between $1M and $10M ARR. Recent work: [Named Customer A] (raised average contract value 28%) and [Named Customer B] (cut churn by 19%)."

3. **Add Pre-Suasion opener (channel attention to the prospect's stated priority).**
   - Before: "Hi [First Name], I noticed your company is in the SaaS space..."
   - After: "Hi [First Name], your Q3 earnings call mentioned enterprise expansion as a 2026 priority. The next three lines are about one thing in your funnel that's quietly capping that goal."

**Anti-overstacking check:** not triggered. The email is currently understacked. The 3 fixes intentionally do NOT add all missing principles; adding all 7 would push the email into manipulation territory.

---

## Use cases

- B2B founder writing a cold email sequence and wanting to know which principles are missing
- Marketer auditing a landing page that is converting below benchmark
- Copywriter reviewing a sales page for a course or coaching program before launch
- Donation page or nonprofit campaign audit (Reciprocity + Commitment + Unity stack heavily here)
- Product launch announcement audit (Scarcity + Social Proof + Authority stack heavily here)
- Speech, keynote, or pitch opener audit using the Pre-Suasion lens

---

## How it works

The skill follows an 8-step audit workflow:

1. **Confirm copy type and input format.** Landing page, email, sales sequence, cold pitch, ad. URL or pasted text.
2. **Offer pre-audit research mode.** Optional. The skill asks per dimension (audience profile, Pre-Suasion opener context, social-proof fact-check) whether you want a research agent to fill in missing inputs. You can skip and go straight to the audit using only what you provided.
3. **Extract intent dimensions.** Audience, goal, existing claims, sender. Clarifying questions if any critical dimension is still missing after the optional research.
4. **Score each of the 7 principles** as PRESENT / WEAK / MISSING with one-sentence evidence per principle.
5. **Score the Pre-Suasion opener** as YES / WEAK / NO.
6. **Anti-overstacking check.** If 5 or more principles are PRESENT (strongly), the recommendation flips: identify weakest applications and recommend cutting them.
7. **Output the Audit Block + Top 3 Fixes.** Each fix targets a MISSING or WEAK principle with a before/after example.
8. **Final humanization pass.** If you have the [`humanizer`](https://github.com/blader/humanizer) skill installed, the skill invokes it on the "After" copy in the Top 3 Fixes block. If not installed, the audit ships as-is.

The full mechanic, framework definitions, and scoring rubric live in [`SKILL.md`](./SKILL.md). Reference cards for each framework live in [`references/`](./references/).

---

## Companion skills

These pair well with `cialdini-influence-audit`:

- **[`hormozi-offer-audit`](https://github.com/johnericforte/claude-skill-hormozi-offer-audit)**: for the OFFER side of the same copy (Value Equation, Grand Slam, lead magnet quality bar). Run on the same page after the Cialdini audit to find missing offer levers. Cialdini audits the persuasion mechanics; hormozi-offer-audit audits the offer construction.
- **[`claude-blog-assistant`](https://github.com/johnericforte/claude-skill-blog-assistant)**: if the persuasive copy lives inside a blog post, this orchestrator wraps the full publishing lifecycle AND audits existing posts. Pair with the Cialdini audit when shipping new blog content.
- **[`humanizer`](https://github.com/blader/humanizer)**: strips AI vocabulary, em-dash overuse, rule-of-three padding, and other AI-writing tells from the "After" copy in your audit. Invoked automatically by this skill if installed.

You do not need either to run this skill. Both raise the quality of the output if installed.

---

## FAQ

**Is this skill affiliated with Robert Cialdini?**

No. This is an independent open-source tool. It is not affiliated with, endorsed by, or sponsored by Robert Cialdini or Influence At Work®. Frameworks are referenced descriptively under nominative fair use. See [`DISCLAIMER.md`](./DISCLAIMER.md).

**Is this a substitute for reading the books?**

No. The books are the source of truth. This skill is a derivative reference for audit-tool use. If your work depends on the frameworks, read _Influence_ (1984; New and Expanded 2021) and _Pre-Suasion_ (2016).

**Can I use this for commercial work?**

Yes. The skill is MIT-licensed. You can use it on client work, paid copy audits, and any other commercial application.

**Why does the skill have an anti-overstacking rule?**

Stacking all 7 principles into the same piece of copy reads as MANIPULATION. Audiences pattern-match high-pressure copy quickly and bounce. The skill checks for overstacking before recommending additions: if 5 or more principles are already strongly present, the recommendation flips to RESTRAINT (cut the weakest application). High-trust copy typically uses 2-4 principles strongly and leaves headroom.

**What's the difference between Liking and Unity? They sound similar.**

Liking is "I like you" (driven by warmth, similarity, compliments). Unity is "we are the same kind of people" (driven by shared identity, profession, struggle, geography, values). A friendly cold email with a warm tone signals Liking. A cold email that names a shared professional identity (e.g., "fellow indie SaaS founders") signals Unity. The skill scores them separately and flags this distinction explicitly.

**Does the skill work with tools other than Claude Code?**

The skill is written in the Claude Code skill format (`SKILL.md` + frontmatter). It also works in OpenCode, which uses the same skill format. For other tools, you may need to adapt the format manually.

**What if I want a tool that GENERATES persuasive copy from scratch instead of auditing existing copy?**

This skill is audit-first. For generation, look at other skills in the ecosystem.

**How do I update the skill when Cialdini publishes new material?**

Open an issue or pull request on the repo. Framework updates and corrections are welcome.

---

## Sources & attribution

Frameworks referenced descriptively under nominative fair use. Not affiliated with or endorsed by Robert Cialdini or Influence At Work®.

**Primary sources (the books are the source of truth):**

- Cialdini, Robert B. _Influence: The Psychology of Persuasion_. William Morrow, 1984. (New and Expanded edition, 2021.)
- Cialdini, Robert B. _Pre-Suasion: A Revolutionary Way to Influence and Persuade_. Simon & Schuster, 2016.

**Verified online references:**

- [Robert Cialdini (Wikipedia)](https://en.wikipedia.org/wiki/Robert_Cialdini)
- [Influence: The Psychology of Persuasion (Wikipedia)](https://en.wikipedia.org/wiki/Influence:_The_Psychology_of_Persuasion)
- [Influence at Work® (official company site)](https://www.influenceatwork.com)

Full source list, prior art, and the verification status of every framework definition: [`references/sources.md`](./references/sources.md).

For the full disclaimer on trademarks, fair use, and the limits of this skill, see [`DISCLAIMER.md`](./DISCLAIMER.md).

---

## Contributing

Pull requests welcome. Especially:

- Framework verification corrections (cite the book chapter and edition)
- Additional worked examples in `references/examples/` (one example per copy type)
- Bug reports on audit logic that misfires on real copy

For framework misattribution or trademark concerns, open an issue or contact the maintainer through the channels in the Author section below. The author will respond and adjust in good faith.

---

## Author

Built by **Eric Forte**, AI Automation Engineer for GoHighLevel Marketing Agencies.

- Website: [ericforte.com](https://www.ericforte.com)
- Blog: [ericforte.com/blog](https://www.ericforte.com/blog)
- LinkedIn: [@johnericforte](https://www.linkedin.com/in/johnericforte/)

---

## License

[MIT](./LICENSE) © 2026 Eric Forte
