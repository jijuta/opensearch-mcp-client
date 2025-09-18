# OpenSearch MCP Client

Simple HTTP client to connect Claude Desktop to OpenSearch MCP servers.

## 🚀 Quick Install

```bash
npm install -g opensearch-mcp-client
```

## 🎯 What does this do?

This is a **simple HTTP proxy** that:
1. Takes JSON-RPC messages from Claude Desktop (stdin)
2. Forwards them to your OpenSearch MCP server via HTTP
3. Returns responses back to Claude Desktop (stdout)

**No hardcoded servers, no exposed credentials!** All configuration is done in Claude Desktop.

## 🔧 Usage

### 1. Install globally
```bash
npm install -g opensearch-mcp-client
```

### 2. Configure Claude Desktop

Add to your Claude Desktop config file:

**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
**Linux**: `~/.config/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "opensearch": {
      "command": "opensearch-mcp-client",
      "env": {
        "MCP_SERVER_URL": "http://your-server:port"
      }
    }
  }
}
```

**Replace `http://your-server:8099` with your actual MCP server URL**

### 3. Restart Claude Desktop

Your OpenSearch tools will now be available! 🎉

## 🔒 Security Features

- **No hardcoded servers**: All configuration via environment variables
- **No credentials in code**: Server URLs specified only in Claude Desktop config
- **Minimal dependencies**: Only axios for HTTP requests
- **Clear error messages**: Helpful guidance when misconfigured

## 🛠️ Available OpenSearch Tools

Once connected, you'll have access to:

- **Index_Lister**: List all OpenSearch indices
- **Index_Searcher**: Search within indices using Query DSL
- **Cluster_Health_Checker**: Check cluster health status
- **IndexMappingTool**: Get index mappings and settings
- **GetShardsTool**: View shard information
- **CountTool**: Count documents in indices
- **MsearchTool**: Multi-search operations
- **ExplainTool**: Explain query execution

## 🔍 Troubleshooting

### "MCP_SERVER_URL environment variable is required"
You need to set the server URL in your Claude Desktop configuration. See [Usage](#usage) section above.

### Connection failed
- Verify your MCP server is running
- Check the URL format: `http://ip:port` or `https://domain:port`
- Test connectivity: `curl http://your-server:port/health`

### Claude Desktop not recognizing
- Check JSON config syntax with a JSON validator
- Restart Claude Desktop completely
- Check Claude Desktop logs for errors

## 🏗️ Requirements

- Node.js 16+
- Access to an OpenSearch MCP server
- Claude Desktop

## 📝 License

MIT

---

**Secure, simple, and configurable!** 🔒
