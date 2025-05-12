# Claude Desktop MCP Server Installer

A simple utility to add MCP servers to Claude Desktop.

[![npm version](https://badge.fury.io/js/%40ownid%2Fclaude-desktop-installer.svg)](https://badge.fury.io/js/%40ownid%2Fclaude-desktop-installer)

## Installation

This package is designed to be used with `npx` without installation:

```bash
npx @ownid/claude-desktop-installer <server-name> <server-url>
```

## Usage

### Add a new MCP server to Claude Desktop:

```bash
npx @ownid/claude-desktop-installer luminok http://localhost:4001/cm9fkjx5e0001ma0q76oaar0c/sse
```

This will add a server named "luminok" to your Claude Desktop configuration.

### Global Installation:

```bash
npm install -g @ownid/claude-desktop-installer
claude-desktop-installer <server-name> <server-url>
```

### Command Line Options:

```
--help, -h     Display usage information
--version, -v  Display version information
```

## How it works

The installer updates the Claude Desktop configuration file with a new MCP server entry in the following format:

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "luminok": {
      "command": "npx",
      "args": [
        "@ownid/mcp-remote",
        "http://localhost:4001/cm9fkjx5e0001ma0q76oaar0c/sse"
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
   - Make sure Claude Desktop is not running when you update the configuration
   - Check that you have write permissions to the configuration directory

2. **MCP server not appearing in Claude Desktop**
   - Restart Claude Desktop after adding the MCP server
   - Verify the configuration file was updated correctly

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
