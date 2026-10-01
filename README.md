# claude-collection

One [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces) for every plugin, skill, and agent I publish on GitHub. Nothing is copied here: each entry points at its source repo, so installs always pull from the original.

## Add the marketplace

```bash
claude plugin marketplace add aaddrick/claude-collection
```

Or inside Claude Code: `/plugin marketplace add aaddrick/claude-collection`

Then install whatever you want:

```bash
claude plugin install <plugin>@claude-collection
```

## Plugins

| Plugin | What it gives you | Source |
|---|---|---|
| `attention-control` | Output style for a reader with ADHD: action first, one meaning per word, state restated every turn. | [attention-control](https://github.com/aaddrick/attention-control) |
| `building-with-typesafe-jev` | Skill for building with TypeSafe AI's Jev: typed decisions, confidence routing, community prior art. | [building-with-typesafe-jev](https://github.com/aaddrick/building-with-typesafe-jev) |
| `directing-agent-teams` | Skill + nine agents for running a large build with a Director-led team of subagents. | [directing-agent-teams](https://github.com/aaddrick/directing-agent-teams) |
| `ticketmill` | Batch-process GitHub issues end-to-end into human-reviewed batch PRs. | [ticketmill](https://github.com/aaddrick/ticketmill) |
| `ptt` | Push-to-talk voice input (Ctrl+Space) with local Whisper transcription. | [claude-ptt](https://github.com/aaddrick/claude-ptt) |
| `gh-cli-search` | Skills for `gh search` code/commits/issues/PRs/repos with correct syntax and quoting. | [gh-cli-search](https://github.com/aaddrick/gh-cli-search) |
| `contrarian` | Devil's advocate agent for pre-mortems, architecture reviews and decision validation. | [contrarian](https://github.com/aaddrick/contrarian) |
| `implementation-pipeline` | The skills and agents from my multi-agent implementation pipeline (planning, TDD, debugging, issue/PR handling, reviewers). | [claude-pipeline](https://github.com/aaddrick/claude-pipeline) |
| `writing-release-notes` | Skill for store and GitHub release notes that don't read like a changelog. | [dotfiles-chezmoi](https://github.com/aaddrick/dotfiles-chezmoi) |
| `yaml-lsp` | YAML language server. Needs `npm install -g yaml-language-server`. | [claude-code-lsps](https://github.com/aaddrick/claude-code-lsps) |
| `bash-lsp` | Bash language server. Needs `npm install -g bash-language-server`. | [claude-code-lsps](https://github.com/aaddrick/claude-code-lsps) |

### Notes

- `contrarian`, `implementation-pipeline` and `writing-release-notes` come from repos that aren't packaged as plugins. Their entries here use `strict: false` and list the skill and agent paths directly, so the source repos don't need any changes.
- `implementation-pipeline` installs only the skills and agents from [claude-pipeline](https://github.com/aaddrick/claude-pipeline). Its hooks and orchestration scripts are project-specific; copy the `.claude/` folder from that repo if you want the full pipeline. Several of its skills are adapted from [obra/superpowers](https://github.com/obra/superpowers) (MIT); see that repo's NOTICE.
- The LSP plugins need `"ENABLE_LSP_TOOL": "1"` in `~/.claude/settings.json`. See [claude-code-lsps](https://github.com/aaddrick/claude-code-lsps) for setup.

## Adding a plugin

Add an entry to [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) with a `github` source, then check it:

```bash
claude plugin validate .
```

Plugin names can't start with `claude-` (that prefix is reserved), which is why claude-pipeline is listed as `implementation-pipeline`.
