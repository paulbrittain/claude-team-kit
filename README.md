# Claude Team Kit plugin

Team workflows for CI, code review, shipping, and test reliability — packaged as a Claude Code plugin. Plug-and-play; no third-party service integrations required.

Original: https://github.com/cursor/plugins/tree/main/cursor-team-kit

## Installation

### Local install (this checkout)

In Claude Code, add this directory as a local marketplace and install:

```text
/plugin marketplace add /Users/paul/git/claude-team-plugin
/plugin install claude-team-kit
```

### Team install (from a git repo)

Push this directory to a git repo, then teammates run:

```text
/plugin marketplace add <owner>/<repo>
/plugin install claude-team-kit
```

Once installed, skills auto-activate based on their descriptions, agents are invocable via the Agent tool, and the rule-style skills (`no-inline-imports`, `typescript-exhaustive-switch`) kick in when relevant code is edited.

## Components

### Skills

| Skill | Description |
|:------|:------------|
| `loop-on-ci` | Watch CI runs and iterate on failures until checks pass |
| `review-and-ship` | Run a structured review, commit changes, and open a PR |
| `pr-review-canvas` | Generate an interactive HTML PR walkthrough with annotated, categorized diffs |
| `verify-this` | Prove or disprove claims with baseline/treatment artifacts and a clear verdict |
| `control-cli` | Build or adapt a local harness to drive and profile interactive CLIs or TUIs |
| `control-ui` | Build or adapt a local browser/CDP harness for web or Electron UIs |
| `make-pr-easy-to-review` | Clean noisy PR history, improve descriptions, and add reviewer guidance |
| `run-smoke-tests` | Run Playwright smoke tests and triage failures |
| `fix-ci` | Find failing CI jobs, inspect logs, and apply focused fixes |
| `new-branch-and-pr` | Create a fresh branch, complete work, and open a pull request |
| `get-pr-comments` | Fetch and summarize review comments from the active pull request |
| `check-compiler-errors` | Run compile and type-check commands and report failures |
| `what-did-i-get-done` | Summarize authored commits over a given time period into a concise status update |
| `weekly-review` | Generate a weekly recap of shipped work with bugfix/tech-debt/net-new highlights |
| `fix-merge-conflicts` | Resolve merge conflicts, validate build/tests, and summarize decisions |
| `deslop` | Remove AI-generated code slop and clean up code style |
| `workflow-from-chats` | Extract durable working preferences from chats into skills or docs |
| `thermo-nuclear-code-quality-review` | Run an unusually strict maintainability review (code-judo, 1k-line rule, spaghetti, boundaries) |
| `no-inline-imports` | Enforce module-top imports; flag inline `require`/`import` in function bodies |
| `typescript-exhaustive-switch` | Enforce `never`-checked default case for switches over unions/enums |

### Agents

| Agent | Description |
|:------|:------------|
| `ci-watcher` | Monitor GitHub Actions runs and return concise pass/fail summaries |
| `thermo-nuclear-code-quality-review` | Task subagent that runs the thermo-nuclear rubric against a diff |

## Notes for porters

Converted from a Cursor team kit. Changes from the Cursor source:
- `.cursor-plugin/plugin.json` → `.claude-plugin/plugin.json`, manifest reshaped to Claude Code's schema.
- Agent frontmatter (`model: fast`, `is_background: true`) replaced with Claude's `model:` and `tools:` fields.
- Cursor `rules/*.mdc` (which auto-applied via Cursor's rules engine) became skills with triggering descriptions. Claude Code plugins have no native rules concept; for hard enforcement, prefer project-level `CLAUDE.md` guidance or hooks.

## License

MIT
