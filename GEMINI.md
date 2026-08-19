# DomainKits MCP

Domain data server for AI assistants. DomainKits MCP connects Claude, GPT, Gemini, and other AI assistants to live domain registration, DNS, availability, trend, and market data through the [Model Context Protocol](https://modelcontextprotocol.io/).

MCP is the **data layer**. For domain industry workflows (naming consultation, competitive analysis, keyword intelligence, expired domain due diligence, and more), see [DomainKits Skills](https://github.com/ABTdomain/domainkits-skills), an open-source collection of workflow prompts that any AI assistant can use on top of this data.

## Tools

### Search
| Tool | Description |
|------|-------------|
| `nrds` | Newly registered domains by keyword, or browse a gTLD |
| `nrds_live` | Live feed of domains registered in the last three days, updated continuously |
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
| `bulk_available` | Batch availability check (up to 50 domains) |

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

## Quick Start

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

With API key (higher limits):
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

### Other MCP Clients

Endpoint: `https://api.domainkits.com/v1/mcp`

Optional header: `X-API-Key: your-api-key-here`

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

## Examples

**Search and discovery**
- "Find domains with 'solar' registered in the last 7 days"
- "What has been registered in the last few hours with 'agent' in the name?"
- "What .ai domains are expiring this week?"
- "Show me trending keywords in .com registrations"

**Lookup**
- "Check DNS and WHOIS for example.com"
- "Is mybrand.ai available? What does it cost?"

**Brand protection**
- "Run a typosquat scan on ourbank.com"
- "Any new registrations containing 'acme' in the last 10 days?"

**Trends**
- "What are the hottest keywords in domain registrations right now?"
- "Compare .ai vs .io registration trends over 90 days"

## Privacy

- Memory is off by default and requires explicit consent
- All stored data is encrypted at rest (AES-256-GCM)
- Isolated per-user directories
- Full data deletion via `preferences` with `action: delete` (GDPR Article 17)

## Links

- Website: [domainkits.com/mcp](https://domainkits.com/mcp)
- Skills: [github.com/ABTdomain/domainkits-skills](https://github.com/ABTdomain/domainkits-skills)
- API Endpoint: `https://api.domainkits.com/v1/mcp`
- Support: info@domainkits.com

## License

Proprietary. The MCP interface specification is public, but the underlying domain data and services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).
