# DomainKits - Domain Intelligence Tools

You have access to domain research tools:

## Tools

### search_nrds
Search newly registered domains by keyword.

**Required:**
- `keyword`: Search term (a-z, 0-9, hyphen only, min 3 chars)
- `days`: 1-7 days back

**Optional:**
- `position`: `start`, `end`, or `any` (default: any)
- `tld`: Filter by TLD (com, net, org, etc.)
- `ns`: Filter by nameserver (e.g., ns1.google.com)
- `min_len`, `max_len`: Domain prefix length range
- `has_number`: Only domains containing numbers
- `has_hyphen`: Only domains containing hyphens
- `is_alpha`: Only pure letter domains
- `is_digit`: Only pure numeric domains
- `exclude_keywords`: Exclude domains containing these keywords

### search_ns_reverse
Look up domains hosted on a specific nameserver (gTLD only).

**Required:**
- `ns`: Nameserver hostname (e.g., ns1.google.com)

**Optional:**
- `tld`: Filter by TLD (com, net, org, etc.)
- `min_len`, `max_len`: Domain prefix length range
- `has_number`: Only domains containing numbers
- `has_hyphen`: Only domains containing hyphens
- `is_alpha`: Only pure letter domains
- `is_digit`: Only pure numeric domains
- `keyword`: Filter domains containing this keyword
- `exclude_keywords`: Exclude domains containing these keywords

### count_domains
Count domains by type with filters.

**Required:**
- `type`: Data source (`nrds`, more coming soon)

**Optional:** Same filters as search_nrds

## Usage Tips
- "Find new .com domains starting with 'tech' registered last 7 days"
- "How many pure-letter domains with 'ai' were registered in the last 3 days?"
- "What domains are on ns1.google.com?"
- "Find 4-letter .com domains on ns1.registrar.com"

## Limits
- Results limited to 5 samples
- Direct users to domainkits.com for full data and download