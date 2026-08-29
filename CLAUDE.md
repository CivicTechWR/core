# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

`core` is CivicTechWR's organizational management repo. It holds no application code. Its job is to be the **register** — the durable, version-controlled record of how the organization works — for a volunteer group whose knowledge otherwise scatters across a website, a blog, a Discourse forum, 38 GitHub repos, and a Google Drive.

Everything here follows from one finding: CivicTechWR has five documentation surfaces and no rule about which one owns a given fact, so volunteers write wherever is easiest and the rest silently rots. See `wiki/Ownership-Model.md`.

## Layout

```
wiki/                source for the GitHub wiki — published automatically (see below)
marketing/archive/   point-in-time snapshots of published output; re-captured at season end
.github/workflows/publish-wiki.yml
```

## The wiki is generated — constraints that will bite

`wiki/` is mirrored to this repo's GitHub Wiki (`core.wiki.git`) on every push to `main` that touches `wiki/`. **Direct edits in the GitHub wiki UI are overwritten on the next merge.**

- **Flat namespace only.** GitHub wikis cannot nest. The workflow *fails* on any `.md` below `wiki/` depth 1. One file per page; the filename becomes the page title.
- **The wiki's default branch is `master`, not `main`,** and GitHub provides no way to change it — pushing a `main` branch succeeds but `HEAD` stays on `master` and the branch is ignored. Verified empirically. The workflow detects the branch at run time rather than assuming.
- **`[[wiki-links]]` only render inside `wiki/`.** In `README.md` or `marketing/`, use full URLs to `https://github.com/CivicTechWR/core/wiki/<Page-Name>`.
- The workflow refuses to publish if `wiki/` is missing, empty, or has no `Home.md` — `rsync --delete` would otherwise wipe the wiki in one bad merge.

## Verify before pushing

There is no build, test, or lint step. Run the same guards the workflow enforces, plus a link check:

```bash
# workflow guards
[ -f wiki/Home.md ] || echo "FAIL: no Home.md"
find wiki -mindepth 2 -name '*.md' | grep -q . && echo "FAIL: nested pages"
find wiki -maxdepth 1 -name '*.md' | wc -l

# dangling [[wiki-links]]
python3 -c "
import re,os,glob
pages={os.path.basename(f)[:-3] for f in glob.glob('wiki/*.md')}
bad=[(os.path.basename(f),m) for f in glob.glob('wiki/*.md') for m in re.findall(r'\[\[([^\]]+)\]\]',open(f).read()) if m not in pages]
print('dangling:', bad or 'none')"
```

To force a republish without a content change, run the **Publish Wiki** workflow from the Actions tab (`workflow_dispatch` is enabled).

## Editing `wiki/Process-Index.md` — recount afterwards

The Process Index is a table of every process and where it is defined, with a status marker per row (`✅` one home · `⚠️` several that agree · `❌` several that disagree · `📭` not written down).

**Adding, removing or re-marking a row invalidates five prose statements of those counts** — four in the Summary, one in the Marketing section. They have been wrong twice. Find them, then recount programmatically:

```bash
grep -nE '[0-9]+ processes\.|Not written down \| [0-9]+|(sixteen|seventeen|eighteen) gaps|accounts for [a-z]+ of the|of (fifteen|sixteen) processes' wiki/Process-Index.md
```


```bash
python3 -c "
import collections
c=collections.Counter(); per=collections.defaultdict(collections.Counter); sec=None
for l in open('wiki/Process-Index.md'):
    if l.startswith('## '): sec=l[3:].strip()
    if l.startswith('|'):
        x=[y.strip() for y in l.strip().strip('|').split('|')]
        if len(x)==3 and x[2] in ('✅','⚠️','❌','📭'): c[x[2]]+=1; per[sec][x[2]]+=1
print(dict(c), 'total', sum(c.values()))
print({s:dict(v) for s,v in per.items()})"
```

