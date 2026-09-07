# Economics Research Feed

Persistent support files for the weekly ChatGPT economics research-feed automation.

## Files

- `weekly_feed_prompt.md` — canonical weekly-feed instructions.
- `annual_roster_refresh_prompt.md` — separate annual roster-maintenance instructions.
- `top20_economics_researchers.md` — cached Top-20 junior-researcher roster used for researcher-site and work-in-progress scans.
- `top20_roster_state.json` — machine-readable roster refresh status.
- `nber_recent.jsonl` — generated compact cache of recent NBER Working Paper metadata and abstracts.
- `nber_recent_state.json` — generated NBER cache status.
- `.github/workflows/refresh_nber_cache.yml` — refreshes the NBER cache before the Monday feed.

## Weekly automation contract

On ordinary weekly runs:

1. Read `weekly_feed_prompt.md`.
2. Load the current NBER cache and roster files named there.
3. Use the cached NBER file as the NBER completeness backbone.
4. Use the cached researcher roster for the lightweight researcher-website/WIP scan.
5. Do not rebuild or re-audit the roster during the weekly feed.

If the NBER cache is missing or stale, report incomplete NBER coverage and continue the other source layers. Do not substitute direct NBER fetch routes that are known to be unreliable in the ChatGPT execution environment.

If the researcher roster is unavailable, continue the NBER, CEPR, and arXiv layers and report that the researcher-website/WIP layer could not run.

## NBER cache

The GitHub Actions workflow downloads NBER's public machine-readable `ref.tsv` and `abs.tsv`, validates the response, and writes a compact 14-day cache containing Working Paper number, authors, title, issue date, DOI, and abstract.

The workflow runs early Monday before the 08:00 America/New_York feed and may also be triggered manually. A failed download or validation stops the workflow before the previous cache is overwritten.

The generated cache is source infrastructure, not a weekly feed output.

## Roster maintenance

Roster maintenance is separate from the weekly feed. Use `annual_roster_refresh_prompt.md` for the annual refresh.

The roster covers junior permanent or tenure-track economics researchers at:

Harvard; MIT; Chicago; UC Berkeley; Stanford; Princeton; Yale; Oxford; NYU; Columbia; Toulouse/Toulouse Capitole; LSE; Penn; Northwestern; UCL; UCSD; UCLA; Brown; Michigan; Duke.

Relevant economics-based junior faculty in business schools, agricultural/resource economics, political science, public policy/government, and closely related units are included when their substantive research is clearly economics-based.

## Maintenance

The repository is intentionally minimal. Do not add weekly feed outputs or general research files here. Git history serves as the audit trail for roster and cache changes.
