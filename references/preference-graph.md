# Reader Preference Graph

Use this model as a conceptual long-term reader profile. Populate it only from available memory/context and current user feedback.

## Node families

Track useful reading signals such as:
- Topics: investing, history, AI, psychology, fiction, etc.
- Subtopics: value investing, index funds, market history, biographies, etc.
- Authors/thinkers.
- Books and series.
- Goals: practical implementation, conceptual mastery, entertainment, worldview expansion.
- Style: narrative, textbook, case-study, data-heavy, concise, philosophical.
- Difficulty: beginner, intermediate, advanced.
- Evidence preference: academic, practitioner, journalistic, anecdotal.
- Time preference: classic/timeless vs current.
- Cultural/geographic interests.
- Format/length signals when explicitly relevant.
- Positive and negative preferences.

Represent relationships conceptually, for example:
`Investing -> Value investing -> Buffett -> Berkshire -> Business biography`
`Prefers -> practical -> case studies`
`Avoids -> repetitive -> generic self-help`

## Signal classes

Treat signals differently:

1. **Explicit** — user directly states a preference. Highest confidence.
2. **Behavioral** — user selects, rejects, asks to expand, finishes, rates or repeatedly engages with a type. Medium confidence.
3. **Inferred** — pattern inferred from limited behavior. Low confidence; never present as a fact.
4. **Exploration reaction** — reaction to a wildcard. Important for discovering new branches but initially medium/low confidence.

Track polarity (positive/negative), confidence and recency conceptually.

## Update rules

- Strengthen an explicit preference immediately.
- Strengthen behavioral preferences gradually after repeated evidence.
- Do not overfit to one click/selection.
- Record rejection reasons when supplied; a rejected book may indicate topic, style, difficulty, length, author or redundancy rather than broad dislike.
- Treat repeated rejection as a negative edge only when the reason is reasonably clear.
- Keep contradictory signals instead of erasing history; favor stronger and more recent evidence.
- Apply time decay: weak inferred interests decay fastest, behavioral signals moderately, explicit stable preferences slowest.
- Do not decay explicit dislikes quickly when the user gives a durable reason.

## Memory storage behavior

When persistent ChatGPT memory is available, store only durable, useful reading preferences and meaningful changes that can improve future recommendations. Do not store every recommendation or transient search.

Good persistent examples:
- prefers advanced investing books over beginner introductions;
- likes business biographies and historical case studies;
- dislikes repetitive motivational/self-help books;
- wants 20% exploratory recommendations.

Avoid storing:
- one-off curiosity with no evidence of durable interest;
- speculative psychological/personality conclusions;
- sensitive attributes unrelated to reading;
- entire web research results.

The skill has no independent database. Never claim that this reference file itself was updated at runtime or that a permanent graph exists unless the platform actually provides persistence. Use available memory/context as the persistence layer and reconstruct the conceptual graph from it.

## Recommendation use

Use the graph to influence approximately 80% of a default recommendation set. Reserve approximately 20% for exploration so the graph does not become a filter bubble.

When choosing between equally strong books, prefer candidates that either:
- reinforce a high-confidence goal with low redundancy, or
- connect two known interests in a novel way.

Do not endlessly recommend books similar to books already consumed. Prefer progression: foundation -> deeper treatment -> contrasting view -> adjacent field.
