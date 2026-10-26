#!/bin/sh
# Starts Bytewell's MCP server from wherever the app is installed: /Applications, or ~/Applications.
for app in /Applications/Bytewell.app "$HOME/Applications/Bytewell.app"; do
  if [ -x "$app/Contents/Helpers/bytewell" ]; then
    exec "$app/Contents/Helpers/bytewell" mcp "$@"
  fi
done
echo "Bytewell isn't installed in /Applications or ~/Applications. Get it free at https://bytewell.app" >&2
exit 1
