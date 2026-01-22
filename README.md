# DomainKits MCP Server

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
        "https://mcp.domainkits.com/mcp/nrds"
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

| Name | Type | Required | Description |
|------|------|----------|-------------|
| keyword | string | Yes | Search term (a-z, 0-9, hyphen only, max 20 chars) |
| days | integer | Yes | 1, 2, or 3 |

**Response:**
```json
{
  "total": 428,
  "domains": [
    "cryptobet365.biz",
    "cryptobot-contest-mrxmxr.bond",
    "cryptob2.buzz",
    "cryptob3.buzz",
    "cryptohq.capital",
    "cryptoaitraders.com",
    "latitude18crypto.com",
    "crypto-toolman.com",
    "eligiblecrypto.com",
    "cryptonewsmap.com"
  ],
  "tip": "Search more at https://domainkits.com/search/new"
}
```

## Limits

- 10 requests per minute per IP
- 10 domains per response
- Data may have 24-48 hour delay

## Full Search

For complete results with filters and export, visit [domainkits.com/search/new](https://domainkits.com/search/new)

## About

[DomainKits](https://domainkits.com) - Domain intelligence tools for investors, brand managers, and researchers.

## License

MIT
