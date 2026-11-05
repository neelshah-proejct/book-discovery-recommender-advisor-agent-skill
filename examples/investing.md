# Investing recommendation examples

## Broad request

**User**

> Recommend books about investing.

**Expected behavior**

Ask only the questions that materially change the search, with a maximum of three. A strong clarification might distinguish general investing, funds/indexing, individual-stock analysis, long-term investing, famous investors/biographies, or market history. Ask about reader level if unknown and important.

Do not immediately return the standard investing bestseller list.

Build a broad candidate pool and investigate expert/practitioner recommendations, reader communities, critical views, editions, and overlap between books. Return eight strong preference matches and two connected exploration picks.

## Advanced reader

**User**

> I already understand ETFs and index investing. I want to learn how to value individual companies. I prefer practical books with real company examples and I am comfortable with accounting.

**Expected behavior**

Do not ask beginner-level questions already answered by the prompt. Prioritize valuation, financial-statement interpretation, case studies, capital allocation, and investor decision-making. Avoid filling the list with introductory personal-finance books.

Potential exploration directions include probability, business history, competitive strategy, or decision science.

## Notable-person attribution

**User**

> Give me books Warren Buffett has recommended about investing.

**Expected behavior**

Verify attribution. Prefer direct sources such as shareholder communications, interviews, letters, or strong reporting. Distinguish:

- directly recommended;
- praised or discussed positively;
- mentioned without a clear recommendation;
- merely associated with Buffett by secondary listicles.

Do not convert weak association into a direct endorsement.
