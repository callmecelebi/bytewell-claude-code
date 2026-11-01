# Bytewell

Find what fills your Mac and get the space back from Claude Code: Xcode DerivedData and simulators, node_modules and
package caches, Docker disks, local AI models (including the same weights saved twice), old agent sessions and
worktrees. Nothing is deleted permanently: everything goes to the Trash with Undo, and anything risky waits for your
click in the Bytewell app.

## Requirements

The Bytewell app for macOS 15 or later, in `/Applications` or `~/Applications`. It's a free download at
[bytewell.app](https://bytewell.app).

Free: disk status, scans, cleanup suggestions, biggest folders, large files, disk health, moving to the Trash and
Undo. Bytewell Pro, a one-time purchase with a 14-day free trial, adds AI models, developer projects, duplicates,
System Data, Docker, disk history, apps and uninstalls, and background items. A Pro tool called without Pro answers
with what it needs and which tools still work.

```
/plugin install bytewell --marketplace callmecelebi/bytewell-claude-code
```

## What the plugin contains and runs

- `.mcp.json` starts `bin/bytewell-mcp`, a short shell script that runs the installed app's own helper,
  `Bytewell.app/Contents/Helpers/bytewell mcp`, over stdio. If the app isn't installed, it prints where to get it and
  exits.
- `skills/free-up-disk-space` tells Claude to load the app's current agent guide first and to preview every cleanup
  before asking you to approve it.

The plugin itself downloads nothing, installs nothing and sends nothing over the network. Scans and cleanups run
locally in the Bytewell app.

## License

The plugin's files are MIT licensed (`LICENSE`); the Bytewell app is proprietary. The Bytewell name and icon
(`.claude-plugin/icon.png`) belong to Axleno LLC and aren't covered by the MIT license.
