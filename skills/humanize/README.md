# humanize

Revises AI-drafted prose so it reads less formulaic. It looks for specific patterns, such as over-explained morals, stock openers and closers, staged reveals, buzzword stacks, and uniform sentence rhythm, and makes the smallest edit that fixes each one. It keeps the author's voice and leaves sentences that already work alone.

## What it covers

- **Fiction and essays.** Narrative craft: stated morals, tidy plots, morally simple protagonists, linear structure, flat escalation, and model-specific tics.
- **Business prose.** LinkedIn posts, emails, executive updates, marketing, sales, and product copy, plus blog posts and slide-deck text. Rules cover contrast frames, reflex triads, generic openers and closers, engagement bait and hashtag walls (LinkedIn only), staged reveals, buzzword stacks, uniform rhythm, intensifier padding, and lesson lists. A buried ask in an email or executive update is flagged, not reordered.

## How to invoke

Implicit. Ask it to humanize a draft, and paste the text. The skill identifies the text type and applies the matching rules. There is no command or flag to set a mode.

## Output format

The revised text, followed by a short change list: what changed, which pattern it addresses, anything removed (claims, hashtags, dropped list items), anything flagged (a buried ask, a missing disclosure), and any spans listed as "locked, untouched".

## What it never changes

- Facts, figures, and names.
- Quotes and testimonials, including attribution.
- Disclosures (#ad, sponsored, affiliate notes, "I work at"). Missing ones are flagged, never added.
- Legal, policy, and pricing wording, which stays byte-identical.

It also adds no new claims or urgency, never strengthens a claim, and never removes an existing deadline.

## Testing your changes

- Keep your own sample drafts outside this repo.
- Run each sample before and after you edit `SKILL.md`, and compare the results.
- Check the list of things that must not change: numbers, names, quotes, disclosures, locked spans, and voice.
