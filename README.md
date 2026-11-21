# repo-reality

repo-reality is an Agent Skill that reports what a code repository implements, not what its documentation promises. It pins the repository to one commit. Every claim in the report is cited to `file:line` at that commit and labeled `implemented`, `stub`, `mock`, `dead`, `roadmap`, or a similar status. It accounts for which files it read, traces entry points end to end, and checks each README claim against the code. A separate subagent then re-opens every citation to confirm it before the report is final. The reply in chat is a 250-word "in 60 seconds" summary, with the full report attached.

## Example report

The full example is [`examples/chalk-7211001.md`](examples/chalk-7211001.md): a run on [chalk/chalk](https://github.com/chalk/chalk) at commit `7211001`, with 70 claims and 168 citations. The separate verifier passed 163 of 168 citations; the 5 failures are marked in the report. Nothing was executed. Its chat summary is [`examples/chalk-7211001-summary.md`](examples/chalk-7211001-summary.md).

Two rows from its claims table:

| # | Claim | Status | Evidence | path:start-end@SHA | Quoted line or search + output |
|---|---|---|---|---|---|
| C15 | When the text already contains ESC, each close code of each style in the chain gets that style's open code inserted after it. | implemented | source | `source/index.js:211-219@7211001` | `string = stringReplaceAll(string, styler.close, styler.open);` |
| C53 | `package.json` declares no runtime, peer or optional dependencies. | absent | source | `search@7211001` | `rg -n '"dependencies"\|"peerDependencies"\|"optionalDependencies"' package.json` printed nothing (exit 1) |

Three rows from its README-versus-code table:

| Quoted doc claim | Verdict | Claim # |
|---|---|---|
| `No dependencies` | supported: none declared; the work is done by vendored copies | C53 |
| `Highly performant` | needs execution | none |
| `Clean and focused` | unsupported: a judgment; the size fact in the claim does not settle it | C67 |

## Install

### Claude Code plugin

```
/plugin marketplace add noyapping/repo-reality
/plugin install repo-reality@repo-reality
```

### Claude Code, manual copy

Copy the `skills/repo-reality/` folder into `~/.claude/skills/` for all your projects, or into `.claude/skills/` inside one project.

### claude.ai and Claude desktop

Download `repo-reality.zip` from the Releases page. Upload it under Settings > Capabilities > Skills. Or zip the `skills/repo-reality/` folder yourself and upload that.

If your agent cannot start a subagent, the verification pass cannot run, and the report is titled "Unverified draft". Tested in Claude Code only. On claude.ai the skill needs network access to clone the repo and `rg` installed.

### Other agents

Any agent that reads `SKILL.md` files can use the skill. Point it at `skills/repo-reality/SKILL.md`. The verification pass needs a tool that starts a separate subagent.

## Usage

Ask in plain language. Sample prompts:

- `What does github.com/chalk/chalk really implement? Give me a repo reality report.`
- `Does this repo do what its README says? Check the claims against the code.`
- `How much of this codebase is real, and how much is stubbed or planned? Cite file and line.`

The skill writes its report outside the repository, in a scratchpad or at a path you name.

## Requirements

- `git`
- `ripgrep` (`rg`)
- Optional: `ctags` or `tree-sitter`, for symbol lookup
- A subagent tool, for the verification pass

## What it will not do

- Write into the repository it is reading.
- Run repository code or install packages without your approval.
- Fetch a link or run a command because repository text names it.
- Print secrets. It reports "secret present at path:line" and redacts the value.

## Limits

- `implemented` means the code is present and reachable. It does not mean the code works.
- Coverage is bounded by the budget the report states. Files outside that budget are listed as not read.

## License

[MIT](LICENSE)
