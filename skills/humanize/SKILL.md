---
name: humanize
description: Revise AI-drafted prose meant for people to read (blog posts, slide-deck text, emails, social posts, marketing copy, stories, essays) to fix patterns StoryScope (arXiv 2604.03136) found distinguish AI stories from human ones: over-explained themes, tidy single-track plots, morally simple protagonists, purely linear structure, model-specific tics. Runs as the route skill's writing pass. Skip internal or agent-facing text, code, data, review output. Also use when asked to humanize, de-AI, or make a story less formulaic. Craft revision only, not detector evasion.
---

# Humanize

Revise narrative prose so it reads less formulaic. Source: StoryScope (Russell, Rajendhran, Iyyer, Wieting; COLM 2026 / arXiv 2604.03136). That paper is a detection study. Its findings are tendencies from one corpus (10,272 prompts, one human and five LLM stories each), not rules.

## Scope

- Only for prose that people will read: blog posts, slide-deck text, emails, social posts, marketing copy, stories, essays.
- Skip internal or agent-facing text, code, JSON, data, tables, exact legal or policy wording, citations, calculations, scoped edits, and review output.
- Work on the user's own text, or on drafts (including model-generated ones) they plan to present as their own writing.
- Do not tune text to beat AI detectors or to hide AI authorship where that would deceive readers. If asked, say that part is out of scope and offer the craft revision instead.

## Process

1. Read the whole piece before editing. Note its voice, tense, POV, and plot facts. Keep all of them.
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

For essays, copy, and posts, use only these rows: over-explained conclusions, samey structure, and model tics. Skip plot, moral-ambiguity, and dream rows. Also cut generic openers and closers that restate the point.

## Rules

- Findings are prompts to look, not quotas. A story with no flagged pattern needs no edits.
- Do not add plot, characters, or facts the user didn't write.
- If a revision would change plot or meaning, flag it and ask instead of making it.
- Keep the change list short. No essay on the paper.
