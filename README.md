# DomainKits MCP Server - Newly Registered Domains Search

Search newly registered domains through MCP-compatible clients.

## Endpoint
```
https://mcp.domainkits.com/mcp/nrds
```

## Configuration

### Claude Desktop

Edit config file:
- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/nrds",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

### Cursor

Edit `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/nrds"
      ]
    }
  }
}
```

## Tool

### search_domains

Search for newly registered domains by keyword.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| keyword | string | Yes | - | Search term (a-z, 0-9, hyphen only, max 20 chars) |
| days | integer | Yes | - | 1-7 |
| position | string | No | any | `start`, `end`, or `any` |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`, `org`) |

**Position Examples:**

| Position | Keyword | Matches |
|----------|---------|---------|
| `start` | ai | ai-tools.com, aihelper.net |
| `end` | ai | openai.com, myai.net |
| `any` | ai | ai-tools.com, openai.com, domain-ai-hub.net |

**Example Request:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/nrds \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_domains","arguments":{"keyword":"ai","days":7,"position":"start","tld":"com"}}}'
```

**Example Response:**
```json
{
  "total": 1234,
  "domains": [
    "ai-tools.com",
    "ai-helper.com",
    "ai-market.com",
    "ai-studio.com",
    "ai-hub.com"
  ],
  "tip": "Search more at https://domainkits.com/search/new"
}
```

## Limits

- 10 requests per minute per IP
- 5 domains per response
- Data may have 24-48 hour delay

## Full Search

For complete newly registered domains search with advanced filters and export, visit [domainkits.com/search/new](https://domainkits.com/search/new)


## About

[DomainKits](https://domainkits.com) - Domain intelligence tools for investors, brand managers, and researchers.

## License

MIT
