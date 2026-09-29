# ocws starter templates

Starter templates for [ocws](https://github.com/c0dn/ocws), which sets up
OpenCode, Claude Code, and Codex CLI workspaces from a templates repository.
`ocws init` clones this repository when you do not pass `--from`.

Full format reference: <https://c0dn.github.io/ocws/templates/>

## What is included

| Profile | Detected by | Base packs | Capability packs |
| --- | --- | --- | --- |
| `webapp` | `package.json`, `vite.config.*`, `next.config.*`, `astro.config.*` | reviewer, commit, writing-tests | Context7 MCP; Playwright MCP (recommended when `playwright.config.*` exists) |
| `general` | fallback | reviewer, commit | Context7 MCP |

Every pack installs for all three harnesses:

| Pack | OpenCode | Claude Code | Codex CLI |
| --- | --- | --- | --- |
| `reviewer` agent | `.opencode/agents/reviewer.md` | `.claude/agents/reviewer.md` | `.codex/agents/reviewer.toml` |
| `commit` command | `.opencode/commands/commit.md` | skill, manual invocation only | skill, explicit invocation only |
| `writing-tests` skill | `.opencode/skills/` | `.claude/skills/` | `.agents/skills/` |
| MCP packs | `opencode.json` | `.mcp.json` | `.codex/config.toml` |

## Try it

```bash
npm i -g @c0dn/ocws
ocws init                     # clones this repository into ~/.config/ocws/templates
cd your-project
ocws                          # interactive wizard
ocws apply -p webapp --harness opencode,claude --cap context7
```

## Make your own

1. Click **Use this template** on GitHub (a private copy is fine).
2. Point ocws at it: `ocws init --force --from git@github.com:you/your-templates.git`.
3. Edit profiles and packs, then check them:

   ```bash
   ocws templates validate --templates .
   ```

4. Push, then run `ocws templates update` on each machine.

## Layout

```text
profiles.json              profiles: detection, config, guide, packs
guides/                    AGENTS.md templates (the first heading becomes the project name)
workspace-configs/         per-harness workspace config merged into each project
scaffolds/                 files created once by profile scaffolds
packs/<kind>/<name>/       pack manifest.json plus its source files
packs/**/harness/          per-harness headers and config fragments
```

`profiles.json` and every `manifest.json` reference a JSON Schema, so editors
with JSON Schema support offer completion and inline errors.
