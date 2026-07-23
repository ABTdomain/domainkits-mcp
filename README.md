[![smithery badge](https://smithery.ai/badge/DomainKits/domainkits)](https://smithery.ai/servers/DomainKits/domainkits)
# DomainKits MCP

Domain data server for AI assistants. DomainKits MCP connects Claude, GPT, Gemini, and other AI assistants to live domain registration, DNS, availability, trend, and market data through the [Model Context Protocol](https://modelcontextprotocol.io/).

MCP is the **data layer**. For domain industry workflows (naming consultation, competitive analysis, keyword intelligence, expired domain due diligence, and more), see [DomainKits Skills](https://github.com/ABTdomain/domainkits-skills), an open-source collection of workflow prompts that any AI assistant can use on top of this data.

## Tools

### Search
| Tool | Description |
|------|-------------|
| `nrds` | Newly registered domains by keyword, or browse a gTLD |
| `aged` | Established domains with registration history by keyword, or browse a gTLD |
| `expired` | Domains entering the deletion cycle by keyword, or browse a gTLD |
| `deleted` | Just-dropped domains available for standard registration |
| `active` | Live registered domains (~240M gTLD database) |
| `market` | Domains carrying marketplace listing data by keyword, or browse a gTLD |
| `ns_reverse` | Reverse lookup by nameserver |
| `unregistered_ai` | Unregistered short .ai domains (3-letter, pattern-based) |
| `domain_changes` | Domain change detection across 4M+ monitored domains (transfers, expirations, NS changes) |
| `typosquat` | Typosquat scanner (dnstwist-style permutations) with live registration verification |

### Lookup
| Tool | Description |
|------|-------------|
| `dns` | DNS records (A, AAAA, MX, NS, TXT, SOA) |
| `whois` | WHOIS/RDAP registration data (registrar, dates, status, nameservers) |
| `safety` | Google Safe Browsing status |
| `available` | Single-domain availability with pricing |
| `tld_check` | Keyword availability across TLDs |
| `keyword_data` | Google Ads keyword data (volume, CPC, competition) |
| `price` | Standard registration and renewal prices by TLD |
| `market_price` | Secondary market listing prices |
| `backlink_summary` | SEO backlink profile |

### Trends
| Tool | Description |
|------|-------------|
| `keywords_trends` | Hot, emerging, and prefix keywords in domain registrations |
| `tld_trends` | Historical registration trends by TLD |
| `tld_rank` | TLD rankings by registration volume |

### Bulk
| Tool | Description |
|------|-------------|
| `bulk_tld` | Keyword popularity across TLDs |
| `bulk_available` | Batch availability check (up to 10 domains) |

### Stateful (require memory)
| Tool | Action | Description |
|------|--------|-------------|
| `preferences` | `get` | Check memory status and saved preferences |
| `preferences` | `set` | Save preferences (TLDs, budget, style, industry) |
| `preferences` | `delete` | Delete all stored data (GDPR Article 17) |
| `monitor` | `get` | Retrieve and check all monitored domains |
| `monitor` | `set` | Create a monitoring task (WHOIS, DNS, page changes) |
| `monitor` | `update` | Save check results for a monitor |
| `monitor` | `delete` | Remove a monitoring task |
| `strategy` | `get` | Retrieve saved strategies with run status |
| `strategy` | `set` | Store user-authored strategy text |
| `strategy` | `update` | Save strategy execution results |
| `strategy` | `delete` | Remove a strategy |
| `usage` | | Current tier, per-group usage, and remaining quota |

Stateful data is server-side and cross-platform: preferences, monitors, and strategies persist across Claude, Gemini, Cursor, and any other MCP client under the same account. All data encrypted at rest (AES-256-GCM) in isolated per-user directories.

---

## Quick Start

### Claude Code

```bash
claude mcp add domainkits https://api.domainkits.com/v1/mcp
```

With API key (higher limits):

```bash
claude mcp add domainkits https://api.domainkits.com/v1/mcp --header "X-API-Key: YOUR_KEY"
```

### Claude.ai

Connect DomainKits via **Settings > Connectors**. No manual configuration needed.

### Claude Desktop

Edit your config file:
- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

**macOS / Linux:**
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://api.domainkits.com/v1/mcp",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

**Windows:**
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "mcp-remote",
        "https://api.domainkits.com/v1/mcp",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

**With API key (higher limits):**

macOS / Linux:
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://api.domainkits.com/v1/mcp",
        "--header",
        "X-API-Key: your-api-key-here",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

Windows:
```json
{
  "mcpServers": {
    "domainkits": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "mcp-remote",
        "https://api.domainkits.com/v1/mcp",
        "--header",
        "X-API-Key: your-api-key-here",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

### Gemini CLI

Edit `~/.gemini/settings.json`:
```json
{
  "mcpServers": {
    "domainkits": {
      "url": "https://api.domainkits.com/v1/mcp"
    }
  }
}
```

With API key:
```json
{
  "mcpServers": {
    "domainkits": {
      "url": "https://api.domainkits.com/v1/mcp",
      "headers": {
        "X-API-Key": "your-api-key-here"
      }
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
      "url": "https://api.domainkits.com/v1/mcp"
    }
  }
}
```

### Other MCP Clients

Endpoint: `https://api.domainkits.com/v1/mcp`

Optional header: `X-API-Key: your-api-key-here`

---

## Skills

DomainKits MCP serves raw data. [DomainKits Skills](https://github.com/ABTdomain/domainkits-skills) are open-source workflow prompts that teach AI assistants how to use that data for domain industry tasks:

- **Domain Name Advisor** -- naming consultation with availability checking
- **Domain Analyze** -- comprehensive WHOIS, DNS, backlink, and market analysis
- **CMA Valuation** -- comparative market analysis against current for-sale listings
- **Expired Domain Analysis** -- due diligence for auction, backorder, and dropping domains
- **Keyword Intel** -- keyword-level supply, demand, and concentration analysis
- **Keyword Trend Hunter** -- spot trending keywords and find registration opportunities
- **Domain Generator** -- creative domain name generation with validation
- **Plan B** -- systematic alternatives when a target domain is taken

Skills work with any MCP client. Add them alongside this server and the AI assistant gains both raw data access and structured workflows.

---

## Access Tiers

| | Guest | Member (free) | Premium | Platinum |
|---|---|---|---|---|
| **Search tools** | Limited | 2,000/day | 2,000/day, unlimited pages | Unlimited |
| **Lookup tools** | Limited | Varies | 50-600/day | Unlimited or high cap |
| **Trend tools** | Limited | Unlimited | Unlimited | Unlimited |
| **Bulk tools** | Limited | Limited | 1,000/day | Unlimited |
| **Backlink summary** | -- | 20/day | 20/day | 200/day |
| **Monitors** | -- | 5 | 50 | Unlimited |
| **Strategies** | -- | 1 | 6 | Unlimited |

Limits vary by tool group. See `usage` tool output for exact per-group quotas.

Register free at [domainkits.com](https://domainkits.com/register). [View pricing](https://domainkits.com/pricing).

---

## Examples

**Search and discovery**
- "Find domains with 'solar' registered in the last 7 days"
- "What .ai domains are expiring this week?"
- "Show me trending keywords in .com registrations"
- "What short domains changed nameservers in the last hour?"

**Lookup**
- "Check DNS and WHOIS for example.com"
- "Is mybrand.ai available? What does it cost?"
- "What domains are on ns1.example.com?"

**Trends**
- "What are the hottest keywords in domain registrations right now?"
- "Compare .ai vs .io registration trends over 90 days"

**Monitoring** (requires memory)
- "Monitor example.com for WHOIS and DNS changes"
- "Save a strategy: find dropping 4-letter .com domains daily"

---

## Privacy

- Memory is off by default and requires explicit consent
- All stored data is encrypted at rest (AES-256-GCM)
- Isolated per-user directories
- Full data deletion via `preferences` with `action: delete` (GDPR Article 17)

---

## Links

- Website: [domainkits.com/mcp](https://domainkits.com/mcp)
- Skills: [github.com/ABTdomain/domainkits-skills](https://github.com/ABTdomain/domainkits-skills)
- API Endpoint: `https://api.domainkits.com/v1/mcp`
- Support: info@domainkits.com

## License

Proprietary. The MCP interface specification is public, but the underlying domain data and services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).
