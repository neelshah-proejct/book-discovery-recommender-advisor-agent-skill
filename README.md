# Book Discovery Advisor

A deep-research ChatGPT Skill for personalized book discovery.

Instead of starting with a familiar bestseller list, **Book Discovery Advisor** clarifies the reader's goal, builds a broad candidate pool from diverse sources, investigates the strongest candidates, searches for criticism as well as praise, and recommends a deliberately diversified set of books.

Its default recommendation model is simple:

> **80% preference match + 20% exploration**

The goal is to make recommendations increasingly personal without turning personalization into a filter bubble.

## What it does

- Asks **no more than 3 clarification questions**, and asks none when the request is already clear.
- Researches before ranking instead of choosing familiar books first and looking for supporting evidence afterward.
- Searches across multiple source families, including community discussions, Reddit, YouTube/interviews/podcasts, publishers, booksellers, editorial lists, universities/institutions, experts, practitioners, and notable people's reading recommendations when relevant.
- Uses international discovery across major Western markets plus India, China, Japan, and South Korea when it improves the search.
- Builds a candidate pool before selecting the final recommendations.
- Returns **10 books by default**: 8 aligned with the reader's preferences and 2 exploration picks.
- Actively searches for substantive criticism and contrarian views.
- Investigates authors, original publication dates, current meaningful editions, edition changes, contents, reader reception, expert reception, longevity, and whether material has become dated.
- Distinguishes a substantive new edition from a reprint, cover change, or format change.
- Shows book-cover imagery when reliable covers and the active interface support it.
- Gives a compact view of all 10 books, followed by deeper research on the top 3 by default.
- Supports follow-up comparison, reading paths, and deeper investigation of selected books.
- Uses available ChatGPT memory/context to build a conceptual, confidence-weighted **reader preference graph**.

## Example

A request such as:

> Recommend books about investing.

should not immediately produce ten generic investing classics. The skill may first clarify whether the reader wants general investing, funds, individual stocks, long-term investing, famous investors, biographies, or another branch, along with experience level when needed.

It then researches a broader candidate pool and may return a mix such as foundational investing, practical portfolio construction, investor biographies, market history, behavioral finance, and two carefully connected exploration picks.

The exploration picks are not random noise. Someone interested in investing might receive an unexpected but defensible book about probability, decision-making, accounting, economic history, psychology, or business history.

## Research philosophy

The skill follows this workflow:

**Understand -> Discover -> Investigate -> Diversify -> Rank -> Present -> Learn**

### Discover before deciding

The skill should not begin with ten books it already knows and then search for evidence that confirms those choices. It first builds a candidate pool—normally 30–50 books for a broad topic and at least 20 for a narrow topic—and then investigates the strongest candidates.

### Diversify evidence

Popularity is not treated as quality. The research process separates signals such as:

- relevance to the reader's actual goal;
- reader/community reception;
- expert or practitioner reputation;
- editorial/critical reception;
- influence and longevity;
- currency or timelessness;
- originality and redundancy;
- reading ROI.

Domain expertise matters. A respected investor recommending an investing book is stronger domain evidence than an unrelated celebrity recommendation.

### Search for criticism

For serious candidates, the skill deliberately looks for weaknesses, dated material, methodological problems, overrated claims, and substantive negative reader discussions. Recommendations should reflect both advocacy and criticism.

## The 80/20 discovery model

The default ten-book result contains:

- **8 Preference Matches** — books strongly aligned with the current request and known reader preferences.
- **2 Exploration Picks** — books connected to the underlying goal but intentionally outside the reader's normal pattern.

Exploration can introduce adjacent disciplines, opposing viewpoints, unfamiliar authors or cultures, classics, biographies, history, psychology, probability, philosophy, or other useful intellectual branches.

This rule exists to prevent a preference model from becoming a self-reinforcing recommendation bubble.

## Reader preference graph

The skill models reading preferences as a conceptual graph rather than a flat list of favorite genres.

For example:

```text
Investing
  -> Value investing
      -> Buffett
          -> Berkshire Hathaway
              -> Business biographies

Reading style
  -> prefers practical material
  -> likes case studies
  -> avoids repetitive self-help
```

