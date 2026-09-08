# Economics Research Feed

Persistent support files for the weekly ChatGPT economics research-feed automation.

## Architecture

The repository keeps deterministic source retrieval separate from model judgment.

GitHub Actions maintains small rolling caches for NBER Working Papers and a fixed arXiv economics/methods category universe. ChatGPT handles weekly date filtering, relevance ranking, CEPR retrieval, cross-source deduplication, research summaries, and a lightweight researcher-site/WIP early-warning layer.

The repository intentionally does not store weekly feed outputs or an emitted-paper ledger.

## Files

- `weekly_feed_prompt.md` — canonical weekly-feed instructions.
- `annual_roster_refresh_prompt.md` — separate annual roster-maintenance instructions.
- `top20_economics_researchers.md` — cached Top-20 junior-researcher roster.
- `top20_roster_state.json` — roster refresh status.
- `nber_recent.jsonl` — generated rolling NBER cache.
- `nber_recent_state.json` — NBER cache status.
- `arxiv_recent.jsonl` — generated rolling arXiv cache.
- `arxiv_recent_state.json` — arXiv cache status.
- `.github/workflows/refresh_nber_cache.yml` — refreshes NBER before the Monday feed.
- `.github/workflows/refresh_arxiv_cache.yml` — refreshes arXiv before the Monday feed.

## Weekly window

Each Monday feed covers the immediately preceding completed Monday through Sunday calendar week in `America/New_York`.

The source caches retain 14 days for resilience, but the feed filters them to the non-overlapping seven-day completed week. No emitted-ID ledger is used.

## NBER cache

The NBER cache is the NBER completeness backbone because direct NBER retrieval from the ChatGPT execution environment has proved unreliable. If the cache is stale or missing, the weekly feed reports incomplete NBER coverage rather than retrying known-unreliable routes.

## arXiv cache

The arXiv workflow queries the official arXiv API for:
`econ.EM`, `econ.GN`, `econ.TH`, `stat.ME`, `stat.AP`, `q-fin.EC`, `cs.GT`.

It stores a rolling 14-day cache with the initial-submission (`v1`) date, title, authors, categories, canonical URL, and abstract. arXiv descriptive metadata, including abstracts, is available under CC0 under the arXiv API terms.

## CEPR

CEPR remains model-side because its weekly Discussion Paper listing is comparatively lightweight to retrieve and does not require another cache unless reliability problems emerge.

## Researcher-site / WIP layer

The roster is an early-warning supplement, not an exhaustive weekly crawl. The feed does not re-audit roster URLs and does not claim week-to-week novelty without concrete recency evidence on the source page.

Annual roster maintenance is handled separately by `annual_roster_refresh_prompt.md`.

## Failure behavior

A failed cache refresh does not overwrite the last known-good cache. The Monday feed checks each cache state file. If a cache is stale or missing, the feed reports that source layer as incomplete and continues with the remaining sources.

## Maintenance

The repository is intentionally minimal. Do not add weekly feed outputs, emitted-ID ledgers, broad web-crawl state, or general research files here. Git history serves as the audit trail for source-cache and roster changes.
