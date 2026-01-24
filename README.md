# DomainKits MCP Server

Domain intelligence tools through MCP-compatible clients.

## Endpoints

| Endpoint | Description |
|----------|-------------|
| `https://mcp.domainkits.com/mcp/nrds` | Newly Registered Domains Search |
| `https://mcp.domainkits.com/mcp/ns-reverse` | NS Reverse Lookup |
| `https://mcp.domainkits.com/mcp/whois` | WHOIS Lookup |
| `https://mcp.domainkits.com/mcp/dns` | DNS Lookup |

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
    "domainkits-whois": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/whois",
        "--transport",
        "http-first"
      ]
    },
    "domainkits-dns": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.domainkits.com/mcp/dns",
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
    "domainkits-whois": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.domainkits.com/mcp/whois"]
    },
    "domainkits-dns": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.domainkits.com/mcp/dns"]
    }
  }
}
```

---

## Tools

### search_nrds

Search for newly registered domains by keyword.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| keyword | string | Yes | - | Search term (a-z, 0-9, hyphen only, max 20 chars) |
| days | integer | Yes | - | 1-7 |
| position | string | No | any | `start`, `end`, or `any` |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`, `org`) |

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/nrds \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_nrds","arguments":{"keyword":"ai","days":7,"position":"start","tld":"com"}}}'
```

---

### search_ns_reverse

Look up gTLD domains hosted on a specific nameserver.

**Parameters:**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| ns | string | Yes | - | Nameserver hostname (e.g., `ns1.google.com`) |
| tld | string | No | all | Filter by TLD (e.g., `com`, `net`, `org`) |
| min_len | integer | No | - | Minimum domain prefix length |
| max_len | integer | No | - | Maximum domain prefix length |

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/ns-reverse \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_ns_reverse","arguments":{"ns":"ns1.google.com","tld":"com","min_len":4,"max_len":8}}}'
```

---

### whois_lookup

Look up WHOIS information for a domain.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| domain | string | Yes | Domain name (e.g., `example.com`) |

**Response fields:**
- `domain` - Domain name
- `registrar` - Registrar name
- `created` - Creation date
- `expires` - Expiry date
- `updated` - Last updated date
- `status` - Domain status codes
- `nameservers` - List of nameservers

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/whois \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"whois_lookup","arguments":{"domain":"google.com"}}}'
```

---

### dns_lookup

Look up DNS records for a domain.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| domain | string | Yes | Domain name (e.g., `example.com`) |

**Response fields:**
- `domain` - Domain name
- `a` - A records (IPv4)
- `aaaa` - AAAA records (IPv6)
- `ns` - Nameserver records
- `mx` - Mail exchange records
- `txt` - TXT records
- `cname` - CNAME records

**Example:**
```bash
curl -X POST https://mcp.domainkits.com/mcp/dns \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"dns_lookup","arguments":{"domain":"google.com"}}}'
```

---

## Limits

- 10 requests per minute per IP
- 5 domains per response (NRDS, NS Reverse)
- NRDS data may have 24-48 hour delay

## Full Access

For complete results with advanced filters and export:
- **NRDS**: [domainkits.com/search/new](https://domainkits.com/search/new)
- **NS Reverse**: [domainkits.com/tools/ns-reverse](https://domainkits.com/tools/ns-reverse)
- **WHOIS**: [domainkits.com/tools/whois](https://domainkits.com/tools/whois)
- **DNS**: [domainkits.com/tools/dns](https://domainkits.com/tools/dns)

## About

[DomainKits](https://domainkits.com) - Domain intelligence tools for investors, brand managers, and researchers.

## Privacy

This service is designed with privacy in mind:
- **IP addresses are anonymized** - Only the first two segments are logged (e.g., `192.168.x.x`)
- **Search queries are anonymized** - Only first and last 2 characters are logged (e.g., `go***le`)
- **Logs are retained for 7 days** and automatically deleted
- **No personal data is collected** - No accounts, no cookies, no tracking
- **No data is shared** with third parties

For full privacy policy, visit [domainkits.com/privacy](https://domainkits.com/privacy)

This service complies with GDPR data minimization principles.

## License

MIT