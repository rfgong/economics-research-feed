# Economics Research Feed

Persistent support files for the weekly ChatGPT economics research-feed automation.

## Files

- `weekly_feed_prompt.md` — canonical automation instructions.
- `top20_economics_researchers.md` — cached Top-20 junior-researcher roster used for researcher-site and work-in-progress scans.
- `top20_roster_state.json` — machine-readable refresh status and checkpoint metadata.

## Automation contract

The scheduled feed should treat this repository as the canonical persistent store for the researcher roster.

On ordinary weekly runs:

1. Read `weekly_feed_prompt.md`.
2. Read `top20_roster_state.json`.
3. If the roster state is `COMPLETE`, use `top20_economics_researchers.md` for the researcher-website scan.
4. Repair obvious dead or redirected research URLs when encountered and persist the correction when repository writes are available.

On the first weekly run in September:

1. Refresh all 20 institutions using the inclusion rules in `weekly_feed_prompt.md`.
2. Persist the roster and state after each completed institution.
3. Keep state `INCOMPLETE` until all 20 institutions are finished.
4. Set state to `COMPLETE` only after the full roster has been refreshed and deduplicated.

If repository access is unavailable, the automation should still run the NBER, CEPR, and arXiv layers and report that the researcher-website/WIP layer could not run.

## Scope

The roster covers junior permanent or tenure-track economics researchers at:

Harvard; MIT; Chicago; UC Berkeley; Stanford; Princeton; Yale; Oxford; NYU; Columbia; Toulouse/Toulouse Capitole; LSE; Penn; Northwestern; UCL; UCSD; UCLA; Brown; Michigan; Duke.

Relevant economics-based junior faculty in business schools, agricultural/resource economics, political science, public policy/government, and closely related units are included when their substantive research is clearly economics-based.

## Maintenance

The repository is intentionally minimal. Do not add weekly feed outputs or general research files here. Git history serves as the audit trail for roster changes.