Signals are classified as:

1. **Explicit** — directly stated by the reader; highest confidence.
2. **Behavioral** — selections, rejections, ratings, repeated engagement; medium confidence.
3. **Inferred** — tentative patterns inferred from limited behavior; low confidence.
4. **Exploration reaction** — response to wildcard recommendations; useful for discovering new branches.

The model keeps positive and negative preferences, confidence, recency, and contradictory evidence. Weak inferred interests decay faster than durable explicit preferences.

### Memory and privacy boundary

The Skill does **not** create its own independent persistent database.

When ChatGPT memory/context is available and appropriate, the skill can use durable reading-related preferences from that context and can treat new user feedback as potential preference signals. When persistence is unavailable, it operates from the current conversation.

It should never claim that a permanent graph exists merely because this Skill is installed, and it should not store speculative or sensitive conclusions as reading preferences.

See [`references/preference-graph.md`](references/preference-graph.md) for the complete model.

## Recommendation output

The default response begins with a concise comparison of all 10 recommendations. Each book can include, where evidence is available:

- title and author;
- original publication year;
- current meaningful edition/year;
- reader level;
- timeless/current/partially dated status;
- why the book surfaced;
- why it fits the reader;
- concise summary;
- quick content outline;
- principal limitation or criticism.

The top 3 receive deeper treatment by default, including relevant author background, first vs. current edition, meaningful edition changes, learning outcomes, verified chapter names when available, strongest positive case, typical reader view, strongest criticism, who should read/skip it, and reading commitment/ROI when reasonably estimable.

## Example prompts

```text
Recommend books about investing.
```

```text
I understand index funds already. I want to learn how professional investors value individual companies, but I don't want a textbook unless it is genuinely worth the effort.
```

```text
What books has Warren Buffett actually recommended about investing? Separate direct recommendations from books merely associated with him.
```

```text
I liked The Psychology of Money but want something more technical. Give me books that move me toward valuation and market history.
```

```text
Recommend books about artificial intelligence, but make two of the ten books come from fields I probably would not search myself.
```

```text
Compare books 2, 5, and 8 from your previous recommendations and tell me which one I should read first.
```

More scenarios are in [`examples/`](examples/).

## Repository structure

```text
book-discovery-advisor/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── preference-graph.md
│   └── research-playbook.md
├── examples/
│   ├── investing.md
│   ├── history.md
│   └── technology.md
├── dist/
│   └── skill.zip
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

## Installation

The installable archive is available at [`dist/skill.zip`](dist/skill.zip).

If your ChatGPT environment supports personal Skills, upload the packaged Skill through the Skills interface. The source directory itself contains the same Skill in readable/editable form.

You can also inspect `SKILL.md` before installation to understand exactly what behavior the Skill instructs.

## Development

The core behavior lives in [`SKILL.md`](SKILL.md). Detailed reusable guidance is kept in `references/` so the main Skill remains compact.

When changing the recommendation methodology:

1. Keep the core workflow concise.
2. Put detailed research or preference-model rules in `references/`.
3. Do not add unsupported external services or claim persistent storage the Skill does not possess.
4. Validate the Skill before publishing a new `dist/skill.zip`.
5. Update `CHANGELOG.md` for meaningful releases.

## Design principles

- Research first, rank second.
- Ask fewer, better questions.
- Suitability matters more than popularity.
- Criticism is part of recommendation quality.
- Personalization should improve discovery, not eliminate surprise.
- Community comments are useful reader evidence, not authoritative bibliographic evidence.
- Primary sources are preferred for editions and direct endorsements.
- Never invent chapters, endorsements, editions, quotes, or rankings.
- Be explicit about uncertainty.

## Contributing

Contributions are welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md).

Particularly useful contributions include better research-source strategies, international discovery patterns, recommendation-quality tests, preference-graph improvements, and examples that reveal failure modes or recommendation bias.

## License

Released under the [MIT License](LICENSE).

## Skills created and managed by Neel Shah, more detials at neelshah18.com or dishuu.com 
