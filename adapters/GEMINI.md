# Gemini Adapter

Use the repository's root `SKILL.md` as the canonical Book Discovery Advisor instructions.

## Setup

For Gemini environments that support custom instructions, Gems, agent workflows, project files, or similar functionality:

1. Load `SKILL.md` as the primary behavioral specification.
2. Make `references/` available when supported.
3. Consult `references/research-playbook.md` for deep book discovery.
4. Consult `references/preference-graph.md` for personalization.
5. Use `memory/preference-graph.example.json` when persistent file or workspace storage is available.

## Research

Map the research requirements from `SKILL.md` onto Gemini's available search, grounding, browsing, YouTube, retrieval, and other supported tools.

When web/search capabilities are available:

- Search broadly before ranking books.
- Build the candidate pool from multiple independent sources.
- Use Google/search results where appropriate.
- Use YouTube videos, interviews, podcasts, descriptions, transcripts, or discussions when accessible.
- Include community discussions such as Reddit where accessible.
- Include major editorial publications and international sources.
- Search practitioner and notable-person reading recommendations.
- Search specifically for criticism and opposing assessments.
- Verify publication dates, editions, authorship, and chapter information.

Do not choose ten books from model memory first and then search only for evidence supporting those choices.

## Memory and preference graph

Use available Gemini persistent memory or personalization features when the environment exposes them to the agent.

Persistence priority:

1. Native persistent user memory or personalization.
2. Persistent project/workspace/file storage.
3. Current conversation context.
4. No persistence.

If persistent file storage is available, maintain:

`memory/preference-graph.json`

Initialize it from:

`memory/preference-graph.example.json`

Track preference relationships rather than maintaining only a flat list.

Examples:

`Investing -> Value Investing -> Warren Buffett`

`History -> Economic History -> Financial Crises`

`Practical > Theoretical`

`Intermediate > Beginner`

Record both positive and negative signals.

Keep explicit preferences distinct from inferred preferences and attach confidence to inferred signals.

Apply recency and time decay where appropriate.

Never tell the user that a preference is permanently stored unless the current Gemini environment actually provides persistent storage.

## Google and YouTube ecosystem

Gemini may have particularly useful access to Google and YouTube information depending on the environment.

Use those capabilities when available, but do not allow Google or YouTube sources to dominate the recommendation pool.

Maintain source diversity.

A highly viewed YouTube recommendation is evidence of popularity, not automatically evidence of book quality.

## Images

Use supported image/search functionality to show book covers when available.

Do not invent cover URLs.

## Citations

Use Gemini's available grounding and citation features.

Distinguish sourced factual information from analytical judgments produced by the agent.

## Portability

The root `SKILL.md` remains authoritative.

This adapter only explains how to map Gemini capabilities to the canonical workflow.
