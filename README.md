# Star System

A [Claude Code skill](https://docs.claude.com/en/docs/claude-code/skills) that turns code review into a structured 1-5 star feedback loop.

After an AI agent delivers code, invoke `/star-system`. The agent asks you for a star rating, then asks follow-up questions scaled to the score — a full diagnostic at 1 star, down to zero questions at 5 stars — and turns your answers into a confirmed action plan before revising.

## The scale

| Rating | Meaning |
|---|---|
| ★ | Unacceptable — start over from scratch |
| ★★ | Significant issues — major rework needed |
| ★★★ | Acceptable — a working MVP, not exceptional |
| ★★★★ | Exceptional — minor tweaks only |
| ★★★★★ | Gold standard — the model future work is measured against |

## Install

Copy this directory to `~/.claude/skills/star-system/` (personal) or `.claude/skills/star-system/` in a project, then invoke with `/star-system`.
