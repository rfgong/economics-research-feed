Prepare my weekly economics research feed as a Yale Economics PhD student focused on Political Economy, Industrial Organization, and Environmental Economics. Optimize for intellectual expected value, not completeness.

DATE WINDOW
Use the immediately preceding Monday 01:01 AM through Monday 01:00 AM America/New_York. Treat a paper as new based on first public release/posting, not a routine revision. For arXiv use the v1 submission date.

PRIMARY SOURCES
1. NBER: complete set newly released in window.
2. CEPR: complete set newly released in window.
3. arXiv: targeted economics/econometrics/theory/statistics/ML searches; enforce v1 date.
4. Researcher websites: lightweight scan of the canonical cached Top-20 roster for newly posted working papers and WIP.

ROSTER DATA
The roster is external data, not part of this prompt. Before the website scan, load:
- `top20_economics_researchers.md`
- `top20_roster_state.json`

Treat those files as the source of truth. Treat roster URLs and affiliations as already verified; do not re-audit them during an ordinary weekly run.

If the roster cannot be loaded, continue the NBER/CEPR/arXiv layers and report:
`ERRORS — researcher roster unavailable; website/WIP layer not run`

The weekly feed does not rebuild the roster. Annual roster maintenance is handled separately by `annual_roster_refresh_prompt.md`.

RESEARCHER WEBSITE SCAN
Use the URL in each canonical roster record as the starting point. Inspect that page for newly posted working papers, research, publications, CV entries, or WIP. When the roster URL is an official unit page, follow at most one clearly identified personal/research/CV/publications link when needed.

Keep this layer lightweight:
- do not re-verify affiliation, rank, or URL validity;
- do not run separate search-engine queries for each researcher;
- do not crawl a site beyond the starting page plus one clearly relevant linked page;
- follow manuscript/project links only when needed to determine whether a candidate qualifies;
- repair an obviously broken roster URL only if encountered naturally.

This is an early-warning supplement, not a completeness-critical bibliographic source. Do not report an error merely because an individual researcher page is inaccessible or ambiguous.

SOURCE COVERAGE
NBER: load `nber_recent.jsonl` and `nber_recent_state.json` from the canonical repository. The cache is generated from NBER's official `ref.tsv` and `abs.tsv` metadata and is the NBER completeness backbone for this feed.

Use the cache only if `refreshed_date_et` is on or after the Monday that ends the feed window. Filter cached `issue_date` to the feed window and screen the complete resulting NBER batch for relevance. The cached title, authors, issue date, DOI, and abstract are sufficient for NBER discovery and description.

Do not attempt direct NBER metadata, Working Papers listing, New This Week, or individual-paper-page fetches as a recovery path; those routes are not reliable in this execution environment. If the cache is missing or stale, report `ERRORS — NBER coverage incomplete; canonical GitHub cache missing or stale` and continue the other source layers.

For an NBER paper that would otherwise be selected, exclude it if a quick title/author check clearly shows that the same manuscript was publicly available before the feed window; do not perform this check for every NBER candidate.

CEPR: use an official CEPR Discussion Paper listing, RSS feed, or date-filtered page to identify the complete set newly released in the window. Verify only papers selected for the final feed on their CEPR pages. If the primary official route fails, try one alternate official CEPR route before reporting incomplete coverage.

arXiv: use official search/API/RSS as available; v1 date must be in window. Keep searches targeted to economics/econometrics/theory/statistics/ML topics with plausible economics research value.

RELEVANCE
Prioritize Political Economy, IO, Environmental Economics, regulation, firms/government, energy, transportation, antitrust, platforms, state capacity, lobbying, and closely related topics.

Wildcard outside fields only if authors/work are strong AND there is direct or transferable economics research value: novel accessible large-sample data, portable method/identification, tractable reformulation, or unusually authoritative research-craft/profession material. Fame alone is insufficient; exceptional junior work may qualify.

SELECTION
Maximum 15 working papers total: Top Working Papers up to 5 ranked by expected value; Alternates up to 10. Do not pad. Deduplicate across sources and prefer the canonical version.

For each:
- Title
- Authors
- Source + first-release date
- Abstract: verbatim block quote preferred; otherwise a source-faithful summary of question, method/data, and main finding with no invented interpretation
- Why it matters: one concise sentence

WORK IN PROGRESS
Up to 5 genuinely earlier-stage projects from tracked websites/CVs/research pages, outside the 15-paper cap. Include only if newly posted, announced, or meaningfully newly described in the window; credibly active; relevant; and no public manuscript is available. Once a manuscript appears, move it to the working-paper pool.

Give:
- Title
- Researchers
- Available description without inference
- Evidence/stage
- Why it is worth watching: one concise sentence

Do not pad.

OUTPUT
No opening quote.
No broad audits, exhaustive lists, search diaries, or methodology boilerplate.
Keep the feed compact and ranked.
Prestige alone does not qualify.

ERRORS
Include terse notes at the end only when:
- NBER or CEPR coverage cannot be established;
- the arXiv layer fails materially;
- the researcher roster cannot be loaded; or
- another source layer fails entirely.

Do not report routine inaccessible individual researcher pages, ordinary redirects, or verification checks that are unnecessary to producing the feed.
