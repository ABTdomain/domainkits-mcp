# DomainKits MCP

A Model Context Protocol (MCP) server that turns AI assistants into domain investment experts. Search, analyze, and discover domain names with real-time market data.

## What is this?

DomainKits MCP connects AI assistants (Claude, GPT, etc.) to professional domain intelligence tools. Instead of guessing domain availability, the AI can actually check it. Instead of generic naming suggestions, it validates ideas against real market data.

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
| `tld_trends` | Historical registration trends by TLD |
| `keywords_trends` | Hot and emerging keywords in domain registrations |
| `tld_rank` | TLD rankings by registration volume |
| `price` | Registration and renewal prices by TLD |

### Bulk Tools
| Tool | Description |
|------|-------------|
| `bulk_tld` | Check keyword popularity across TLDs |
| `bulk_available` | Batch availability check with pricing |

### Workflow Guides
| Tool | Description |
|------|-------------|
| `analyze` | Comprehensive domain audit (WHOIS, DNS, safety, TLD distribution) |
| `brand_match` | Brand conflict detection with trademark database links |
| `plan_b` | Find alternatives when target domain is taken |
| `domain_generator` | Generate creative domain ideas with availability check |
| `expired_analysis` | Due diligence for expiring/expired domains |
| `trend_hunter` | Spot trending keywords and find related opportunities |

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

## Quick Start

### Option A: Without API Key (Limited Access)

Add to your MCP client configuration:
```json
{
  "mcpServers": {
    "domainkits": {
      "url": "https://api.domainkits.com/v1/mcp"
    }
  }
}
```

### Option B: With API Key (Full Access)

1. Sign up at [domainkits.com](https://domainkits.com) to get your API key
2. Add to your MCP client configuration:
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

With API key you get:
- Higher rate limits
- More results per search
- Memory features (save preferences)
- Priority support

### 3. Start Using

Ask your AI assistant:
- "Find me a short .com domain for an AI startup"
- "What domains with 'crypto' are expiring today?"
- "Check if awesomeapp.com is available"
- "Analyze the domain domainkits.com"

## Usage Examples

### Find Available Domains
```
User: Help me find a domain for my vegan skincare brand

AI: [calls bulk_available with generated ideas]
    Found 3 available options:
    - veganglow.io ($39/year) - Register Now
    - purevegan.co ($29/year) - Register Now  
    - skincarelab.app ($14/year) - Register Now
```

### Monitor Trends
```
User: What keywords are trending in domain registrations?

AI: [calls keywords_trends type="emerging"]
    Top emerging keywords this week:
    1. "gpt" - 340% increase
    2. "llm" - 280% increase
    3. "agent" - 195% increase
```

### Domain Analysis
```
User: Analyze example.com for me

AI: [calls whois, dns, safety, tld_check]
    Domain Profile:
    - Registered: 1995 (29 years old)
    - Registrar: ICANN
    - Status: Active with MX records
    - Safety: Clean
    - Brand Protection: .net/.org also taken
```

## Access Tiers

| Tier | Daily Limits | Rate/Min | Monitors | Strategies | SEO Tools |
|------|-------------|----------|----------|------------|-----------|
| **Guest** | ~5-20/day | 1-4 | ❌ | ❌ | ❌ |
| **Member** (free) | 10-120/day | 2-10 | 5 | 1 | ✅ |
| **AI Access** ($13.99/mo) | 100-500/day | 5-20 | 20 | 3 | ✅ |
| **Premium** ($29.99/mo) | 200-1100/day | 10-50 | 50 | 6 | ✅ |
| **Platinum** | Unlimited | Unlimited | Unlimited | Unlimited | ✅ |

Limits vary by tool. AI Access is included with Premium.

## Memory & Privacy

DomainKits supports optional memory to remember your preferences:
- Preferred TLDs
- Budget range
- Naming style
- Industry

**GDPR Compliant:**
- Memory is OFF by default
- Requires explicit user consent to enable
- Users can delete all data anytime via `preferences` with `action: delete`

## Links

- Website: [domainkits.com](https://domainkits.com)
- API Endpoint: `https://api.domainkits.com/v1/mcp`
- Support: info@domainkits.com

## License

Proprietary. The MCP interface specification is public, but the underlying domain data and gateway services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).