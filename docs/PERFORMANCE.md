# Performance

No measured benchmarks are published here; figures depend on run conditions.

## What drives runtime
Per store the Actor makes up to 3 sequential requests (search result already fetched, storefront page ≤10s timeout, `/products.json` ≤7s timeout). Runtime therefore scales linearly with `maxResults`.

## Optimization tips
- Set `detectTechStack` to false to skip app regex matching (minor saving).
- Keep `maxResults` small for first runs, then scale up.
- Use Apify Proxy to reduce blocking.
- Possible improvements: concurrent store fetching with `asyncio.Semaphore`, paginating `/products.json`.

Measure your own runs from the Apify Console run statistics. See [../assets/performance-data.md](../assets/performance-data.md).
