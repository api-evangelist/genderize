# Genderize.io

Free REST API that predicts the gender of a first name with probability scores based on name statistics from millions of users worldwide. Part of the Demografix suite alongside Agify (age prediction) and Nationalize (nationality prediction), sharing a single API key across all three services.

- **Human URL:** https://genderize.io
- **Base URL:** https://api.genderize.io

## Description

Genderize.io accepts first names and returns gender predictions (male, female, or null) along with a probability score (0–1) and a sample count reflecting how many people in the dataset bear that name. The underlying dataset covers over one billion people. The API supports single-name lookups, batch requests of up to 10 names per call, and country-scoped lookups using ISO 3166-1 alpha-2 country codes for improved accuracy with regionally ambiguous names.

## Links

- **Website:** https://genderize.io
- **Documentation:** https://genderize.io/documentation
- **API Reference:** https://genderize.io/documentation/api/reference
- **Pricing:** https://genderize.io/pricing
- **FAQ:** https://genderize.io/faq
- **Login / API Key:** https://genderize.io/login
- **Status Page:** https://status.genderize.io
- **X (Twitter):** https://x.com/genderizeio
- **GitHub:** https://github.com/genderize
- **LinkedIn:** https://www.linkedin.com/company/demografix

## API Endpoint

**GET** `https://api.genderize.io?name={name}`

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `name` | Yes | First name to predict gender for |
| `name[]` | No | Array of up to 10 names for batch requests |
| `country_id` | No | ISO 3166-1 alpha-2 country code for localized prediction |
| `apikey` | No (Free) / Yes (Paid) | API key from account dashboard |

### Example Response

```json
{
  "name": "james",
  "gender": "male",
  "probability": 0.99,
  "count": 1234567
}
```

### Response Headers

| Header | Description |
|--------|-------------|
| `X-Rate-Limit-Limit` | Total monthly name allowance |
| `X-Rate-Limit-Remaining` | Names remaining in current window |
| `X-Rate-Limit-Reset` | Seconds until allowance resets |

## Authentication

Free-tier requests require no API key. Paid accounts use an `apikey` query parameter obtained from the account dashboard. The same API key works across all three Demografix services (Genderize, Agify, Nationalize).

## Pricing

| Plan | Price | Names/Month |
|------|-------|-------------|
| Free | $0/month | 2,500 |
| Standard | $60/month | 250,000 |
| Enterprise | Custom | 25,000,000+ |

Annual billing saves approximately 17% (two months free). No overage charges — requests return HTTP 429 once the monthly quota is exhausted.

## Rate Limits

The service does not apply per-second or per-minute rate limits. All limits are monthly name-allowance caps. Names are counted individually regardless of whether sent singly or in batches. Unused allowances do not roll over.

## Related APIs

- **Agify.io** — Age prediction from first names: https://agify.io
- **Nationalize.io** — Nationality prediction from first names: https://nationalize.io

---

*This profile is maintained by [Kin Lane](mailto:kin@apievangelist.com) as part of the [API Evangelist](https://apievangelist.com) catalog.*
