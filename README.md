# FirmenABC.at Scraper

Extract structured data from [FirmenABC.at](https://FirmenABC.at) — FirmenABC.at — Austria's largest business directory with 800,000+ companies. Includes full Jahresabschluss balance sheet, Firmenbuchnummer, and board members for each company. Incremental mode tracks changes across runs.

**[FirmenABC.at Scraper on Apify →](https://apify.com/blackfalcondata/firmenabc-at-scraper?fpr=1h3gvi)**

---

## Key features

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Result cap** — Stop after N listings. Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from FirmenABC.at on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from FirmenABC.at.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Lead generation**
Extract employer contact details alongside listings to build outreach lists for recruiters, staffing agencies, or B2B sales teams.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "maxResults": 10
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `startUrls` | array | — | Optional: provide specific FirmenABC.at company detail URLs to scrape directly (e.g. https://www.firmenabc.at/wien-holding-gmbh_ocT). Leave empty to discover all companies via sitemap. |
| `maxResults` | integer | `100` | Maximum number of companies to return. 0 = no limit (full sitemap crawl ~800k). Use a small number for testing. |
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

- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

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

*Last updated: 2026 04*
