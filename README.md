# Awesome AX

> A quality-first list of resources for building products that AI agents can use: find, understand, authenticate to, call, recover from, and be evaluated against.

**AX (agent experience)** here means the experience *agents* have when they use your product, site, API or service.

## Contents

- [Start Here](#start-here)
- [Discoverability & Context](#discoverability--context)
- [Access & Identity](#access--identity)
- [Tools & Interfaces](#tools--interfaces)
- [Reliability & Recovery](#reliability--recovery)
- [Evaluation](#evaluation)
- [Related Lists](#related-lists)

These topics are **out of scope**:

- the UX of humans chatting with agents
- general guides to building agents
- generative engine optimization (GEO) for AI search

The list is written equally for two audiences:

- **Designer-builders**, who shape interfaces, tool contracts and copy.
- **Infrastructure engineers**, who run protocols, identity and reliability.

Other lists cover overlapping ground (see [Related Lists](#related-lists)). This one aims to be short, annotated and explicit about limits.

## How to read entries

Each entry has a status label, a note on what problem it addresses and how, and its main limitation. The labels are:

- `standard`: published by a standards body (IETF, W3C).
- `protocol spec`: normative text of an open protocol. It binds only that protocol, at the version linked.
- `proposal`: draft, experimental or early-stage work that may change or never be widely adopted.
- `vendor docs`: one company's product documentation. Behaviour described there is specific to that platform.
- `guidance`: design or engineering advice from a lab, maintainer or platform team. It is not normative.
- `release notes`: an announcement of changes. The spec it announces governs.
- `tool` / `benchmark`: software you run.

Two distinctions recur throughout the list:

- **Schema correctness is not semantic correctness.** A tool call or result can match its JSON Schema and still be wrong.
- **MCP `structuredContent` is server-produced result data.** It is unrelated to model-side constrained generation, which some APIs call structured outputs or strict mode.

MCP pages older than the 2026-07-28 revision describe an initialize handshake and protocol sessions that this revision removed. Check which version a tutorial targets before following it.

Sources reviewed on 2026-11-07 (Europe/Vilnius). The notes describe what each source says. We did not production-test any listed resource. The initial entries were drafted with AI assistance from fetched source text. Per-entry evidence, rejected candidates and caveats are in [research-evidence.md](research-evidence.md).

## Start Here

Read both entries below, then follow the path that fits your role. Everyone should finish at Evaluation.

- **Designer-builders:** Tools & Interfaces, then Discoverability & Context, then Evaluation.
- **Infrastructure engineers:** Access & Identity, then Tools & Interfaces, then Reliability & Recovery, then Evaluation.

- [Plan tools (OpenAI plugin docs)](https://developers.openai.com/plugins/plan/tools) `vendor docs` — A worksheet for turning user outcomes into tool contracts: name, schemas, authorization, side effects and failure behaviour, with reads and consequential writes split by risk. Written for ChatGPT and Codex plugins, so its annotation and testing advice is platform-specific, though the contract checklist transfers.
- [Writing effective tools for AI agents (Anthropic)](https://www.anthropic.com/research/writing-tools-for-agents) `guidance` — Argues that agent tools should not mirror API endpoints. Instead, consolidate common workflows, namespace overlapping tools, return high-signal fields, paginate or truncate with guidance, and refine descriptions against evaluations. Grounded in Anthropic's internal tools and Claude; reported effects vary by model, so rerun the loop yourself.

## Discoverability & Context

- [llms.txt](https://llmstxt.org/) `proposal` — Proposes a small markdown index at a site or path, plus markdown twins of pages and link relations pointing to them, so agents follow a curated route instead of parsing HTML. Now a v2 community proposal, not a standard; agents need not read it, and a stale index misleads.
- [MCP 2026-07-28: Resources](https://modelcontextprotocol.io/specification/2026-07-28/server/resources) `protocol spec` — Defines how a server exposes readable context by URI, with templates, subscriptions, cache hints and audience or priority annotations, separate from callable tools. Normative for this revision only. Resources are application-driven, so whether a host surfaces them to the model is up to the client.
- [Optimize metadata (OpenAI plugin docs)](https://developers.openai.com/plugins/guides/optimize-metadata) `vendor docs` — Treats tool names, descriptions and parameter docs as product copy that drives tool selection. Recommends testing changes against labelled direct, indirect and negative prompts for precision and recall. Specific to ChatGPT and Codex; the method transfers better than the wording advice.
- [Tool search tool (Anthropic)](https://platform.claude.com/docs/en/agents-and-tools/tool-use/tool-search-tool) `vendor docs` — Shows how searchable names, descriptions and parameter metadata let agents discover deferred tool definitions without loading a whole catalog into context. Claude-specific; definitions still travel in every request, and poor search metadata can hide the right tool.

## Access & Identity

- [Agent Payments Protocol v0.2](https://ap2-protocol.org/ap2/specification/) `protocol spec` — Binds agent purchases to signed Checkout and Payment Mandates, with deterministic verification and receipts, so services can distinguish authorized delegation from inferred intent. An evolving, payments-specific protocol, not a universal identity standard; commerce APIs, agent-to-agent delegation and dispute procedures are outside its scope.
- [MCP 2026-07-28: Authorization](https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization) `protocol spec` — Specifies OAuth for HTTP-based MCP: resource metadata discovery, resource indicators, audience-checked tokens, scope challenges with step-up, and issuer validation. It prefers Client ID Metadata Documents while retaining deprecated dynamic registration for compatibility. Authorization is optional, stdio servers use environment credentials, and the spec normatively cites an OAuth 2.1 Internet-Draft.
- [MCP 2026-07-28: Security Best Practices](https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/security_best_practices) `guidance` — Maps MCP-specific attacks to mitigations: confused-deputy proxies, token passthrough, SSRF during OAuth discovery, guessable state handles, malicious local server commands, unsafe authorization URLs and over-broad scopes. Complements the normative spec; mitigations still require correct implementation and deployment.
- [RFC 9700: Best Current Practice for OAuth 2.0 Security](https://www.rfc-editor.org/rfc/rfc9700.txt) `standard` — An IETF Best Current Practice that updates OAuth 2.0's threat model. It covers exact redirect matching, PKCE, mix-up defences, sender-constrained and audience-restricted tokens, and least-privilege scopes. Protocol-generic and silent on agents; you must map its attacker model onto agent clients and tool servers yourself.
- [RFC 9728: OAuth 2.0 Protected Resource Metadata](https://www.rfc-editor.org/rfc/rfc9728.txt) `standard` — A standards-track JSON document that an API publishes at a well-known URL, optionally advertised via WWW-Authenticate. It names the API's authorization servers, scopes and token methods, and HTTP MCP servers must implement it. It describes configuration, not trustworthiness: clients still validate resource identifiers and guard against SSRF.

## Tools & Interfaces

- [Agent2Agent (A2A) Protocol Specification](https://a2a-protocol.org/latest/specification/) `protocol spec` — Lets independently built agents advertise skills in an Agent Card and exchange messages, tasks and artifacts over JSON-RPC, gRPC or HTTP. Supports streaming, push updates and explicit version negotiation. Relevant when your product is an agent that others delegate to; it complements rather than replaces a product’s tool interface.
- [MCP 2026-07-28: Tools](https://modelcontextprotocol.io/specification/2026-07-28/server/tools) `protocol spec` — Normative rules for listing and calling tools: naming, input and output schemas, server-produced `structuredContent`, and `isError` results that models can correct from, plus state-handle guidance. A matching output schema proves shape, not truth, and annotations from untrusted servers remain untrusted.
- [Understanding WCAG 2.2 SC 4.1.2: Name, Role, Value (W3C)](https://www.w3.org/WAI/WCAG22/Understanding/name-role-value.html) `guidance` — Explains the WCAG requirement to expose component names, roles, states and values programmatically. These semantics also support accessibility-tree-driven browser tools. This page is informative guidance for an accessibility standard, not an agent benchmark; the AX connection is our inference, and conformance alone does not ensure task success.
- [WebMCP (Chrome for Developers)](https://developer.chrome.com/docs/ai/webmcp) `proposal` — A proposed web standard that lets a page register tools through a JavaScript API or annotated HTML forms. An in-browser agent then calls declared functions instead of guessing at clicks. Available behind a Chrome flag and in an origin trial from Chrome 149; agents discover tools only by visiting the page.

## Reliability & Recovery

- [A2A: Life of a Task](https://a2a-protocol.org/latest/topics/life-of-a-task/) `guidance` — Explains task IDs, artifacts and explicit working, input-required and terminal states so clients can follow delegated work rather than infer completion from a chat response. A2A-specific explanatory documentation; task completion is not a substitute for verifying the underlying business outcome.
- [AIP-151: Long-running operations (Google)](https://google.aip.dev/151) `guidance` — An approved Google API rule for slow methods: return an operation that the client polls for progress metadata and an eventual result or error. Includes guidance on parallel requests and expiry. Written for Google's protobuf APIs; the pattern transfers, but its names and thresholds are conventions, not requirements elsewhere.
- [Stripe API: Idempotent requests](https://docs.stripe.com/api/idempotent_requests) `vendor docs` — A concrete safe-retry design: clients attach a unique key to writes, and retries return or complete the original outcome instead of repeating it. Mismatched parameters are rejected. These are Stripe's semantics, which differ between its v1 and v2 APIs and expire keys; other APIs make no such guarantee.

## Evaluation

- [Demystifying evals for AI agents (Anthropic)](https://www.anthropic.com/research/demystifying-evals-for-ai-agents) `guidance` — Vocabulary and a roadmap for agent evals: tasks, trials, graders, transcripts and outcomes. Covers grading end state over exact tool sequences, pass@k versus pass^k, balanced positive and negative cases, and reading transcripts. Framed around evaluating agents, so adapt it to ask whether agents succeed with your product.
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector) `tool` — Inspects MCP servers through a web UI, a scriptable CLI, a terminal UI and an experimental connection CLI, so you can list, call and assert before a model is involved. It tests protocol behaviour, not how agents choose tools. Its README warns of an unencrypted secrets-file fallback where no OS keychain exists.
- [Playwright: Snapshot testing (ARIA snapshots)](https://playwright.dev/docs/aria-snapshots) `tool` — Asserts a page's accessibility tree against a YAML template with partial, strict and regex matching, so regressions in names, roles and states fail a test. It checks structure, not agent task success, and carelessly accepted snapshot updates can hide bugs. The link to agent usability is our inference.
- [WebArena-Verified (ServiceNow)](https://github.com/ServiceNow/webarena-verified) `benchmark` — Provides audited web tasks and deterministic evaluators over agent responses and captured network traces, including offline replay. Useful for designing outcome-based usability tests for agent-operated sites. Its fixed simulated environments are not a certification of your product; adapt tasks and inspect real state changes.
- [τ-bench (sierra-research/tau2-bench)](https://github.com/sierra-research/tau2-bench) `benchmark` — Simulated customer-service domains that pair a policy, agent tools and tasks with a simulated user. A useful template for testing tool-backed products in realistic conversations. It ranks agents in fixed domains, not your product, and its README says 2.0 results are not comparable with 1.x.

## Related Lists

- [alexngai/awesome-agent-experience](https://github.com/alexngai/awesome-agent-experience) — An earlier collection of resources for building agent-friendly systems; overlaps this list’s scope.
- [hmishra2250/awesome-agent-experience](https://github.com/hmishra2250/awesome-agent-experience) — A broader annotated collection spanning discovery, tools, authorization, evaluation and human control.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Every pull request is reviewed by a maintainer. No automated link checking runs at present.

## License

The original text in this repository is dedicated to the public domain under CC0 1.0 (see [LICENSE](LICENSE)). Linked resources keep their own copyright, licenses and trademarks.
