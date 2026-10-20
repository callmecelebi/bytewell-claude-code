# Bytewell for Claude Code

A Claude Code plugin for [Bytewell](https://bytewell.app), the Mac disk analyzer for developers and AI users. It adds
Bytewell's MCP server and a skill that tells Claude how to clean your Mac carefully: show what it found, preview,
wait for your OK, move to the Trash (never delete), and undo on request.

## Install

1. Install Bytewell in `/Applications`: [bytewell.app](https://bytewell.app) (free) or
   `brew install --cask callmecelebi/tap/bytewell`.
2. In Claude Code:

```
/plugin marketplace add callmecelebi/bytewell-claude-code
/plugin install bytewell@bytewell
```

Then ask things like *"what's filling my disk?"*, *"clean my Xcode and simulator clutter"* or *"which local AI models
haven't I used in months?"*.

Already connected Bytewell from the app's *AI Agents* page? The MCP tools are there already and the plugin adds the
skill. If you see the tools twice, remove one of the two connections.

## What Claude can and can't do

- Read the disk map Bytewell made: free space, biggest folders, cleanup suggestions, local AI models, code projects,
  Docker, duplicates, System Data.
- Move suggested items to the Trash, only after showing you a preview and getting your confirmation. Undo puts them back.
- It can't delete permanently, touch personal data (keychains, mail, messages, SSH keys, iCloud, Photos) or remove
  anything you told Bytewell to keep.

## Contents

| Path | What it is |
|---|---|
| `.claude-plugin/marketplace.json` | The marketplace (one plugin) |
| `plugins/bytewell/.claude-plugin/plugin.json` | Plugin metadata |
| `plugins/bytewell/.mcp.json` | Starts `/Applications/Bytewell.app/Contents/Helpers/bytewell mcp` |
| `plugins/bytewell/skills/free-up-disk-space/SKILL.md` | How Claude should use the tools |

Questions: ismail@axleno.com
