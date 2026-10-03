# Setup

## Local
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
mkdir -p storage/key_value_stores/default
echo '{"searchTerms":["Beauty & Cosmetics"],"maxResults":5,"detectTechStack":true}' \
  > storage/key_value_stores/default/INPUT.json
python -m src.main
```
Results are written to `storage/datasets/default/`. Tests: `pytest tests/`.

## Apify deployment
```bash
npm i -g apify-cli
apify login
apify push
```
The Actor uses `.actor/actor.json`, `.actor/input_schema.json` and the `Dockerfile`.
Live Actor: https://apify.com/opility/shopify-store-lead-extractor-emails-catalog-size-apps

See also [../DEPLOYMENT.md](../DEPLOYMENT.md) and [TROUBLESHOOTING.md](TROUBLESHOOTING.md).
