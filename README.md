# Genderize.io

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
