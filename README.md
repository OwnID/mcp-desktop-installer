# MCP Server Installer

A simple utility to add MCP servers to Claude Desktop, VSCode, or Cursor.

[![npm version](https://badge.fury.io/js/%40ownid%2Fmcp-desktop-installer.svg)](https://badge.fury.io/js/%40ownid%2Fmcp-desktop-installer)

## Installation

This package is designed to be used with `npx` without installation:

```bash
npx @ownid/mcp-desktop-installer <install-target> <server-name> <server-url>
```

## Usage

### Add a new MCP server:

```bash
npx @ownid/mcp-desktop-installer "Claude Desktop" acme https://abc.server.ownid.ai/mcp/ai
```

This will add a server named "acme" to your Claude Desktop configuration.

### Supported Install Targets:

- `"Claude Desktop"` - For Claude Desktop application
- `"VSCode"` - For Visual Studio Code
- `"Cursor"` - For Cursor editor

Install targets are case-insensitive and support variations (e.g., "claude", "vs code").

### Global Installation:

```bash
npm install -g @ownid/mcp-desktop-installer
mcp-desktop-installer <install-target> <server-name> <server-url>
```

### Command Line Options:

```
--help, -h     Display usage information
--version, -v  Display version information
```

## How it works

The installer updates the configuration file for the selected target with a new MCP server entry:

- Claude Desktop:
  - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
  - Windows: `%APPDATA%\Claude\claude_desktop_config.json`
  - Other platforms: `~/.anthropic/config.json` (fallback)

- VSCode:
  - `~/.vscode/mcp.json`

- Cursor:
  - `~/.cursor/mcp.json`

Example configuration (Claude Desktop):

```json
{
  "mcpServers": {
    "acme": {
      "command": "/path/to/npx",
      "args": [
        "-y",
        "@ownid/mcp-remote@next",
        "https://abc.server.ownid.ai/mcp/ai"
      ]
    }
  }
}
```

## Requirements

- Node.js 14 or later
- Claude Desktop installed

## Troubleshooting

### Common Issues

1. **Configuration file not updating**
   - Make sure the target application is not running when you update the configuration
   - Check that you have write permissions to the configuration directory

2. **MCP server not appearing in the application**
   - Restart the application after adding the MCP server
   - Verify the configuration file was updated correctly

3. **Incorrect install target**
   - Make sure you're using one of the supported targets: "Claude Desktop", "VSCode", or "Cursor"
   - Check the command line arguments order: <install-target> <server-name> <server-url>

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
