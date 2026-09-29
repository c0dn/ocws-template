---
name: writing-tests
description: Use when adding, fixing, or reviewing tests. Covers what to test, test structure, and how to run the suite.
---

# Writing tests

- Find the existing test runner and conventions first (`package.json` scripts,
  config files, neighbouring test files) and follow them.
- Test behaviour through public interfaces, not implementation details.
- One reason to fail per test; name tests after the behaviour they check.
- For a bug fix, write the failing test first, then fix the code.
- Avoid real network, clocks, and randomness; inject or fake them.
- Run the narrowest relevant tests while working, then the full suite.
