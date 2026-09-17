# Connecting Hamla to your agent

Hamla runs an MCP server, so an assistant can work your marketing account
directly — and can hand you your real install snippet instead of a
placeholder. Authentication is OAuth: you sign in with your own Hamla account
and the assistant acts as you. **There is no API key to paste.**

Server URL:

```
https://app.hamla.io/mcp
```

Registry name, for clients that search the registry rather than take a URL:
`io.hamla/hamla`

## Claude Code

```bash
claude mcp add --transport http hamla https://app.hamla.io/mcp
```

Add `--scope project` to write it into the repo's `.mcp.json` and share it
with the rest of the team.

## Claude (desktop and web)

Search for Hamla in the Connectors Directory and connect it. No URL needed.

## Cursor

`.cursor/mcp.json`, in the project or at `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "hamla": {
      "url": "https://app.hamla.io/mcp"
    }
  }
}
```

No `auth` block: Hamla's connector signs you in through OAuth in the browser,
so there is no client id or secret to place here.

## Any other MCP client

VS Code, Windsurf, Zed, Goose, ChatGPT and Gemini Enterprise all take the
server URL above. The `.mcp.json` shape Claude Code writes is the same one
most of them read:

```json
{
  "mcpServers": {
    "hamla": {
      "type": "http",
      "url": "https://app.hamla.io/mcp"
    }
  }
}
```

## Then ask for the snippet

```
Put Hamla on this site.
```

With the connector attached, `getInstallSnippet` returns the real script tag
for your business. Without it, an agent has to guess a `businessId` — which is
the failure `POST https://app.hamla.io/api/install` and the rest of these files exist
to remove.
