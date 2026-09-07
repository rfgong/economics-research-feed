Refresh the canonical Top-20 economics researcher roster used by the weekly economics research feed.

FILES
Read and update:
- `top20_economics_researchers.md`
- `top20_roster_state.json`

Treat the repository versions on branch `main` as the source of truth. Do not reconstruct the roster from prior chat state.

INSTITUTION SET
Harvard; MIT; Chicago; UC Berkeley; Stanford; Princeton; Yale; Oxford; NYU; Columbia; Toulouse/Toulouse Capitole; LSE; Penn; Northwestern; UCL; UCSD; UCLA; Brown; Michigan; Duke.

INCLUSION RULE
For each institution, include assistant professors or genuine non-US junior permanent/tenure-track equivalents.

Include economics-based junior faculty in:
- economics;
- business schools;
- agricultural/resource/environmental economics;
- political science;
- public policy/government; and
- similar units

when their actual research is substantively economics-based.

Exclude:
- postdocs;
- visitors;
- teaching-only faculty;
- adjuncts;
- temporary positions; and
- research-assistant-professor or equivalent non-permanent positions.

URL RULE
For each researcher, store one URL using this preference order:
1. personal research site;
2. individual research/publications profile;
3. official individual faculty page;
4. official unit faculty page only as a fallback.

Do not add multiple URLs per researcher.

REFRESH PROCEDURE
Refresh institutions sequentially in the order listed above.

Before starting, read `top20_roster_state.json`.

If state is `INCOMPLETE`, resume from `next_institution`.
If state is `COMPLETE`, start again from Harvard for the annual refresh.

After EACH completed institution:
1. update and deduplicate `top20_economics_researchers.md`;
2. update `top20_roster_state.json` with:
   - `status=INCOMPLETE`;
   - the current verification date;
   - `completed_institutions`;
   - `next_institution`;
   - refreshed `records_by_institution`;
   - refreshed `records_total`;
3. persist both files immediately.

Only after all 20 institutions are complete should state be replaced with:
- `status=COMPLETE`;
- `completed_institutions` containing all 20 institutions;
- `next_institution=null`;
- the current verification date;
- final `records_by_institution`;
- final `records_total`.

If persistence fails, report the failure and do not claim the refresh is complete.

DEDUPLICATION
Deduplicate within and across units at the same institution. Prefer the research-relevant unit label when a researcher has multiple appointments. Do not remove a legitimate cross-field researcher merely because they also appear in economics or a business school.

OUTPUT
Keep the roster file compact: one researcher per line in the existing canonical format.

Do not produce a narrative audit. At the end, report only:
- completion status;
- institutions completed in this run;
- total canonical records; and
- any persistence or unresolved eligibility errors.
