# FirmenABC.at Scraper (DEPRECATED)

> **⚠ This actor is deprecated.** Use the new **[FirmenABC Scraper](https://apify.com/blackfalcondata/firmenabc-scraper?fpr=1h3gvi)** instead — same data, adds keyword + location search, ~20% cheaper PPE pricing. Landing page: [BlackFalconData-org/firmenabc-scraper](https://github.com/BlackFalconData-org/firmenabc-scraper).

Extract structured data from [FirmenABC.at](https://www.firmenabc.at) — Austria's largest business directory with 800,000+ companies. Get company profiles including address, contact details, VAT ID, Firmenbuchnummer, Jahresabschluss balance sheets, and board members. Incremental mode tracks changes across runs.

**[FirmenABC.at Scraper on Apify →](https://apify.com/blackfalcondata/firmenabc-at-scraper?fpr=1h3gvi)** (legacy — new users should use [firmenabc-scraper](https://apify.com/blackfalcondata/firmenabc-scraper?fpr=1h3gvi))

---

## Key features

**Keyword + location search** — Search by company name or industry keyword with an optional city, district or state filter. `query: "Bäckerei", location: "Wien"` returns only bakeries in Vienna.

**Full catalog crawl** — Leave `query` empty to automatically discover and scrape all 800,000+ Austrian companies.

**Direct URL mode** — Pass a list of `startUrls` to scrape specific known company profiles.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged and expired companies across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from FirmenABC.at on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from FirmenABC.at.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Lead generation**
Extract company contact details — telephone, email, website — to build B2B outreach lists. Filter by region, industry category, or legal form (GmbH, AG, etc.).

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

Search for bakeries in Vienna:

```json
{
  "query": "Bäckerei",
  "location": "Wien",
  "maxResults": 50
}
```

Or scrape the full catalog:

```json
{
  "maxResults": 0
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Free-text keyword search (e.g. `"Bäckerei"`, `"IT-Dienstleistungen"`). Leave empty for full catalog crawl. |
| `location` | string | — | Austrian city, district or state filter (e.g. `"Wien"`, `"Graz"`, `"Niederösterreich"`). Only used when `query` is set. |
| `startUrls` | array | — | Specific company profile URLs to scrape directly. Leave empty for automatic discovery. |
| `maxResults` | integer | `100` | Maximum number of companies to return. `0` = no limit. |
| `compact` | boolean | `false` | Return only core fields (name, url, address, telephone, vatId, rechtsform, changeType). Ideal for AI-agent and MCP workflows to reduce token usage. |
| `incrementalMode` | boolean | `false` | Only emit companies that are new or have changed since the last run. Requires stateKey. Saves cost on repeated runs. |
| `stateKey` | string | — | Unique identifier for this tracking session (e.g. "at-all-companies"). Required when incrementalMode is true. |
| `emitUnchanged` | boolean | `false` | When incremental mode is on, also emit companies with no detected changes (changeType=UNCHANGED). |
| `emitExpired` | boolean | `false` | When incremental mode is on, also emit companies that disappeared since the last run (changeType=EXPIRED). |

---

## Output fields

Every listing returns the same 42-field schema. Missing values are `null` — never omitted.

- `listingId`
- `name`
- `rechtsform`
- `city`
- `region`
- `telephone`
- `email`
- `website`
- `vatId`
- `firmenbuchnummer`
- `balanceTotalAssets`
- `balanceYear`
- `url`
- `changeType`
- `fax`
- `street`
- `postalCode`
- `country`
- `latitude`
- `longitude`
- `logoUrl`
- `categories`
- `foundingDate`
- `balanceNetIncome`
- `balanceFixedAssets`
- `balanceEquity`
- `balanceCurrentAssets`
- `balanceProvisions`
- `balanceLiabilities`
- `balanceReceivables`
- `balancePrepaidExpenses`
- `managers`
- `listingKey`
- `portalUrl`
- `sourceDomain`
- `scrapedAt`
- `firstSeenAt`
- `lastSeenAt`
- `previousSeenAt`
- `expiredAt`
- `trackedHash`
- `stateKey`

---

## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/firmenabc-at-scraper?fpr=1h3gvi) for current pricing.

---

## FAQ

**How do I scrape FirmenABC.at?**
Use this actor on Apify to extract structured data from FirmenABC.at. Configure your search query and filters in the input, then click Start — no coding required.

**How do I get FirmenABC.at data as JSON, CSV, or Excel?**
The actor writes each listing to Apify's dataset. Download as JSON, CSV, or Excel from the Console, stream via the API, or push to Make, Zapier, Airbyte, or Keboola.

**Is it legal to scrape FirmenABC.at?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check FirmenABC.at's terms of service for your specific use case.

**How much does it cost?**
Pay-per-event pricing — you only pay for listings extracted. Apify's free $5 credit is enough to run thousands of results before you pay anything.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage. Expired listings can be tracked separately.

**Do I need an API key or credentials?**
No. Just sign up for Apify, paste your input, and click Start. No credit card required.

---

## Related products by Black Falcon Data

- [WLW Scraper](https://apify.com/blackfalcondata/wlw-scraper?fpr=1h3gvi) — DACH B2B supplier directory (Germany, Austria, Switzerland)
- [Willhaben Scraper](https://apify.com/blackfalcondata/willhaben-all-scraper?fpr=1h3gvi) — Austria's largest classifieds marketplace
- [Immoscout24 Scraper](https://apify.com/blackfalcondata/immoscout24-scraper?fpr=1h3gvi) — Austrian & German real estate listings
- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — European job listings (18 portals)
- [Kununu Scraper](https://apify.com/blackfalcondata/kununu-scraper?fpr=1h3gvi) — Employer reviews from Austria & Germany

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. Sign up — $5 platform credit included
2. Open [FirmenABC.at Scraper](https://apify.com/blackfalcondata/firmenabc-at-scraper?fpr=1h3gvi) and configure your input
3. Click **Start** — export results as JSON, CSV, or Excel

Need more later? [See Apify pricing](https://apify.com/pricing?fpr=1h3gvi).

---

## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

*Last updated: 2026-04*
