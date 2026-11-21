# Contributing

## Before you start

Open an issue first for any change in behavior. Describe what the skill does now, what it should do, and why. Typo and wording fixes in the docs can go straight to a pull request.

## Changes to SKILL.md

A pull request that changes `skills/repo-reality/SKILL.md` must meet all of these:

- It includes a test report that the skill produced on a public repository at a pinned commit. Give the repository URL and the full commit hash.
- Any prose it changes passes the hype grep in step 8 of SKILL.md. Every hit must sit inside a quote, a code span, or a proper name.
- SKILL.md stays ASCII-only and under 500 lines. The one exception is the visible symbols in the step 10 summary (the warning sign, arrow, cross, check mark, question mark and middle dot). No invisible characters, such as emoji variation selectors, anywhere.
- It adds no required tools beyond git and ripgrep. Optional tools are fine if the skill still works without them.

## Style

Write plain, direct sentences in active voice. Use no promotional words. Use no em dashes or en dashes.
