# Research evidence

This file records the evidence behind each entry. The initial review was on 2026-11-07 (Europe/Vilnius); source 32 was added on 2026-11-08 (UTC), without re-reviewing earlier entries.

## Method and limits

- **How the sources were read**
  - Source text was fetched before drafting and supplied as untrusted data. Every fetch returned HTTP 200.
  - Instructions that appeared inside sources were ignored. Sources were only cited and evaluated.
- **What was not done**
  - No listed resource was installed, run or tested, in production or otherwise.
  - No benchmarks were run. No metrics in this list come from us.
  - No CI workflow or scheduled link checking exists.
- **Authorship:** the initial entries and notes were drafted with AI assistance from fetched source text, then approved for publication by the maintainer.
- **License:** source 25 is the complete CC0 1.0 legal text fetched directly from https://creativecommons.org/publicdomain/zero/1.0/legalcode.txt and copied unchanged into LICENSE. It was handled separately from the AI-assisted drafting.

## Included entries: 24 resources plus 2 related lists

| ID | Resource | Section | Status | Version / date observed | Coverage of fetched text | Why included |
|---|---|---|---|---|---|---|
| 11 | Plan tools (OpenAI) | Start Here | vendor docs | No date in text | Full page | Contract checklist covering inputs, outputs, auth, side effects and failure. The single OpenAI design guide chosen. |
| 1 | Writing effective tools for AI agents (Anthropic) | Start Here | guidance | Published 2025-09-11 (verified with original-page fetch) | Full article | Foundational tool-design principles plus an eval-driven loop. Results are internal and Claude-centric. |
| 31 | Tool search tool (Anthropic) | Discoverability & Context | vendor docs | Current docs read 2026-11-07; no stable publication date asserted | Full current documentation | Replaces the older beta launch article with implementation-level deferred-loading and metadata-search guidance. Vendor performance claims not repeated. |
| 17 | llms.txt | Discoverability & Context | proposal | v2 of a proposal first written in 2024 | Full page | Path-scoped index, markdown twins and link relations. The page's adoption claims are the author's and were not verified. |
| 6 | MCP Resources | Discoverability & Context | protocol spec | 2026-07-28 | Full page | URI-addressed context with templates, subscriptions and cache hints. |
| 12 | Optimize metadata (OpenAI) | Discoverability & Context | vendor docs | No date in text | Full page | Selection-focused metadata testing with a golden prompt set. |
| 26, 29 | Agent Payments Protocol (AP2) | Access & Identity | protocol spec, not universal standard | v0.2 | Landing page and complete specification read | Signed Checkout/Payment Mandates, deterministic verification, receipts, human-present and autonomous modes; explicit scope exclusions. |
| 7 | MCP Authorization | Access & Identity | protocol spec | 2026-07-28 | Full page; linked subpages on discovery, registration and security considerations not read | OAuth profile for HTTP MCP, including the deprecation of dynamic registration. |
| 8 | MCP Security Best Practices | Access & Identity | guidance | 2026-07-28 docs path | Full page | MCP-specific attacks and mitigations. |
| 19 | RFC 9700 | Access & Identity | standard (BCP 240) | January 2025 | §1–3 read; text truncated during §3, so the §4 attack details were not read | Current OAuth security baseline. Evergreen. |
| 18 | RFC 9728 | Access & Identity | standard (Standards Track) | April 2025 | §1–5 read; text truncated in the §5 flow; §7 security known only from the table of contents | Resource metadata discovery that MCP requires. Evergreen. |
| 15 | A2A Protocol Specification | Tools & Interfaces | protocol spec | 1.0.0 listed as latest release | §1–5 and the start of §6; later sections, including security, not read | Interface for products that are themselves agents. |
| 5 | MCP Tools | Tools & Interfaces | protocol spec | 2026-07-28 | Full page | Tool contracts, errors, state handles and structuredContent. The spec itself separates structuredContent from model-side structured outputs. |
| 28 | Understanding WCAG 2.2 SC 4.1.2 | Tools & Interfaces | guidance (the success criterion is normative; the Understanding document is informative) | WCAG 2.2; page updated 2026-11-02 | Full page | Accessibility-tree semantics. Relevance to agents is our inference. |
| 13, 14 | WebMCP (Chrome) | Tools & Interfaces | proposal | Docs published 2026-05-18 and updated 2026-10-07; origin trial post dated 2026-06-09 | Overview page and origin trial post; API subpages not read | Declared page tools in place of DOM actuation. Not a universal standard. |
| 21 | AIP-151 | Reliability & Recovery | guidance (approved AIP) | Created 2019-07-25; changelog runs to 2025-02-04 | Full page | Long-running operation pattern. |
| 16 | A2A: Life of a Task | Reliability & Recovery | protocol guide | Current latest documentation | Full page | Explicit task lifecycle, IDs, input-required and terminal outcomes; practical recovery interface rather than another general announcement. |
| 20 | Stripe: Idempotent requests | Reliability & Recovery | vendor docs | No page date; examples show Stripe-Version 2026-10-28.preview | Idempotency section read in full; adjacent sections ignored | A concrete safe-retry example. Not a universal guarantee. |
| 32 | [agent-qa](https://vostride.com) | Evaluation | tool | Official documentation read 2026-11-08; unversioned pages | [Overview](https://vostride.com/docs/agent-qa), quickstart prerequisites, README feature summary, [license](https://vostride.com/license.md) and [pricing](https://vostride.com/pricing.md); five official page fetches returned HTTP 200 | Runs natural-language product journeys through a QA agent, with persistent memidex memory, validated self-improvement and reviewable execution evidence. Relevance to agent usability is inferred; early-stage, FSL competing-use limits and external model/infrastructure costs. No runtime or benchmark executed. |
| 2 | Demystifying evals for AI agents (Anthropic) | Evaluation | guidance | Published 2026-01-09 (verified with original-page fetch) | Full article | Eval vocabulary, grader types and pass@k versus pass^k. |
| 22 | MCP Inspector | Evaluation | tool | Current README describes a v2 line; no version number relied on | README only; docs/ guides not read | Deterministic, model-free server checks. |
| 27 | Playwright ARIA snapshots | Evaluation | tool | No date in text | Full page | Regression tests for accessibility-tree structure. Relevance to agents is inferred. |
| 24 | τ-bench (tau2-bench) | Evaluation | benchmark | Current README describes τ-bench 2.0 and points to v1.0.1 for 1.x-comparable scores | README only | Policy, tools, tasks and simulated user as an eval template. |
| 30 | WebArena-Verified | Evaluation | benchmark | README announcements through 2026-02-02; current main read 2026-11-07 | Full original README | Audited web tasks, deterministic grading, network traces and offline replay. Maintainer quality claims are not independently replicated. |
| — | hmishra2250/awesome-agent-experience | Related Lists | related list | Public URL validated before drafting | README inspected in earlier research; not every outbound resource checked | Overlapping coverage, so the list makes no first-or-only claim. |
| — | alexngai/awesome-agent-experience | Related Lists | related list | Previously observed as archived; current state unconfirmed | README inspected in earlier research; not every outbound resource checked | As above. |

## Considered but not included

| ID | Resource | Reason |
|---|---|---|
| 4 | MCP 2026-07-28 specification overview | Accurate but general. The Tools, Resources and Authorization pages carry the actionable detail. Consulted for its security principles. |
| 10 | OpenAI function calling guide | Would make three OpenAI guides. It covers a generic model API, and its strict mode is model-side constrained generation rather than product AX. The fetched text was partial. |
| 14 | WebMCP origin trial post | Folded into the WebMCP entry as evidence for the trial start date. |
| 9 | MCP release announcement | Used to verify the July revision and migration context; excluded from main list in favor of actionable lifecycle documentation. |
| 3 | Anthropic advanced tool-use launch article | Read in full; replaced by current Tool search documentation to avoid carrying forward launch-era beta status. |
| 23 | WebArena-x | The fetched page is a project listing only. It benchmarks agents on simulated sites and offers little direct guidance for product teams. Specific project pages could be reconsidered. |

## Caveats

- **MCP versions**
  - 2026-07-28 is the latest revision observed.
  - It removes the initialize handshake and Mcp-Session-Id, replaces server-initiated requests with input-required round trips, and deprecates dynamic client registration, Roles, Sampling and Logging.
  - Older docs and tutorials, including 2025-11-25 and earlier, differ.
  - Entry URLs are pinned to 2026-07-28 and will not follow future revisions.
- **Structured data**
  - MCP structuredContent is server-produced. It is not LLM constrained generation.
  - Output schemas validate shape. They do not validate meaning or truth.
- **WebMCP**
  - A proposed web standard led by Chrome, available behind a flag and through an origin trial from Chrome 149.
  - The fetched Chrome docs describe a proposal/origin trial, not a W3C Recommendation or proof of cross-browser availability.
  - The docs say it is designed mainly for local, human-in-the-loop browsing.
- **llms.txt**
  - A v2 proposal, not a standard.
  - Its adoption and platform-support statements were not verified.
- **MCP Inspector and τ-bench**
  - Both repositories have changed substantially.
  - The notes reflect the current READMEs only and assume no other versions or features.
  - τ-bench 2.0 scores are not comparable with 1.x scores.
- **RFCs**
  - RFC 9700 and RFC 9728 are evergreen published documents.
  - MCP authorization also normatively cites an OAuth 2.1 Internet-Draft, which is not yet an RFC.
- **Stripe:** a vendor example. v1 and v2 behave differently, and keys can be pruned after 24 hours in v1. It is not a guarantee any other API provides.
- **Vendor and lab material**
  - Pages from Anthropic, OpenAI, Stripe, Google and Chrome describe their own platforms.
  - Internal metrics in those pages are not repeated in the annotations.
- **A2A:** the A2A site banner mentions joining the Agentic AI Foundation. This was not used as evidence.
- **Related lists:** overlapping lists exist, so this list makes no claim to be first or only.

## Verification inventory

Initial review: 31 original-source fetches (including CC0), all returned HTTP 200. Two related GitHub URLs were also resolved publicly. Source reads verify availability and support for annotations, not runtime correctness. A2A `/latest/` and unversioned vendor documentation can change; evidence reflects this review date.

Outstanding: no bespoke AX task suite run against a real product, no independent replication of vendor measurements, and no certification of standard adoption or security.

## Final link and artifact checks

Initial review: all 25 external README links were fetched again after final edits and returned HTTP 200. Every relative Markdown file link resolves. LICENSE is byte-identical to the CC0 legal text fetched as source 25. These are availability/consistency checks, not security or production tests. No workflow was created or enabled.
