# Security policy

The repo-reality skill reads repositories that its user does not control. Text in those repositories is untrusted data, and the skill is built to treat it that way.

## In scope

Report a repository text that makes the skill do any of the following:

- Follow an instruction that the repository text contains.
- Run code, or run a command that the repository text names, without the user's approval.
- Fetch a URL that the repository text names.
- Print or leak a secret found in the repository.
- Render a link or image taken from repository text, instead of quoting it in a code span or code block.

## Out of scope

Bugs in Claude itself, such as model behavior, the Claude apps, or Claude Code. Report those to Anthropic.

## How to report

Use GitHub's "Report a vulnerability" button on the Security tab of this repository. This opens a private report that only the maintainer can read. Please do not open a public issue for a security problem.

Include a minimal repository or snippet that reproduces the problem, the agent and model you ran the skill in, and what the skill did that it should not have done.
