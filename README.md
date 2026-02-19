# DomainKits MCP
[![MCP Badge](https://lobehub.com/badge/mcp/abtdomain-domainkits-mcp?style=for-the-badge)](https://lobehub.com/mcp/abtdomain-domainkits-mcp)

The domain agent framework for AI assistants. DomainKits MCP combines domain intelligence tools with built-in industry expertise — turning Claude, GPT, Gemini, and other AI assistants into domain agents that can search, analyze, and act on market data through natural conversation.

## What is this?

DomainKits MCP is more than an API — it combines domain intelligence tools with built-in expertise, turning your AI into a domain agent that knows what to look for, how to analyze it, and when to act.

## Features

### Search Tools
| Tool | Description |
|------|-------------|
| `nrds` | Monitor newly registered domains, spot viral trends |
| `aged` | Find established domains with 5-20+ years history |
| `expired` | Discover domains entering deletion cycle |
| `deleted` | Search just-dropped domains available for standard registration |
| `active` | Scan live websites and acquisition targets |
| `ns_reverse` | Reverse lookup by nameserver |
| `unregistered_ai` | Find unregistered short .ai domains (3-letter, CVCV, VCVC, CCVV patterns) |


### Query Tools
| Tool | Description |
|------|-------------|
| `dns` | Query DNS records (A, MX, NS, TXT, etc.) |
| `whois` | Get registration details and dates |
| `safety` | Check domain reputation via Google Safe Browsing |
| `tld_check` | Check keyword availability across all TLDs |
| `available` | Instant availability check with pricing |

### Analysis Tools ⚠️
| Tool | Description |
|------|-------------|
| `backlink_summary` | SEO backlink profile analysis |
| `keyword_data` | Google Ads keyword data: volume, CPC, competition |

> ⚠️ Analysis tools require a registered account. [Sign up free](https://domainkits.com/login)

### Trend Tools
| Tool | Description |
|------|-------------|
| `tld_trends` | Historical registration trends by TLD |
| `keywords_trends` | Hot and emerging keywords in domain registrations |
| `tld_rank` | TLD rankings by registration volume |
| `price` | Registration and renewal prices by TLD |

### Bulk Tools
| Tool | Description |
|------|-------------|
| `bulk_tld` | Check keyword popularity across TLDs |
| `bulk_available` | Batch availability check with pricing (up to 10 per request) |

### Workflow Guides
| Tool | Description |
|------|-------------|
| `analyze` | Comprehensive domain audit (WHOIS, DNS, safety, TLD distribution) |
| `brand_match` | Brand conflict detection with trademark database links |
| `plan_b` | Find alternatives when target domain is taken |
| `domain_generator` | Generate creative domain ideas with availability check |
| `expired_analysis` | Due diligence for expiring/expired domains |
| `trend_hunter` | Spot trending keywords and find related opportunities |

### Preferences
| Tool | Description |
|------|-------------|
| `get_preferences` | Check memory status and retrieve saved preferences |
| `set_preferences` | Save preferences (TLDs, budget, style, industry) |
| `delete_preferences` | Delete all stored data (GDPR Article 17) |

### Monitor (Requires Memory)
| Tool | Description |
|------|-------------|
| `set_monitor` | Create domain monitoring task (WHOIS/DNS/page changes) |
| `get_monitors` | Retrieve and execute pending monitor checks |
| `update_monitor` | Save monitor check results |
| `delete_monitor` | Remove a monitoring task |

### Strategy (Requires Memory)
| Tool | Description |
|------|-------------|
| `set_strategy` | Create automated opportunity discovery strategy |
| `get_strategies` | Retrieve and execute pending strategies |
| `update_strategy` | Save strategy execution results |
| `delete_strategy` | Remove a strategy |

---

## Quick Start

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

Use endpoint: `https://api.domainkits.com/v1/mcp`

Optional header: `X-API-Key: your-api-key-here`

---

## Access Tiers

| Tier | Rate Limit | Monitors | Strategies | SEO Tools |
|------|------------|----------|------------|-----------|
| **Guest** | ~10/day per category | ❌ | ❌ | ❌ |
| **Member** (free) | 30-50/day | 5 | 1 | ✅ |
| **Premium** | 500/day | 50 | 3 | ✅ |
| **Platinum** | Unlimited | Unlimited | Unlimited | ✅ |

Get your API key at [domainkits.com](https://domainkits.com)

---

## Examples

**Search & Discovery**
- "Find available 3-letter .ai domains"
- "What domains with 'crypto' are expiring today?"
- "Show me trending keywords in domain registrations"

**Analysis**
- "Analyze the domain domainkits.com"
- "Check brand conflict risk for niceflow.com"

**Generation**
- "Find me a short .com domain for an AI startup"
- "Generate domain ideas for a fintech company"

**Monitoring** (requires memory)
- "Monitor domainkits.com for any changes"
- "Set up a strategy to find dropping AI domains daily"

---

## Memory & Privacy

DomainKits supports optional memory to remember your preferences:
- Preferred TLDs
- Budget range
- Naming style
- Industry

**GDPR Compliant:**
- Memory is OFF by default
- Requires explicit user consent to enable
- Users can delete all data anytime via `delete_preferences`

---

## Links

- Website: [domainkits.com/mcp](https://domainkits.com/mcp)
- API Endpoint: `https://api.domainkits.com/v1/mcp`
- GitHub: [github.com/ABTdomain/domainkits-mcp](https://github.com/ABTdomain/domainkits-mcp)
- Support: info@domainkits.com

## License

Proprietary. The MCP interface specification is public, but the underlying domain data and gateway services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).
