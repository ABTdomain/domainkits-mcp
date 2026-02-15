# DomainKits MCP

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
| `suggest` | AI-guided domain name brainstorming |
| `similar` | Find alternatives when a domain is taken |
| `plan_b` | Orchestrated search across deleted/expired/aged |
| `analyze` | Comprehensive domain audit |
| `brand_match` | Brand association risk detection |
| `expired_analysis` | In-depth analysis for expired domains before acquisition |

### Memory (GDPR Compliant)
| Tool | Description |
|------|-------------|
| `get_preferences` | Retrieve saved user preferences |
| `set_preferences` | Save preferences (requires explicit consent) |
| `delete_preferences` | Delete all stored data |

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

- **Guest** — No account needed. Most tools available with ~10 requests/day per category. Good for trying out.
- **Member** (free) — All tools including SEO analysis. 30-50 requests/day. Memory features enabled.
- **Premium** — 500 requests/day, deep search
- **Platinum** — Unlimited requests. No restrictions.

Get your API key at [domainkits.com](https://domainkits.com)

---

## Examples
```
"Find me a short .com domain for an AI startup"

"What domains with 'crypto' are expiring today?"

"Check if awesomeapp.com is available"

"Analyze the domain stripe.com"

"Show me trending keywords in domain registrations"

"Find 4-letter .com domains registered this week"
```

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