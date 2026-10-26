# Bytewell for Claude Code

A Claude Code plugin: Bytewell's MCP server plus a skill that tells the agent how to clean a Mac carefully (preview
first, Trash only, undo). It needs the Bytewell app in `/Applications` or `~/Applications` ([bytewell.app](https://bytewell.app), free).

```
/plugin marketplace add callmecelebi/bytewell-claude-code
/plugin install bytewell@bytewell
```

Then ask Claude things like *"what's filling my disk?"* or *"clean my Xcode and simulator clutter"*.

Already connected Bytewell from the app's *AI Agents* page? Then the MCP tools are there already; the plugin adds the
skill. Remove one of the two connections if you see the tools twice.

## Updates

Starting with 1.2.2, `bytewell mcp` keeps the client's stdio connection open and switches to the installed
helper when the app is updated. Existing previews and approval requests finish in their original worker;
forwarded tool calls are never replayed. A successful switch sends the standard tools-list change notification.
The first tool result from a new worker includes its current developer guide, and the read-only `agent_guide`
tool retrieves that same guide on demand. A new scan is still needed when current disk findings are requested.

This skill is a small loader for the guide shipped in the installed app, so future tool/safety updates need no
repeated skill edits. Plugin metadata and connection changes remain separate releases through the public plugin
repository. Changes in this working copy are unpublished.

Connections already running 1.2.1 or earlier remain intact; the client's next normal MCP connection starts the
installed supervisor automatically. No separate manual reconnect or configuration task is required to keep using
Bytewell. The already-open older connection continues with its original code until that normal reconnect; the new
app cannot upgrade it in place. Do not terminate old helpers or restart Claude Code to force adoption.
Older full guides copied into AGENTS.md or CLAUDE.md are not rewritten. Replace only the Bytewell section once
with `/Applications/Bytewell.app/Contents/Helpers/bytewell agent-guide --bootstrap` (or use the app's Copy
instructions button); that stable loader reads the current guide on future tasks. Keep the app at its configured
path. No assistant process or project instructions are changed automatically.

## This folder

Published as the public marketplace repository github.com/callmecelebi/bytewell-claude-code (this repo is private); copy changes there:

| Path | What it is |
|---|---|
| `.claude-plugin/marketplace.json` | The marketplace (one plugin) |
| `plugins/bytewell/.claude-plugin/plugin.json` | Plugin metadata |
| `plugins/bytewell/.mcp.json` | Starts `bin/bytewell-mcp`, which runs `Bytewell.app/Contents/Helpers/bytewell mcp` from `/Applications` or `~/Applications` |
| `plugins/bytewell/bin/bytewell-mcp` | Finds the installed app (keep it executable when copying) |
| `plugins/bytewell/skills/free-up-disk-space/SKILL.md` | How the agent should use the tools |

Test locally before publishing: `claude --plugin-dir integrations/claude-code/plugins/bytewell`.

## Where else to list it

| Directory | How |
|---|---|
| Claude Code plugin directory (Anthropic) | Submission form: https://clau.de/plugin-directory-submission (needs the public repo) |
| mcp.so | "Submit" on the site, with the public repo URL |
| Glama MCP directory | "Add server" with the public repo URL |
| awesome-mcp-servers lists | Pull request adding one line under *File systems* or *Developer tools* |

The official MCP Registry and Smithery list servers installable from a package (npm, PyPI, Docker) or hosted over
HTTP. Bytewell's server ships inside a signed Mac app, so it doesn't fit them as is.
