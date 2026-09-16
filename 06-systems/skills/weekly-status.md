# Skill: Weekly Status

*A reusable prompt/skill for this project. Not a globally installed Claude skill — just a markdown file Claude can be pointed to when asked for a weekly status update.*

## When to use this

Use whenever raw, unstructured bullet notes need to become a weekly status update — for the squad, for leadership, or for your own record.

## Input

Raw bullet points, in any order, mixing done work, ongoing work, blockers, and forward-looking items. No required structure — fragments and shorthand are fine.

## Output

Four sections, in this order:

```
## Shipped
- ...

## In Progress
- ...

## Blockers
- ...

## Next Week
- ...
```

## Rules for sorting input into sections

- **Shipped** — anything completed, launched, or closed out. Past tense.
- **In Progress** — active work, not yet done. No firm completion signal.
- **Blockers** — anything explicitly stuck, waiting on someone/something, or flagged as a risk. If a bullet mentions a dependency or "waiting on," it goes here even if it also sounds like in-progress work.
- **Next Week** — forward-looking items: planned work, upcoming decisions, things explicitly framed as "next."

## Formatting rules

- One bullet per item. Keep each bullet to a single line where possible.
- Clean up grammar and tighten phrasing, but preserve the original meaning — don't add detail, context, or outcomes that weren't in the raw input.
- If a raw bullet doesn't clearly say what happened (e.g., ambiguous between Shipped and In Progress), default to **In Progress** rather than guessing it's done.
- If a section has no input to put in it, keep the header and write `- None this week.` rather than omitting the section.
- Do not invent metrics, dates, or names not present in the raw input.

## Example

**Raw input:**
```
- finished the comeback screen spec, raj is starting build monday
- still waiting on legal review for the streak-freeze copy
- data pull for churn cohort done
- need to schedule the leadership readout
```

**Output:**
```
## Shipped
- Finished the Comeback screen spec.
- Completed the data pull for the churn cohort.

## In Progress
- Raj starting build on the Comeback screen Monday.

## Blockers
- Waiting on legal review for streak-freeze copy.

## Next Week
- Schedule the leadership readout.
```
