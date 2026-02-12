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

### Query Tools
| Tool | Description |
|------|-------------|
| `dns` | Query DNS records (A, MX, NS, TXT, etc.) |
| `whois` | Get registration details and dates |
| `safety` | Check domain reputation via Google Safe Browsing |
| `tld_check` | Check keyword availability across all TLDs |
| `available` | Instant availability check with pricing |

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
| `suggest` | AI-guided domain name brainstorming |
| `similar` | Find alternatives when a domain is taken |
| `plan_b` | Orchestrated search across deleted/expired/aged |
| `analyze` | Comprehensive domain audit |

### Memory (GDPR Compliant)
| Tool | Description |
|------|-------------|
| `get_preferences` | Retrieve saved user preferences |
| `set_preferences` | Save preferences (requires explicit consent) |
| `delete_preferences` | Delete all stored data |

## Quick Start

### 1. Get an API Key

Sign up at [domainkits.com](https://domainkits.com) to get your API key.

### 2. Configure Your MCP Client

Add to your MCP client configuration:
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

### 3. Start Using

Ask your AI assistant:
- "Find me a short .com domain for an AI startup"
- "What domains with 'crypto' are expiring today?"
- "Check if awesomeapp.com is available"
- "Analyze the domain stripe.com"

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

## Rate Limits

| Tier | Requests/Min | Daily Limit |
|------|--------------|-------------|
| Guest | 5 | 50 |
| Member | 20 | 500 |
| Premium | 60 | 2000 |
| Platinum | Unlimited | Unlimited |

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

## Links

- Website: [domainkits.com](https://domainkits.com)
- API Endpoint: `https://api.domainkits.com/v1/mcp`
- Support: info@domainkits.com

## License

Proprietary. The MCP interface specification is public, but the underlying domain data and gateway services are proprietary.

For commercial use and API access, visit [domainkits.com](https://domainkits.com).