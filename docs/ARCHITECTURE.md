# Architecture

## Overview
`src/main.py` is a single-file async Python 3.11 Apify Actor.

```text
Actor input (searchTerms, maxResults, detectTechStack)
  -> DuckDuckGo HTML search: "<term> myshopify.com store"
  -> per result: normalize domain, de-duplicate (seen_domains)
  -> fetch storefront HTML (httpx, 10s timeout, redirects followed)
  -> extract_emails / extract_socials / detect_apps
  -> GET /products.json?limit=250 (catalog signal, 7s timeout)
  -> Actor.push_data(lead_record)
```

## Components
| Function | Responsibility |
|---|---|
| `extract_emails` | Regex match, lower-case, drop image extensions, `sentry.io`, `wixpress.com` and placeholder domains |
| `extract_socials` | BeautifulSoup scan of `<a href>` for Instagram, Facebook, TikTok, LinkedIn, Twitter/X |
| `detect_apps` | Case-insensitive regex fingerprints from `APP_PATTERNS` |
| `check_shopify_products_catalog` | Counts products returned by `/products.json?limit=250` |
| `main` | Orchestration, limits, logging, dataset output |

## Design notes
- Stack: Python 3.11, Apify SDK, HTTPX (async), BeautifulSoup.
- Failures per store are swallowed so one bad site never stops the run.
- Catalog size is capped at 250 because only one `/products.json` page is read.
- Stores are processed sequentially, which keeps request volume polite.

See [APP-DETECTION.md](APP-DETECTION.md) and [API-REFERENCE.md](API-REFERENCE.md).
