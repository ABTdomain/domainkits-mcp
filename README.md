# DomainKits MCP

Domain MCP server for AI assistants. DomainKits MCP connects Claude, GPT, Gemini, and other AI assistants to domain data, turning them into domain agents that can search, analyze, and act on market data through natural conversation.

## What is this?

Check availability with pricing. Search newly registered, expired, and deleted domains. Analyze WHOIS, DNS, backlinks, and keyword value. Track registration trends and market movements. Pair with [DomainKits Skills](https://github.com/ABTdomain/domainkits-skills) to give your AI agent domain industry workflows for deeper analysis.

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
| `domain_changes` | Domain change detection, actively monitors 4M+ domains for transfers, expirations, new registrations, and NS changes |
| `price` | Registration and renewal prices by TLD |

### Query Tools
| Tool | Description |
|------|-------------|
| `dns` | Query DNS records (A, MX, NS, TXT, etc.) |
| `whois` | Get registration details and dates |
| `safety` | Check domain reputation via Google Safe Browsing |
| `tld_check` | Check keyword availability across all TLDs |
| `available` | Instant availability check with pricing |
| `market_price` | Check secondary market listings and price estimates |

### Analysis Tools ⚠️
| Tool | Description |
|------|-------------|
| `backlink_summary` | SEO backlink profile analysis |
| `keyword_data` | Google Ads keyword data: volume, CPC, competition |

> ⚠️ Analysis tools require a registered account. [Sign up free](https://domainkits.com/login)

### Trend Tools
| Tool | Description |
|------|-------------|
| `keywords_trends` | Hot, emerging, and prefix keywords in domain registrations |
| `tld_trends` | Historical registration trends by TLD |
| `tld_rank` | TLD rankings by registration volume |

### Bulk Tools
| Tool | Description |
|------|-------------|
| `bulk_tld` | Check keyword popularity across TLDs |
| `bulk_available` | Batch availability check with pricing (up to 10 per request) |

### Workflow Guides
| Tool | Description |
|------|-------------|
| `analyze` | Comprehensive domain analysis (WHOIS, DNS, safety, TLD distribution) |
| `brand_match` | Brand conflict detection with trademark database links |
| `plan_b` | Find alternatives when target domain is taken |
| `domain_generator` | Generate creative domain ideas with availability check |
| `expired_analysis` | Due diligence for expiring/expired domains |
| `trend_hunter` | Spot trending keywords and find related opportunities |
| `keyword_intel` | Deep keyword intelligence for domain investment |
| `market_beat` | Domain market news briefing |
| `name_advisor` | Professional domain naming consultation |
| `valuation_cma` | Comparative Market Analysis valuation |

### Personal Tools (Require Memory)
| Tool | Action | Description |
|------|--------|-------------|
| `preferences` | `get` | Check memory status and retrieve saved preferences |
| `preferences` | `set` | Save preferences (TLDs, budget, style, industry) |
| `preferences` | `delete` | Delete all stored data (GDPR Article 17) |
| `monitor` | `get` | Retrieve and auto-check all monitored domains |
| `monitor` | `set` | Create domain monitoring task (WHOIS/DNS/page changes) |
| `monitor` | `update` | Save web_fetch page results for a monitor |
| `monitor` | `delete` | Remove a monitoring task |
| `strategy` | `get` | Retrieve strategies with run status and available presets |
| `strategy` | `set` | Create automated opportunity discovery strategy |
| `strategy` | `update` | Save strategy execution results |
| `strategy` | `delete` | Remove a strategy |
| `usage` | — | Check current usage and remaining quota |

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

Connect DomainKits via **Settings → Connectors**. No manual configuration needed.

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

## Access Tiers

| Tier | Daily Limits | Rate/Min | Monitors | Strategies | SEO Tools |
|------|-------------|----------|----------|------------|-----------|
| **Guest** | ~5-20/day | 1-4 | ❌ | ❌ | ❌ |
| **Member** (free) | 10-120/day | 2-10 | 5 | 1 | ✅ |
| **AI Access** ($13.99/mo) | 100-500/day | 5-20 | 20 | 3 | ✅ |
| **Premium** ($29.99/mo) | 200-1100/day | 10-50 | 50 | 6 | ✅ |
| **Platinum** | Unlimited | Unlimited | Unlimited | Unlimited | ✅ |

Limits vary by tool. AI Access is included with Premium.

Register a free account and get your API key at [domainkits.com](https://domainkits.com/register) · [View pricing](https://domainkits.com/pricing)

---

## Examples

**Search & Discovery**
- "Find available 3-letter .ai domains"
- "What domains with 'crypto' are expiring today?"
- "Show me trending keywords in domain registrations"
- "What short domains changed NS in the last 1 hour?"

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
- Skills: [github.com/ABTdomain/domainkits-skills](https://github.com/ABTdomain/domainkits-skills)
- Developed by: [abtdomain.com](https://abtdomain.com)
- Support: info@domainkits.com


## License

Proprietary. The MCP interface specification is public, but the underlying domain data and gateway services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).