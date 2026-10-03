# App Detection

Detection is a case-insensitive regex search over the storefront HTML. The first matching pattern per app wins.

| App | Fingerprints |
|---|---|
| Klaviyo | `klaviyo`, `static\.klaviyo\.com` |
| Yotpo | `yotpo`, `staticw2\.yotpo\.com` |
| Recharge | `recharge`, `rechargeassets\.com` |
| Gorgias | `gorgias`, `config\.gorgias\.chat` |
| Loox | `loox\.io`, `loox-images` |
| Judge.me | `judgeme`, `cdn\.judge\.me` |
| Zendesk | `zendesk`, `assets\.zendesk\.com` |
| Privy | `privy\.com`, `widget\.privy\.com` |
| Smile.io | `smile\.io`, `sweettooth` |

## Adding an app
Add an entry to `APP_PATTERNS` in `src/main.py` with specific script/CDN patterns, then add a test in `tests/test_extractor.py`.

## Limitations
Only the homepage HTML is inspected, so apps loaded lazily or on other pages may be missed. Generic words (e.g. `recharge`) can produce false positives.
