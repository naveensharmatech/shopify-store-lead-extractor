# Shopify Lead Extractor Architecture

## System Design

```
Search Input
    ↓
Shopify Store Discovery (DuckDuckGo)
    ↓
Web Fetch (HTTPX + BeautifulSoup)
    ↓
Email Pattern Detection (Regex)
    ↓
App Fingerprinting (Frontend signals)
    ↓
Catalog Analysis (Product endpoints)
    ↓
Deduplication
    ↓
Apify Dataset Output
```

## Tech Stack

- **Python 3.11** - Core language
- **Apify SDK** - Actor runtime
- **BeautifulSoup4** - HTML parsing
- **HTTPX** - Async HTTP requests
- **DuckDuckGo API** - Search backend

## App Detection Patterns

- Klaviyo, Yotpo, Recharge
- Gorgias, Loox, Judge.me
- Zendesk, Privy, Smile.io
