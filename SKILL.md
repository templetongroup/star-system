---
name: star-system
description: Ask the user to rate the code/output just produced on a 1-5 star scale, then ask rating-appropriate follow-up questions to drive the next revision. Use when the user says "run the star system", "rate this", or invokes /star-system after a deliverable is complete.
---

# Star System — Code Rating & Feedback Loop

You have just delivered code or another work product, and the user wants to grade it. Run this process exactly.

## Step 1: Ask for the rating

Ask the user to rate the output you just produced, presenting this scale (use AskUserQuestion with the five options if that tool is available; otherwise ask in chat):

- ★ (1) — **Unacceptable.** Everything is wrong. The work must be redone from scratch.
- ★★ (2) — **Significant issues.** The code, UI, or another major element needs substantial rework.
- ★★★ (3) — **Acceptable.** A minimum viable product — works, but not exceptional.
- ★★★★ (4) — **Exceptional.** Very good; only minor tweaks needed in specific areas.
- ★★★★★ (5) — **Gold standard.** Exemplary. A model that all future output in this area should be measured against.

Wait for the user's answer. Do not guess or self-assign a rating.

## Step 2: Ask follow-up questions scaled to the rating

The lower the rating, the more you must learn before touching the code again. Ask the questions for the given rating (one message; use AskUserQuestion where it fits, free-form otherwise). Adapt wording to the actual deliverable — these are topics, not scripts.

### 1 star — full diagnostic (6-8 questions)
The output is being discarded, so re-establish requirements from zero:
1. What was the single biggest failure — wrong functionality, wrong approach, wrong design, or wrong understanding of the request?
2. Was the core requirement misunderstood? Restate what you built it to do and ask the user to correct it.
3. Is there *anything* in the current output worth salvaging, or is it a true clean-slate restart?
4. What should the rebuilt version do differently at the architectural/structural level?
5. Are there examples, references, or existing code the redo should follow?
6. What constraints (stack, style, performance, scope) were violated or missed?
7. What would a 3-star (acceptable) version of this look like, at minimum?
8. Anything else that went wrong that the above didn't cover?

### 2 stars — deep rework interview (5-6 questions)
Major surgery, not a restart:
1. Which areas are the significant problems — code quality, UI/UX, functionality, performance, or something else? (multi-select)
2. For each problem area named: what specifically is wrong, and what would "fixed" look like?
3. Which parts are working well enough to leave alone?
4. In what order should the problems be fixed (what's most painful)?
5. Are the issues fixable within the current approach, or does some part need a redesign?
6. What would move this to 4 stars?

### 3 stars — elevation interview (3-4 questions)
It works; find out what separates MVP from exceptional:
1. What's the biggest gap between this and what you'd call exceptional?
2. Which areas feel most "bare minimum" — polish, edge cases, UX, code structure?
3. Are there missing features or refinements that were expected but not delivered?
4. If only one thing could be improved, what should it be?

### 4 stars — tweak targeting (1-3 questions)
Close to perfect; identify the specific minor tweaks:
1. Which specific areas need the minor tweaks?
2. For each: what exactly should change?
3. Optionally: what small thing kept this from being 5 stars?

### 5 stars — no questions
Ask nothing. Instead:
1. Acknowledge the gold-standard rating.
2. Briefly summarize (2-4 bullets) what made this output exemplary — the patterns, structure, and decisions worth repeating — so it can serve as the reference model for future work in this area.
3. If a memory system or project notes file (e.g. CLAUDE.md) is available, offer to record this output as the gold-standard reference for its category.

## Step 3: Confirm the action plan

For ratings 1-4, after the user answers:
1. Play back what you heard as a concise, prioritized action plan (redo plan for 1 star; fix list for 2-4).
2. Ask the user to confirm or correct the plan.
3. Once confirmed, execute it.

## Rules

- Never skip Step 1 or assume a rating from context.
- Never argue with or negotiate the rating. The rating is the user's verdict; your job is to extract actionable specifics.
- Scale strictly: 1 star = most questions, 4 stars = fewest, 5 stars = zero.
- Don't ask questions the user already answered — if they gave the rating alongside detailed feedback, only ask about the gaps.
- Keep the whole exchange efficient: batch questions rather than dribbling them one per message, unless an answer genuinely gates the next question.
