# Contributing

Thanks for helping improve Book Discovery Advisor.

## What makes a useful contribution?

High-value contributions include:

- better candidate-discovery strategies;
- stronger ways to distinguish popularity from suitability;
- international or local-language discovery guidance;
- methods for identifying direct endorsements vs. weak attribution;
- better edition-verification rules;
- preference-graph improvements that avoid overfitting;
- test prompts exposing bias, repetition, hallucinated bibliographic details, or weak criticism research;
- examples demonstrating successful reading paths and follow-up refinement.

## Principles to preserve

Please preserve these core properties unless a change explicitly proposes and justifies a different design:

1. Ask at most three clarification questions.
2. Research before selecting the final books.
3. Recommend ten books by default for open recommendation requests.
4. Preserve the 80% preference-match / 20% exploration model.
5. Search for substantive criticism as well as praise.
6. Do not invent editions, chapters, endorsements, quotes, reviews, or rankings.
7. Do not claim the Skill owns an independent persistent memory database.
8. Keep persistent preference signals durable, reading-relevant, and appropriately confidence-weighted.

## Making a change

1. Create a branch for the change.
2. Edit `SKILL.md` for core behavior or a file in `references/` for detailed methodology.
3. Add or update an example when the change affects observable recommendation behavior.
4. Validate the Skill using the current ChatGPT Skill validation/packaging workflow.
5. Rebuild `dist/skill.zip`.
6. Add an entry under `Unreleased` in `CHANGELOG.md`.
7. Open a pull request describing the behavior before and after the change.

## Writing guidance

Skill instructions should be concise, imperative, and operational. Avoid generic advice that the model already knows. Detailed methodologies belong in `references/` rather than making `SKILL.md` unnecessarily large.

## Issues

When reporting a recommendation-quality problem, include:

- the original user prompt;
- any clarification answers;
- the problematic recommendation or behavior;
- what you expected instead;
- whether the problem concerns discovery, research quality, ranking, diversity, editions, memory/preferences, or presentation.

Do not include private or sensitive personal information in public issues.
