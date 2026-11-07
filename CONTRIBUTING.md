# Contributing

This list stays small on purpose. Suggestions are assessed editorially, not automatically accepted.

## Scope

**In scope:** resources that help make products usable *by* agents. The sections are Discoverability & Context, Access & Identity, Tools & Interfaces, Reliability & Recovery and Evaluation.

**Out of scope:**

- the UX of humans chatting with agents
- general agent-building guides or frameworks
- GEO and AI-search optimization
- launch posts, listicles and directories

## What an entry needs

1. **Relevance:** the AX problem the resource addresses, and the mechanism it uses.
2. **Evidence:** what the source itself says that supports your note. Do not invent metrics, testing, dates or adoption.
3. **Limitations:** at least one honest limitation, such as scope, maturity, vendor specificity or schema-versus-semantics gaps.
4. **Primary source:** a link to the original from the maintainer, standards body, lab or vendor. Do not link a summary, mirror or aggregator.
5. **Status and version:** one label from `standard`, `protocol spec`, `proposal`, `vendor docs`, `guidance`, `release notes`, `tool` or `benchmark`. Name the version or date you reviewed, and state plainly whether it is a standard or a proposal.
6. **Current link:** a resolving URL for current documentation, or an explicit version when reproducibility matters. If versions differ materially, say so.
7. **Affiliation disclosure:** any relationship you have with the resource, such as author, maintainer, employer, client, investor or sponsor. Affiliated entries are welcome if you disclose the relationship.

There are no star thresholds and no hard maturity cutoff. Experimental work can qualify if it is labelled `proposal` and its limits are stated.

## Writing the annotation

- Write one or two sentences, about 40–60 words at most: first the need and mechanism, then the limitation.
- Use your own words. Do not paste excerpts or marketing copy.
- Describe vendor behaviour as vendor-specific, not as universal.
- Insert the entry alphabetically by link text within its section. Non-Latin first characters sort by transliteration, so τ sorts as tau.
- Submit one resource per PR unless two resources are tightly related.

## Review

- A maintainer reviews every PR by checking the source against your note. Approval is a judgement call, not a checklist.
- Links are checked by hand during review. No automated or scheduled link checking exists yet.
- Entries may be revised or removed when their sources change, break or drift out of scope.
- AI-assisted contributions are welcome if you disclose them and have checked the note against the source yourself.
- AI-generated submissions get no special treatment, and acceptance is never guaranteed. The same applies when this list is proposed to other directories.

## Evidence log

For each new entry, add a row to [research-evidence.md](research-evidence.md). The row records the resource's status, the date or version you observed, which parts you read, and why it belongs. If you are unsure how to do this, describe it in the PR and a maintainer will add the row.

## Licensing

Original text you contribute is dedicated to the public domain under CC0 1.0 (see LICENSE). Linked materials keep their own copyright, licenses and trademarks; CC0 does not apply to them.
