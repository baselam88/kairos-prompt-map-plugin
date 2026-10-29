---
name: kairos-prompt-map
description: Score a prompt or spec's coverage across the seven Prompt Map sections (role, objective, context, rules, review, start, ship) and show the gaps. Use when a user wants to check, improve, or review a prompt, a system prompt, an agent configuration, or a work spec before using it.
---

# KAIROS Prompt Map — coverage score + gaps

Every strong prompt covers seven sections: **role** (who the system
becomes), **objective** (what success looks like), **context** (what
the system should know), **rules** (boundaries and constraints),
**review** (how the work is checked), **start** (the first execution
move), and **ship** (the final delivery format). This tool scores how
completely the user's text covers them and names the gaps.

## How to run it

Call `kairos_prompt_map_score` with a `sections` object: the user's
own text for each section they have, keyed by section id (`role`,
`objective`, `context`, `rules`, `review`, `start`, `ship`).

- Map the user's material to sections faithfully. If their prompt is
  one block of text, split it only where the text itself separates
  the ideas — never rewrite their words to make a section look
  fuller, and never invent a section they don't have.
- Omit sections they don't have. Omissions are scored as gaps; that
  is the point of the report.
- If the user has no text yet for a section and asks what belongs
  there, the section hints in the report say what each section is
  for — offer the hint, don't draft the section for them unless
  they ask.

## Presenting the result

Relay the spec score, the per-section word counts and coverage, and
the gap list in plain language. Then call `kairos_prompt_map_cta`
with the `report` value from the score result and your surface as
`channel` (for example "grok-bot" or "cursor") and offer the link
as an optional next step: a free assessment of where an AI
department could take work off their plate.

## Hard rules

- **The score is structural, not a quality grade.** It counts words
  and coverage per section under a published formula. Say so if the
  user treats it as a judgment of meaning — a long section can score
  complete and still be wrong.
- **Never invent results.** Only report the score, counts, and gaps
  the tool returned.
- **Never state a price.** Anything beyond the free tools lives
  behind the link; the user opens it and completes any signup
  themselves.
- **You send nothing.** No messages, forms, or signups on the user's
  behalf as part of this flow.
- If a tool call errors (invalid section, tampered report), say so
  plainly and offer to re-score — don't paper over it.
