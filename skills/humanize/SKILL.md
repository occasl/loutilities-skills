---
name: humanize
description: Revise AI-drafted prose meant for people to read (blog posts, slide-deck text, emails, LinkedIn and other social posts, executive writing, marketing, sales, and product copy, stories, essays) to fix formulaic, model-sounding patterns. Runs as the route skill's writing pass. Skip internal or agent-facing text, code, data, review output. Also use when asked to humanize, de-AI, or make a story less formulaic. Craft revision only, not detector evasion.
---

# Humanize

Revise prose so it reads less formulaic. Narrative findings come from StoryScope (Russell, Rajendhran, Iyyer, Wieting; COLM 2026 / arXiv 2604.03136). That paper is a detection study. Its findings are tendencies from one corpus (10,272 prompts, one human and five LLM stories each), not rules. The business rules come from editorial practice, not from that paper.

## Scope

- Only for prose that people will read: blog posts, slide-deck text, emails, LinkedIn and other social posts, executive updates, marketing, sales, and product copy, stories, essays.
- Skip internal or agent-facing text, code, JSON, data, tables, citations, calculations, scoped edits, and review output.
- Protect only the spans that are legal, policy, or pricing wording: leave them byte-for-byte and list them in the change list as "locked, untouched".
- Work on the user's own text, or on drafts (including model-generated ones) they plan to present as their own writing.
- Do not tune text to beat AI detectors or to hide AI authorship where that would deceive readers. If asked, say that part is out of scope and offer the craft revision instead.

## Process

1. Read the whole piece before editing. Identify the text type (story, essay, LinkedIn post, email, executive update, marketing or sales copy, and so on). Note its voice, tense, POV, and plot facts. Lock numbers, names, quotes, disclosures, and legal spans before editing. Keep all of them.
2. Check each finding below. Revise only where the pattern actually appears.
3. Make the smallest edit that fixes the pattern. Keep the author's voice and sentences that already work.
4. Return the revised text, then a short change list: what changed, which finding it addresses.

## Findings to check

| Pattern (paper) | Check | Revision |
|---|---|---|
| Themes explained outright | Closing lines or dialogue that state the moral or lesson | Cut the statement. Let an image, action, or unresolved beat carry it. |
| Tidy, single-track plots | Every thread resolves cleanly; one storyline | Keep one spine, but allow a loose thread, a cost that stays, or a side concern that doesn't tie off. Only if it fits the story. |
| Morally simple protagonists | Protagonist's choices framed as clearly right or clearly wrong | Give the choice a real cost or a motive the reader can half-sympathize with. |
| Linear structure only | Strictly chronological scenes | Consider a flashback, time jump, or out-of-order scene if it serves the story. Don't add one mechanically. |
| Flat escalation (Claude tendency) | Tension rises in even, predictable steps | Vary the pacing. Let a beat stall, reverse, or land off-beat. |
| Dream sequences as default device (GPT tendency) | Dreams or visions used as a go-to turn | Cut any dream that is decorative. Keep one only if it does structural work. |
| External character description (Gemini tendency) | Paragraphs that catalogue appearance before action | Replace with action, speech, or what other characters notice. |
| Samey shapes across drafts | Several stories or chapters follow the same arc and ending | Vary openings, endings, and structure between pieces. |

## Non-fiction prose

For essays, copy, and posts, use only these rows: over-explained conclusions, samey structure, and model tics. Skip plot, moral-ambiguity, and dream rows. Also cut generic openers and closers that restate the point. For business formats, also apply "Business prose" below.

## Business prose

The skill picks these rules from the text type; there is no mode to set. Each is a prompt to look, not a quota. Rule 5 is for LinkedIn posts only; rule 10 is for emails and executive writing.

| # | Pattern | Check and fix | Example |
|---|---|---|---|
| 1 | Contrast frame | "Not just X, it's Y". State Y directly. | Before: This isn't just a report, it's a weekly snapshot. After: The report is a weekly snapshot. |
| 2 | Reflex triad | Three vague adjectives or benefits. Keep only items the draft backs up; log drops. | Before: A faster, simpler, smarter way to file. (Draft supports only "two fewer steps".) After: Filing takes two fewer steps. |
| 3 | Generic opener | "In today's fast-paced world", "I'm thrilled to announce". Open with the draft's first concrete point. | Before: I'm thrilled to announce our new intake form. After: The new intake form is live. |
| 4 | Reflex closer | "At the end of the day", "The bottom line?". End on the last concrete point or the ask. | Before: ...Send corrections by Friday. At the end of the day, clarity matters. After: ...Send corrections by Friday. |
| 5 | Engagement bait and hashtags | LinkedIn posts only. Cut "Agree?", "Thoughts?", "Comment YES", "Tag someone who", and hashtag walls. Keep up to three specific hashtags the author chose, and one real question if the author wants replies. Log every removal. | Before: Which step would you cut? Agree? Thoughts? #Success #Growth #Onboarding After: Which step would you cut? #Onboarding |
| 6 | Staged reveal | "Here's the kicker:", "The result?" followed by its answer. State the point. | Before: The result? Replies now go out the same day. After: Replies now go out the same day. |
| 7 | Buzzword stack | leverage, unlock, seamless, robust, game-changer, synergy. Replace only with a specific the draft already contains; otherwise cut or flag. No fixed swap list. | Before: Our robust platform unlocks seamless handoffs. (Draft elsewhere: "handoffs go into one shared queue".) After: Handoffs go into one shared queue. |
| 8 | Uniform rhythm | Five or more similar-length sentences in a row, or a one-sentence-per-line staircase. Merge and vary length. Leave lines that already work. | Before: We met Monday. We reviewed the plan. We moved the dates. We updated the owners. We sent notes. After: We met Monday, reviewed the plan, moved the dates, and updated the owners. Notes went out after. |
| 9 | Intensifier padding | truly, incredibly, very, "I genuinely believe". Cut. | Before: I genuinely believe this is a very important change. After: This is an important change. |
| 10 | Buried ask | The request or decision sits late, after context. Flag only; do not reorder. Note the ask and where it sits in the change list. | Flag: Ask ("please approve by Friday") is in paragraph 4 of 5; not moved. |
| 11 | Lesson list | "Here's what I learned:" followed by morals (LinkedIn story posts). Apply the "Themes explained outright" guidance above: keep specifics, cut restated morals. | Before: The handoff slipped twice. Here's what I learned: communication is key. After: The handoff slipped twice. |

## Rules

- Findings are prompts to look, not quotas. A story with no flagged pattern needs no edits.
- Do not add plot, characters, or facts the user didn't write.
- If a revision would change plot or meaning, flag it and ask instead of making it.
- Keep the change list short. No essay on the paper.
- Business guardrails:
  - Add no claims, metrics, percentages, customers, quotes, testimonials, awards, rankings, or endorsements. Never strengthen a claim ("can reduce" stays "can reduce"). Never turn an estimate into a firm figure. Log every removed claim in the change list.
  - Keep quotes and testimonials verbatim, including attribution.
  - Add no urgency or scarcity. Never remove an existing deadline.
  - Never remove, shorten, or move disclosures (#ad, sponsored, affiliate notes, "I work at"). If one looks missing, flag it briefly; never insert disclosure text.
  - Legal, policy, and pricing wording stays byte-identical.
  - No scores or verdicts, and never frame a revision as beating AI-text checks.
  - No posting, scheduling, or account-access steps.
- Output contract: the revised text, then the change list.
