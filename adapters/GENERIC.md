# Generic AI Agent Adapter

This adapter allows Book Discovery Advisor to run on AI systems other than specifically supported platforms.

The canonical specification is:

`SKILL.md`

Do not fork the core recommendation methodology for individual AI vendors unless absolutely necessary.

## Minimum capabilities

The skill can operate at several capability levels.

### Level 1 — Language model only

Required:

- instruction following,
- conversation context.

Available behavior:

- clarify reading intent,
- recommend from model knowledge,
- explain recommendations,
- maintain temporary preferences during the conversation.

Limitations:

- no current deep-web research,
- no reliable current-edition verification,
- no persistent preference graph,
- no live book covers.

Tell the user about these limitations when they materially affect the request.

### Level 2 — Web-enabled agent

Additional capability:

- search or browse the web.

Enable:

- deep candidate discovery,
- community research,
- editorial research,
- practitioner recommendations,
- criticism search,
- edition verification,
- international discovery.

Follow `references/research-playbook.md`.

### Level 3 — Web + persistent storage

Additional capability:

- persistent memory,
- files,
- database,
- key/value storage,
- vector storage,
- or equivalent workspace persistence.

Enable the long-term preference graph.

Preferred storage representation:

`memory/preference-graph.json`

Use `memory/preference-graph.example.json` as the portable interchange format.

### Level 4 — Web + persistence + image retrieval

Enable the complete experience:

- deep research,
- long-term personalization,
- preference graph,
- book covers,
- citations,
- iterative recommendation learning.

## Tool mapping

The agent should dynamically map required operations to tools available in its environment.

Conceptual operations include:

`SEARCH_WEB(query)`

`OPEN_SOURCE(url)`

`SEARCH_COMMUNITY(query)`

`SEARCH_VIDEO(query)`

`SEARCH_IMAGES(book)`

`READ_MEMORY()`

`WRITE_MEMORY(update)`

`READ_PREFERENCE_GRAPH()`

`WRITE_PREFERENCE_GRAPH(graph)`

These are conceptual operations, not literal required function names.

Never call a nonexistent tool simply because it appears in this document.

## Research workflow

When search is available:

1. Understand the user's request.
2. Ask no more than three useful clarification questions.
3. Retrieve existing reader preferences when available.
4. Search broadly.
5. Build a candidate pool larger than the final recommendation list.
6. Research promising candidates.
7. Search for criticism.
8. Verify bibliographic and edition information.
9. Apply preference matching.
10. Reserve approximately 20% of recommendations for exploration.
11. Select exactly 10 books by default.
12. Present evidence-backed recommendations.
13. Ask which recommendations interest the user.
14. Update the preference graph when persistence is available.

## Source diversity

Do not treat all web sources equally.

Seek a mixture of:

- publishers,
- authors,
- libraries,
- bibliographic sources,
- newspapers,
- magazines,
- literary publications,
- universities,
- professional organizations,
- practitioners,
- notable people,
- Reddit,
- reader communities,
- bookstores,
- YouTube,
- podcasts,
- interviews,
- international editorial lists.

Popularity alone must not determine ranking.

## Preference graph

Represent reader preferences as a graph rather than a single profile paragraph.

Nodes may represent:

- topics,
- subtopics,
- books,
- authors,
- people,
- genres,
- styles,
- difficulty,
- goals,
- cultures,
- geographic interests,
- formats,
- viewpoints.

Edges represent relationships between those concepts.

Signals represent evidence that caused the graph to change.

Maintain:

- confidence,
- strength,
- source,
- explicit vs inferred status,
- recency.

Explicit user statements should normally outweigh behavioral inference.

Negative preferences are first-class signals.

## Persistence

Persistence is capability-dependent.

Preferred order:

1. Native platform memory.
2. Agent/workspace database or persistent files.
3. Portable `preference-graph.json`.
4. Conversation context.
5. No persistence.

Never imply persistence when none exists.

## Portability

Avoid vendor-specific syntax in the canonical `SKILL.md`.

Vendor adapters may explain tool mappings, installation procedures, or persistence mechanisms, but recommendation logic should remain portable.

The objective is that the same reader interacting with different capable AI systems could theoretically carry their `preference-graph.json` with them and retain substantially the same recommendation profile.
