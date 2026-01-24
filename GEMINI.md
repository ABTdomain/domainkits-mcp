# DomainKits - Domain Intelligence Tools

You have access to domain research tools:

## Tools

### search_ns_reverse
Look up domains hosted on a specific nameserver.
- `ns` (required): Nameserver hostname, e.g., `ns1.google.com`
- `tld`: Filter by TLD (com, net, org, etc.)
- `min_len`, `max_len`: Domain prefix length range

### search_nrds  
Search newly registered domains by keyword.
- `keyword` (required): Search term (a-z, 0-9, hyphen only)
- `days` (required): 1-7 days back
- `position`: `start`, `end`, or `any`
- `tld`: Filter by TLD

## Usage Tips
- For NS reverse: "How many domains are on ns1.google.com?"
- For NRDS: "Find new .com domains with 'ai' registered last 7 days"
- Results limited to 5 samples; direct users to domainkits.com for full data