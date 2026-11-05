# Claude Adapter

Use the repository's root `SKILL.md` as the canonical Book Discovery Advisor instructions.

## Setup

For Claude environments that support skills or project instructions:

1. Load `SKILL.md` as the primary instruction file.
2. Make the `references/` directory available to the agent.
3. Use `references/research-playbook.md` when performing book research.
4. Use `references/preference-graph.md` when updating reader preferences.
5. If persistent project files are available, maintain the preference graph using the schema demonstrated in:
   `memory/preference-graph.example.json`.

## Research

Map the research workflow in `SKILL.md` to Claude's available web-search, browsing, retrieval, or connector capabilities.

Do not assume a specific search tool exists.

When web access is available:

- Search before selecting the final books.
- Build a broad candidate pool first.
- Research multiple independent source types.
- Search Reddit and community discussions when accessible.
- Search YouTube, podcasts, interviews, and transcripts when accessible.
- Search editorial and international sources.
- Search for criticism as well as praise.
- Verify publication and edition information from reliable sources.

When web access is unavailable, clearly tell the user that recommendations are based on available model knowledge and cannot satisfy the full deep-research workflow.

## Memory and preference graph

Use Claude's available persistent memory, project knowledge, files, or workspace storage when supported.

Preference persistence priority:

1. Native persistent user memory, if available.
2. Persistent project/workspace preference graph.
3. Current conversation context.
4. No persistence.

Never claim that a preference was permanently remembered unless the current Claude environment actually supports persistence.

If file persistence is available, maintain:

`memory/preference-graph.json`

Use `memory/preference-graph.example.json` as the starting schema.

Preserve:

- explicit preferences,
- inferred preferences,
- rejected recommendations,
- liked books,
- disliked books,
- authors,
- topics,
- difficulty preferences,
- style preferences,
- exploration reactions,
- confidence,
- recency.

Explicit user statements should normally have greater weight than inferred behavior.

## Images

If Claude can retrieve or display book-cover images, include covers with recommendations.

If it cannot, continue with the recommendation workflow without fabricating image URLs.

## Citations

Use Claude's native citation or source-linking mechanism when available.

Every important factual claim discovered during research should remain traceable to its source.

Do not invent citations.

## Portability

Do not alter the recommendation methodology merely because the skill is running in Claude.

The canonical behavior remains defined by `SKILL.md`.

Platform-specific capabilities should change execution mechanics, not the underlying recommendation philosophy.