## The model the wiki encodes

Four ideas connect the pages. Changes that contradict them need a deliberate decision, not a silent edit.

**One owner per fact.** Each kind of fact has exactly one home; everywhere else links rather than restates. Luma owns event times, Discourse owns meeting notes and recaps, GitHub owns anything needing a review trail, Drive owns only what cannot legally leave it, the blog owns public narrative. `wiki/Ownership-Model.md`.

**Prefer fetching over stating.** `ctwr-web/_plugins/fetch_luma_event.rb` pulls the next hacknight from Luma at build time, which is why the website is the only surface whose meeting time is never wrong. That is the pattern to extend.

**Register vs. board.** The wiki holds the durable register; GitHub Projects hold what someone has actually picked up. Items graduate from `wiki/Remediation-Checklist.md` to a board — the checklist marks them *"On the board."* rather than duplicating the detail.

**One process, one pillar.** A process appears in exactly one Process Index section — the pillar *whose volunteer is holding the document at the moment they need it*. The Process Index arbitrates; the project board follows it.

## Project boards

Two, deliberately separate. Content work has publish dates and process work does not; in a shared queue the undated work always loses.

- **[Project 46 — Marketing](https://github.com/orgs/CivicTechWR/projects/46)** — content production: blog, social, photography, design assets, newsletter, Luma event pages.
- **[Project 47 — Process Management](https://github.com/orgs/CivicTechWR/projects/47)** — meta-work, typed by a chain: `Inventory → Policy → Process → Control → Remediation`, grouped into themes via sub-issues. Its rule is **no policy without a control** — every doc that drifted in the audit was a policy-like statement with nothing checking it.

Project 10 belongs to other contributors and is not ours to reorganize.

Board work needs `gh auth refresh -s project`. Views can be created and filtered via `createProjectV2View` / `updateProjectV2View`, but **group-by, sort-by and roadmap date fields are UI-only**. Roadmap views also reject `visibleFieldIds`.

## Data sources used by the audits

```bash
# Discourse — key in .env (gitignored). Send Api-Key with NO Api-Username header; adding one 403s.
curl -s -H "Api-Key: $DISCOURSE_API" https://discourse.ctwr.org/categories.json
curl -s -H "Api-Key: $DISCOURSE_API" https://discourse.ctwr.org/c/<slug>/<id>.json

# Luma — public ICS, no auth. Calendar feed is the superset of the user feed.
curl -s "https://api2.luma.com/ics/get?entity=calendar&id=cal-BVpgpDCgYaCqcPx"

# Bluesky — public, no auth
curl -s "https://public.api.bsky.app/xrpc/app.bsky.feed.getAuthorFeed?actor=civictechwr.bsky.social"
```

Instagram, Facebook and Threads are not retrievable without account access — the public pages are JavaScript shells. LinkedIn exposes roughly ten recent posts to logged-out requests. See `marketing/archive/README.md`.

**Measure recency by last *content* change, not `pushed_at`.** Two repos in this org look active in the GitHub listing while having had no content change in eleven months — the commits are deploy and CI churn. Use `gh api "repos/OWNER/REPO/commits?path=docs&per_page=5"`.

## Org constraint on GitHub Actions

The organization restricts Actions to GitHub-owned, Marketplace-verified, `peaceiris/*` and `ruby/*`. **A third-party action needs a policy exception.** `publish-wiki.yml` uses only `actions/checkout` plus plain `git` for this reason.

## Conventions

- Branch from `main`; PRs target `main`. Merging publishes the wiki.
- Write claims that can be checked, and check them. Nearly every finding in `wiki/Drift-Findings.md` came from measuring behaviour rather than reading documentation — the season doc says 12 weeks because someone wrote an ideal; the seasons are 15.
- When correcting a claim already published in the wiki, correct it in place and say so in the commit message. `Marketing.md` once asserted a recap cadence that the data contradicted.
