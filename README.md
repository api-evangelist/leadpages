# Leadpages

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Leadpages is an AI web platform with built-in conversion optimization, part of the Redbrick family of
brands. It builds and hosts landing pages, multi-page sites and blogs that optimize themselves through
A/B testing, Smart Traffic variant routing, heatmaps, dynamic text replacement and personalization.

- Website: https://leadpages.com/
- Developer portal: https://leadpages.com/developers
- API documentation: https://leadpages.com/developers/docs
- MCP documentation: https://leadpages.com/developers/mcp

## API surface

| Surface | Endpoint | Auth | State |
|---|---|---|---|
| REST API | `https://api.leadpages.com` | Bearer `lp_` key, Pro plan and above | Documented; **host does not serve** (see below) |
| MCP server | `https://mcp.leadpages.com/mcp` | OAuth 2.0 + PKCE, all plans | Live, 47 documented tools, `tools/list` OAuth-gated |
| A2A agent | `https://leadpages.com/api/a2a` | OAuth 2.0 | Live, agent card published, 5 skills |
| Webhooks | dashboard-configured | — | Advertised; 3 event types named, no schemas published |

## Notes on this profile

**Leadpages publishes no OpenAPI of its own.** The document served at
`https://leadpages.com/openapi.json` returns 200 and parses as OpenAPI 3.1.0, but it describes
**HTML Pub** — a sibling brand on the same engine — with `servers[]` of `https://htmlpub.com`,
`hp_live_` key prefixes and `support@htmlpub.com` as contact. It is not the Leadpages API and nothing
in this repo is derived from it. See `conventions/leadpages-conventions.yml` for the full evidence.

**The documented REST base URL does not resolve to a working endpoint.** `api.leadpages.com` CNAMEs to
`ghs.googlehosted.com` and does not complete a TLS handshake, so the published REST quickstart cannot
be run as written. See `lifecycle/leadpages-lifecycle.yml`.

**The status page is provisioned but inactive.** `status.leadpages.com` redirects to
`leadpages.statuspage.io/inactive`.

What Leadpages does publish unusually well is its OAuth and agent discovery stack: RFC 8414
authorization-server metadata, RFC 9728 protected-resource metadata, PKCE, dynamic client
registration, an A2A agent card, and a substantive `llms.txt` with a machine-readable `pricing.md`.
