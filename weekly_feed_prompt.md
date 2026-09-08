Prepare my weekly economics research feed as a Yale Economics PhD student focused on Political Economy, Industrial Organization, and Environmental Economics. Optimize for intellectual expected value, not completeness.

DATE WINDOW
Use the immediately preceding completed Monday through Sunday calendar week in America/New_York.

For date-only sources such as NBER `issue_date` and CEPR release dates, use those seven calendar dates inclusively. For arXiv use `v1_date_et`. Treat a paper as new based on first public release/posting, not a routine revision.

PRIMARY SOURCES
1. NBER: complete weekly batch from the canonical GitHub cache.
2. CEPR: complete set of Discussion Papers newly released in the completed week.
3. arXiv: complete weekly batch within the canonical cached category universe.
4. Researcher websites: lightweight, best-effort early-warning layer for relevant new manuscripts and WIP.

CANONICAL DATA
Load from the repository:
- `nber_recent.jsonl`
- `nber_recent_state.json`
- `arxiv_recent.jsonl`
- `arxiv_recent_state.json`
- `top20_economics_researchers.md`
- `top20_roster_state.json`

Treat these repository files as the source of truth. Do not reconstruct missing caches or the roster from prior chat state.

NBER
Use `nber_recent.jsonl` as the NBER completeness backbone. Use it only if `nber_recent_state.json` has `refreshed_date_et` equal to the current Monday run date. Filter `issue_date` to the completed Monday-Sunday week and screen the complete resulting batch for relevance.

Do not attempt direct NBER metadata, Working Papers listing, New This Week, or individual-paper-page fetches as recovery paths; those routes are not reliable in this execution environment.

If the NBER cache is missing or stale, report:
`ERRORS — NBER coverage incomplete; canonical GitHub cache missing or stale`
and continue the other source layers.

For an NBER paper that would otherwise be selected, exclude it if a quick title/author check clearly establishes that the same manuscript was publicly available before the completed week. Do not perform this check for every NBER candidate.

ARXIV
Use `arxiv_recent.jsonl` as the arXiv completeness backbone for:
`econ.EM`, `econ.GN`, `econ.TH`, `stat.ME`, `stat.AP`, `q-fin.EC`, `cs.GT`.

Use it only if `arxiv_recent_state.json` has `refreshed_date_et` equal to the current Monday run date. Filter `v1_date_et` to the completed Monday-Sunday week. Do not rerun broad arXiv searches during an ordinary weekly feed.

If the arXiv cache is missing or stale, report:
`ERRORS — arXiv coverage incomplete; canonical GitHub cache missing or stale`
and continue the other source layers.

CEPR
Use an official CEPR Discussion Paper listing, RSS feed, weekly notice, or date-filtered page to identify the complete set newly released in the completed Monday-Sunday week. If the primary official route fails, try one alternate official CEPR route before reporting incomplete coverage.

RESEARCHER WEBSITE / WIP LAYER
The roster is a best-effort early-warning supplement, not a completeness-critical source. Treat roster URLs and affiliations as already verified. Do not re-audit them and do not attempt to crawl every roster researcher each week.

Prioritize researchers and pages with the strongest direct relevance to the feed. Surface a researcher-site manuscript or WIP only when the page itself supplies credible evidence that the item is recent or actively developing, such as a dated posting, dated CV update, explicit "new" or "work in progress" label, recent presentation information, or another concrete recency signal. Without a stored historical baseline, do not claim that an item is newly posted merely because it appears on the current page.

If the roster cannot be loaded, report:
`ERRORS — researcher roster unavailable; website/WIP layer not run`
and continue NBER/CEPR/arXiv.

RELEVANCE
Prioritize Political Economy, IO, Environmental Economics, regulation, firms/government, energy, transportation, antitrust, platforms, state capacity, lobbying, and closely related topics.

Wildcard outside fields only if authors/work are strong AND there is direct or transferable economics research value: novel accessible large-sample data, portable method/identification, tractable reformulation, or unusually authoritative research-craft/profession material. Fame alone is insufficient; exceptional junior work may qualify.

SELECTION
Maximum 15 working papers total:
- Top Working Papers: up to 5, ranked by expected value.
- Alternates: up to 10.

Do not pad. Deduplicate across sources and prefer the earliest/canonical public version.

For each selected paper give:
- Title
- Authors
- Source + first-public-release date
- Research summary
- Why it matters: one concise sentence
- Canonical paper/source link when available

ABSTRACT / SUMMARY RULE
For arXiv candidates, the cached API abstract is descriptive metadata released under CC0; reproduce it verbatim when useful.

For NBER and CEPR, do not reproduce a full abstract verbatim in the ChatGPT response. Give a compact source-faithful summary that preserves the question, identification or method, data, and principal finding when those elements are available. Do not invent interpretation.

This NBER rule is provisional pending clarification of reuse permissions for complete abstracts in the public repository.

WORK IN PROGRESS
Up to 5 genuinely earlier-stage projects from the researcher-site layer, outside the 15-paper cap. Include only when credibly active, relevant, and no public manuscript is available. Give:
- Title
- Researchers
- Available description without inference
- Evidence/stage
- Why it is worth watching: one concise sentence

Do not pad and do not imply exhaustive WIP coverage.

OUTPUT
No opening quote.
No broad audits, exhaustive lists, search diaries, or methodology boilerplate.
Keep the feed compact and ranked.
Prestige alone does not qualify.

ERRORS
Include terse notes at the end only when:
- the NBER cache is missing or stale;
- CEPR coverage cannot be established;
- the arXiv cache is missing or stale;
- the researcher roster cannot be loaded; or
- another source layer fails entirely.

Do not report routine inaccessible individual researcher pages, ordinary redirects, or the expected incompleteness of the best-effort WIP layer.
