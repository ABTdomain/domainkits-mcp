# DomainKits MCP Server

Domain intelligence tools through MCP-compatible clients.

## Endpoints

| Endpoint | Description |
|----------|-------------|
| `https://mcp.domainkits.com/mcp/nrds` | Newly Registered Domains Search |
| `https://mcp.domainkits.com/mcp/ns-reverse` | NS Reverse Lookup |
| `https://mcp.domainkits.com/mcp/count` | Domain Count by Type |

## Configuration

### Claude Desktop

Edit config file:
- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
```json
{
  "mcpServers": {
    "domainkits-nrds": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/nrds",
        "--transport",
        "http-first"
      ]
    },
    "domainkits-ns-reverse": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/ns-reverse",
        "--transport",
        "http-first"
      ]
    },
    "domainkits-count": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/count",
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
    "domainkits-nrds": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.domainkits.com/mcp/nrds"]
    },
    "domainkits-ns-reverse": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.domainkits.com/mcp/ns-reverse"]
    },
    "domainkits-count": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.domainkits.com/mcp/count"]
    }
  }
}
```

---

### Gemini CLI
```bash
gemini extensions install https://github.com/AKBTdomain/domainkits-mcp
```

## Tools

### search_nrds

Search for newly registered domains by keyword.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| keyword | string | Yes | - | Search term (a-z, 0-9, hyphen only, min 3 chars) |
| days | integer | Yes | - | Search range in days (1-7) |
| position | string | No | any | `start`, `end`, or `any` |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`) |
| ns | string | No | all | Filter by nameserver (e.g., `ns1.google.com`) |
| min_len | integer | No | - | Minimum domain prefix length |
| max_len | integer | No | - | Maximum domain prefix length |
| has_number | boolean | No | - | Only domains containing numbers |
| has_hyphen | boolean | No | - | Only domains containing hyphens |
| is_alpha | boolean | No | - | Only pure letter domains (a-z) |
| is_digit | boolean | No | - | Only pure numeric domains (0-9) |
| exclude_keywords | array | No | - | Exclude domains containing these keywords |

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/nrds \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_nrds","arguments":{"keyword":"tech","days":7,"position":"start","tld":"com","is_alpha":true}}}'
```

**Response:**
```json
{
  "total": 128,
  "showing": 5,
  "domains": [
    {"domain": "techflow.com", "ns": "ns1.example.com"},
    {"domain": "techbase.com", "ns": "ns2.example.com"}
  ]
}
```

---

### search_ns_reverse

Look up gTLD domains hosted on a specific nameserver.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| ns | string | Yes | - | Nameserver hostname (e.g., `ns1.google.com`) |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`) |
| min_len | integer | No | - | Minimum domain prefix length |
| max_len | integer | No | - | Maximum domain prefix length |
| has_number | boolean | No | - | Only domains containing numbers |
| has_hyphen | boolean | No | - | Only domains containing hyphens |
| is_alpha | boolean | No | - | Only pure letter domains (a-z) |
| is_digit | boolean | No | - | Only pure numeric domains (0-9) |
| keyword | string | No | - | Filter domains containing this keyword |
| exclude_keywords | array | No | - | Exclude domains containing these keywords |

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/ns-reverse \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_ns_reverse","arguments":{"ns":"ns1.google.com","tld":"com","is_alpha":true,"min_len":4,"max_len":8}}}'
```

**Response:**
```json
{
  "ns": "ns1.google.com",
  "total": 50000,
  "matched": 1234,
  "showing": 5,
  "samples": ["example.com", "domain.com", "test.com"]
}
```

---

### count_domains

Count domains by type with filters. Supports multiple data sources.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| type | string | Yes | - | Data source: `nrds`, `expired`, `aged` |
| keyword | string | Yes* | - | Search term (min 3 chars, required for nrds) |
| days | integer | Yes* | - | Search range in days (1-7, required for nrds) |
| position | string | No | any | `start`, `end`, or `any` |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`) |
| ns | string | No | all | Filter by nameserver |
| min_len | integer | No | - | Minimum domain prefix length |
| max_len | integer | No | - | Maximum domain prefix length |
| has_number | boolean | No | - | Only domains containing numbers |
| has_hyphen | boolean | No | - | Only domains containing hyphens |
| is_alpha | boolean | No | - | Only pure letter domains (a-z) |
| is_digit | boolean | No | - | Only pure numeric domains (0-9) |

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/count \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"count_domains","arguments":{"type":"nrds","keyword":"tech","days":7,"tld":"com"}}}'
```

**Response:**
```json
{
  "type": "nrds",
  "total": 128
}
```

---

## Limits

- 10 requests per minute per IP
- 5 domains per response
- NRDS data may have 24-48 hour delay

## Full Access

For complete results with advanced filters and export:

- **NRDS**: [domainkits.com/search/new](https://domainkits.com/search/new)
- **NS Reverse**: [domainkits.com/tools/ns-reverse](https://domainkits.com/tools/ns-reverse)

## About

[DomainKits](https://domainkits.com) - Domain intelligence tools for investors, brand managers, and researchers.

## Privacy

- IP addresses anonymized
- Search queries anonymized
- Logs retained 7 days
- No personal data collected

## License

MIT