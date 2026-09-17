# Hamla for agents

Everything an AI coding agent needs to add Hamla to a project, in the formats
different agents install.

| File | For |
| --- | --- |
| [`AGENTS.md`](./AGENTS.md) | The procedure itself. The `AGENTS.md` convention, read by most coding agents |
| [`SKILL.md`](./SKILL.md) | Claude Code and the Claude Agent SDK |
| [`.cursor/rules/hamla.mdc`](./.cursor/rules/hamla.mdc) | Cursor |
| [`mcp.md`](./mcp.md) | Connecting Hamla's own tools to your assistant |

All four carry the same procedure. The first three are the same document with
different frontmatter — a skill, a Cursor rule and an `AGENTS.md` differ in how
they are installed, not in what they say.

## Install

Claude Code, into a project:

```bash
mkdir -p .claude/skills/hamla-install
curl -fsSL https://raw.githubusercontent.com/usehamla/agent-packages/main/SKILL.md \
  -o .claude/skills/hamla-install/SKILL.md
```

Cursor:

```bash
mkdir -p .cursor/rules
curl -fsSL https://raw.githubusercontent.com/usehamla/agent-packages/main/.cursor/rules/hamla.mdc \
  -o .cursor/rules/hamla.mdc
```

Anything else: point it at https://hamla.io/AGENTS.md, which is the same file served
over HTTP and needs no clone.

## One name, three spellings

`usehamla` on GitHub, `@gethamla` on npm, `hamla.io` on the web.

## Generated — do not edit here

Every file in this repo is rendered from
`apps/landing/src/lib/content/` in the Hamla monorepo, where the event
vocabulary and the endpoints come from the registries the product actually
runs on. Nothing here is written by hand, and nothing here is pushed by hand:
a merge to the monorepo's `main` that changes these files publishes them.

So editing a file here is editing a build artifact. The next sync overwrites
it, and in the monorepo `pnpm agents:check` fails CI in the meantime.

Fix it at the source instead — `pnpm agents:generate` regenerates the lot.
