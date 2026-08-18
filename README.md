# Star System

A rating-and-feedback protocol for AI-generated code. **Model-agnostic and harness-agnostic** — the protocol is plain markdown instructions that work with any AI model, in any agent harness, IDE, or chat window.

After an AI agent delivers code, invoke the protocol. The agent asks you for a 1–5 star rating, asks follow-up questions scaled to the score — a full diagnostic at 1 star, down to zero questions at 5 — turns your answers into a confirmed action plan, executes it, and asks you to **re-rate until the work reaches 4+ stars**.

## The scale

| Rating | Meaning |
|---|---|
| ★ | Unacceptable — start over from scratch |
| ★★ | Significant issues — major rework needed |
| ★★★ | Acceptable — a working MVP, not exceptional |
| ★★★★ | Exceptional — minor tweaks only |
| ★★★★★ | Gold standard — the model future work is measured against |

## Features

- **Scaled questioning** — 6–8 diagnostic questions at 1 star, 1–3 at 4 stars, zero at 5.
- **Optional sub-scores** — 2–3 star ratings can be broken down (code quality / UI / functionality / requirements fit) so questions target the weak dimension.
- **Rating log** — every round is appended to a `ratings.md` in the reviewed project, building a history.
- **Gold-standard registry** — 5-star outputs are recorded permanently with *where* the code lives and *why* it's exemplary, so future work is measured against it.
- **Re-rating loop** — after fixes, the agent asks you to re-rate; the cycle repeats until you give 4+ stars or call it off.

## Example

> **Agent:** How would you rate the pricing page I just built? ★ start over · ★★ major issues · ★★★ acceptable MVP · ★★★★ minor tweaks · ★★★★★ gold standard
>
> **You:** 2 stars.
>
> **Agent:** Understood. Optionally, score the dimensions so I target the right problems: code quality, UI/UX, functionality, requirements fit?
>
> **You:** UI is a 1, functionality maybe 4.
>
> **Agent:** Then I'll focus there: What specifically is wrong with the UI, and what would "fixed" look like? Which parts should I leave alone? What order should I fix things in — what's most painful? Would fixing the UI within the current layout work, or does it need a redesign? What would move this to 4 stars?
>
> **You:** *(answers)*
>
> **Agent:** Here's the plan I heard: 1) rebuild the layout on a grid, 2) fix the mobile breakpoints, 3) match the brand palette. Confirm? *(…executes, logs the round to `ratings.md`, then asks you to re-rate.)*

## Install

**Any agent:** paste the contents of [`PROMPT.md`](PROMPT.md) into your agent after it delivers work, or save it wherever your harness loads instructions from (custom instructions, system prompt, skills directory, `.cursorrules`, `AGENTS.md`, …).

**Harnesses with a skills directory:** clone this repo into it, e.g.:

```bash
git clone https://github.com/templetongroup/star-system ~/.claude/skills/star-system
```

## Files

- [`SKILL.md`](SKILL.md) — the protocol in skill format (YAML frontmatter + instructions; body is harness-agnostic)
- [`PROMPT.md`](PROMPT.md) — the same protocol as a paste-anywhere prompt
- [`LICENSE`](LICENSE) — MIT
