# OwlCAD

Parametric 3D CAD for 3D printing, for your AI assistant. This plugin connects Claude, GitHub
Copilot in VS Code, Cursor or Gemini CLI to OwlCAD's hosted MCP server, so the assistant can
build millimeter-dimensioned parts, check that they will print, and export STL, 3MF or STEP.
Everything it makes is a normal OwlCAD project: a tree of named, dimensioned parts you can open
in the browser editor at [owlcad.com](https://owlcad.com) and change afterwards.

## What it can do

- Build parts from primitives and booleans, built-in generators (gears, threads, Gridfinity
  bins and baseplates) and a library of datasheet-dimensioned parts.
- Check them: watertight build, size and volume, overhangs, thinnest wall, collisions between
  parts, and whether a part fits a given printer's bed. It can also cut an oversized part into
  printable pieces.
- Export STL, 3MF or OBJ for a slicer, STEP for other CAD tools, or a 2D drawing.
- List, read, edit, organize, share and delete your saved OwlCAD projects.

29 tools in all. The full list, with what each one does, is at
[owlcad.com/mcp-server](https://owlcad.com/mcp-server).

## Requirements

An OwlCAD account on the **Pro** plan. The first time the assistant uses OwlCAD, a browser opens
so you can sign in and approve what it may do. You can revoke the connection at any time from
Account settings on owlcad.com.

## What it runs, sends and fetches

This plugin contains configuration only. It runs nothing on your machine. It points your
assistant at `https://mcp.owlcad.com/`, OwlCAD's hosted server. Each tool call sends that server
the model or project the assistant is working on, and the server reads and writes projects in
your OwlCAD account. How that data is handled is described in the
[privacy policy](https://owlcad.com/privacy).

## Install

The server is `https://mcp.owlcad.com/` (Streamable HTTP). It signs you in with OAuth, so there is
no API key to copy.

- **Claude** (web, desktop): open [OwlCAD in Claude's directory](https://claude.ai/directory/owlcad)
  and select Connect. Or add it by URL: Settings → Connectors → Add custom connector, and paste
  `https://mcp.owlcad.com/`.
- **GitHub Copilot in VS Code:** run **MCP: Add Server** from the Command Palette, choose HTTP and
  enter `https://mcp.owlcad.com/`, or add it to `.vscode/mcp.json`, then sign in when VS Code asks:

  ```json
  { "servers": { "owlcad": { "type": "http", "url": "https://mcp.owlcad.com/" } } }
  ```

- **Claude Code:** `claude mcp add --transport http owlcad https://mcp.owlcad.com/`
- **Cursor:** add the server to `~/.cursor/mcp.json` (or a project's `.cursor/mcp.json`), then
  sign in when Cursor asks:

  ```json
  { "mcpServers": { "owlcad": { "url": "https://mcp.owlcad.com/" } } }
  ```

- **Gemini CLI:** `gemini extensions install https://github.com/Spare-Matter/owlcad-plugin`

Other MCP clients that speak Streamable HTTP work the same way: point them at the URL and sign in.

## Using it

Ask in plain language. For example:

- "Design a 60 mm wall hook with two screw holes and check that it prints."
- "Make a 2 by 3 Gridfinity bin, 6 units tall, and save it to OwlCAD."
- "Make a 20-tooth and a 40-tooth spur gear that mesh, check they don't collide, and export a STEP."
- "Export my latest OwlCAD project as a 3MF."

The assistant builds the model with OwlCAD's tools, checks it, and gives you a file or a link that
opens the project in the editor, where every dimension can still be changed. Units are
millimeters and Z points up.

## Support

[owlcad.com/contact](https://owlcad.com/contact) · contact@owlcad.com

## License

The files in this repository (configuration and documentation) are MIT-licensed; see
[LICENSE](LICENSE). The OwlCAD service they connect to is proprietary.
