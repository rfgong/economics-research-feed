Prepare my weekly economics research feed as a Yale Economics PhD student focused on Political Economy, Industrial Organization, and Environmental Economics. Optimize for intellectual expected value, not completeness.

DATE WINDOW
Use the immediately preceding Monday 01:01 AM through Monday 01:00 AM America/New_York. Treat a paper as new based on first public release/posting, not a routine revision. For arXiv use the v1 submission date.

PRIMARY SOURCES
1. NBER: complete set newly released in window.
2. CEPR: complete set newly released in window.
3. arXiv: targeted economics/econometrics/theory/statistics/ML searches; enforce v1 date.
4. Researcher websites: scan the canonical cached Top-20 roster for new working papers and WIP.

ROSTER DATA
The roster is external data, not part of this prompt. Before the website scan, load:
- `top20_economics_researchers.md`
- `top20_roster_state.json`

Treat those files as the source of truth. Do not reconstruct a missing roster from memory or from old chat state. If the roster cannot be loaded, continue the NBER/CEPR/arXiv layers and report `ERRORS — researcher roster unavailable; website/WIP layer not run`.

Each roster record contains researcher name, institution/unit, and one research URL. When a record points to an official unit page, follow a clearly identified personal/research-site link when available.

SEPTEMBER ROSTER REFRESH
On the first weekly run in September, refresh the full roster before the website scan unless `top20_roster_state.json` already shows `status=COMPLETE` and `last_verified` in the current September.

Institution set:
Harvard; MIT; Chicago; UC Berkeley; Stanford; Princeton; Yale; Oxford; NYU; Columbia; Toulouse/Toulouse Capitole; LSE; Penn; Northwestern; UCL; UCSD; UCLA; Brown; Michigan; Duke.

For each institution, include assistant professors or genuine non-US junior permanent/tenure-track equivalents. Include economics-based junior faculty in economics plus business, ARE/environmental, political science, public policy/government and similar units when their actual research is substantively economics-based. Exclude postdocs, visitors, teaching-only faculty, adjuncts, and temporary/research-assistant-professor positions.

Refresh sequentially. After EACH completed institution:
1. update and deduplicate the canonical roster;
2. update state with `status=INCOMPLETE`, `completed_institutions`, `next_institution`, and current verification date;
3. persist both files immediately.

Resume from the first incomplete institution after any interruption. Only after all 20 institutions are complete should state be replaced with `status=COMPLETE`, `completed_institutions` containing all 20, and `next_institution=null`. If persistence fails, report an error and do not claim the refresh is complete.

On ordinary runs, use the cached COMPLETE roster and only repair obvious dead URLs/redirects encountered during scanning.

SOURCE COVERAGE
NBER: use the official NBER database as discovery backbone, sort/query by release date, page as needed, cross-check official New This Week where available, and verify selected papers on individual NBER pages. If one official route fails, use alternative official NBER listing/query routes and sequential WP numbers where useful. Do not use third-party reposts/newsletters as the completeness backbone. Report an error only if complete coverage cannot reasonably be established.

CEPR: use official Discussion Paper listings/RSS/date filters; verify selected papers on CEPR pages; try alternate official CEPR routes before declaring incomplete.

arXiv: use official search/API/RSS as available; v1 date must be in window.

RELEVANCE
Prioritize Political Economy, IO, Environmental Economics, regulation, firms/government, energy, transportation, antitrust, platforms, state capacity, lobbying, and closely related topics.

Wildcard outside fields only if authors/work are strong AND there is direct or transferable economics research value: novel accessible large-sample data, portable method/identification, tractable reformulation, or unusually authoritative research-craft/profession material. Fame alone is insufficient; exceptional junior work may qualify.

SELECTION
Maximum 15 working papers total: Top Working Papers up to 5 ranked by expected value; Alternates up to 10. Do not pad. Deduplicate across sources and prefer the canonical version.

For each: Title; Authors; Source + first-release date; Abstract (verbatim only if user-provided/public domain/license permits; otherwise concise source-faithful summary of question/method-data/main finding with no invented interpretation); Why it matters (one concise sentence).

WORK IN PROGRESS
Up to 5 genuinely earlier-stage projects from tracked websites/CVs/research pages, outside the 15-paper cap. Include only if newly posted/announced/meaningfully newly described in the window, credibly active, clears the relevance threshold, and has no public manuscript. Once a manuscript appears, move it to the working-paper pool. Give title, researchers, available description without inference, evidence/stage, and one sentence on why it is worth watching. Do not pad.

OUTPUT
No broad audits, exhaustive lists, search diaries, or methodology boilerplate. Keep the feed compact and ranked. Prestige alone does not qualify.

ERRORS
Include terse notes at the end only for failed verification, incomplete source coverage, a key source unreachable/stale without an official workaround, unfinished annual roster refresh, roster unavailability, or roster persistence failure.
