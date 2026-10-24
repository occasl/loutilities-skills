# loutilities-skills

A Claude Code plugin with two skills: `route` sends each request to the best model, and `humanize` revises AI-drafted prose so it reads less formulaic.

- **route**: classifies a request and either answers it directly or delegates it to a chosen provider and model.
- **humanize**: a light editing pass for prose people will read (posts, emails, copy, stories, essays).

## Install

```
/plugin marketplace add occasl/loutilities-skills
/plugin install loutilities-skills@loutilities-skills
```

Restart or reload Claude Code (`/reload-plugins`) if the skills don't appear.

## Usage

Plugin skills are namespaced, so invoke them as `/loutilities-skills:route` and `/loutilities-skills:humanize`.

```
/loutilities-skills:route draft a migration plan from Postgres 14 to 16
/loutilities-skills:humanize <paste your blog post draft here>
```

## route

Classifies each request using the whole conversation, then acts. It never asks you which model to use. Stakes override size: medical, legal, financial, security, and production-data requests are never `quick`.

| Class | Used for | Goes to |
|---|---|---|
| quick | one-liners, lookups, small standalone Q&A | answered directly, no delegation |
| biz | analysis, plans, spreadsheets, meeting prep, summaries | Sonnet High; Opus High for hard analysis |
| write | prose for people: copy, essays, editing, routine emails | Gemini |
| create | fiction, naming, concepts, campaigns, ideation | Opus High |
| deck | slide decks | Opus High (drafts: Sonnet High) |
| code | build, fix, refactor, review code | Sonnet High for bounded work, Opus High for hard work, plan-then-implement chain for big projects |
| multimodal | image, audio, video, PDF input | Gemini |
| review overlay | "council of N", "adversarial review", "red team", "critique this" | several reviewers from other vendors, then a synthesis |

Prose routes also get a `humanize` pass before the result is returned.

### Prefix overrides

Start a request with a prefix to force the route. The prefix is stripped before delegating.

- `!quick`, `!biz`, `!write`, `!create`, `!deck`, `!multimodal`, `!code`: force that class.
- `!opusplan`: force the plan-then-implement chain (Opus plans, Sonnet implements).
- `!raw`: skip the humanize writing pass for this request.

### Requirements

- `route` delegates through T3 Code's `t3-code` MCP tools: `delegate_task`, `task_status`, and `orchestrator_capabilities`. Without T3 Code it can only answer directly.
- It also needs access to the model IDs it names: `claude-opus-5-5`, `claude-sonnet-5-5`, `claude-haiku-5-5`, `gpt-6.1-sol`, `gpt-6-astra`, `gemini-4-argon-high`, and a few others.
- The `route` skill is the one that names specific model IDs and providers (`claudeAgent`, `codex`, `antigravity`). They match the author's setup. Edit `skills/route/SKILL.md` to match the providers and models you have.

## humanize

Revises narrative and marketing prose to fix patterns that one study of AI-written stories (StoryScope, arXiv 2604.03136) found: over-explained morals, tidy single-track plots, morally simple protagonists, purely linear structure, and model-specific tics. It makes the smallest edit that fixes a pattern, keeps your voice, and returns the revised text plus a short change list. It is a craft revision, not AI-detector evasion.

Requirements: none. It also runs on its own as the writing pass inside `route`.

## Auto-routing

The `route` skill does not run on every request by itself. If you want that, add a rule to your own `~/.claude/CLAUDE.md`. Example:

```markdown
# Model routing

For every user request, invoke the `loutilities-skills:route` skill before answering,
unless the request already invoked it. Its prefix overrides (`!quick`, `!code`, and so on) still apply.
```

If you only want it for a cheap model, make the rule conditional on the model ID (for example, only when it starts with `claude-haiku-`).

## License

MIT. See [LICENSE](LICENSE).

This is an unofficial personal toolset. It is not affiliated with or endorsed by Anthropic or T3 Code.
