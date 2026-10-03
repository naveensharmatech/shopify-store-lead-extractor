# API Reference

## Input
| Field | Type | Default | Description |
|---|---|---|---|
| `searchTerms` (required) | array | 4 niches | Niches/keywords to search |
| `maxResults` | integer (1–50000) | 100 | Maximum stores to extract |
| `detectTechStack` | boolean | true | Enable app detection |
| `proxyConfiguration` | object | Apify Proxy | Proxy options |

## Output (one dataset item per store)
| Field | Type |
|---|---|
| `storeName` | string |
| `domain`, `website` | string |
| `category` | string (search term) |
| `catalogSize` | integer (0–250) |
| `detectedApps` | string[] |
| `email` | string or null |
| `allEmails` | string[] |
| `socialLinks` | object: linkedin, facebook, instagram, tiktok, twitter |
| `source` | string |

Example: [../examples/output-samples.json](../examples/output-samples.json).
