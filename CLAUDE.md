# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

`core` is CivicTechWR's organizational management repo. It holds no application code. Its job is to be the **register** — the durable, version-controlled record of how the organization works — for a volunteer group whose knowledge otherwise scatters across a website, a blog, a Discourse forum, 38 GitHub repos, and a Google Drive.

Everything here follows from one finding: CivicTechWR has five documentation surfaces and no rule about which one owns a given fact, so volunteers write wherever is easiest and the rest silently rots. See `01 - Evergreen/Ownership-Model.md`.

## Layout — this repo is an Obsidian vault

The repo root is the vault. Folder names have spaces and a numeric prefix; **quote every path**.

```
01 - Evergreen/      the register — published as the docs site (see below); index.md is the landing page
02 - Attachments/    data snapshots, exports, PDFs that notes point at; not notes
03 - Templates/      unique.md
site/                quartz.config.yaml (site build) and wiki-stub.md (retired wiki's one page)
.obsidian/           vault config, committed (workspace.json is gitignored — per-machine UI state)
.github/workflows/deploy-site.yml    build 01 - Evergreen/ with Quartz, deploy to Pages
.github/workflows/retire-wiki.yml    one-shot, manual: point the old wiki at the site
```

**Every note carries frontmatter**, matching `03 - Templates/unique.md`:

```yaml
---
title: "Ownership Model"   # published notes only; drives the tab, sidebar and search
date: "YYYY-MM-DD"
status: current            # draft | current | archived — metadata only, the site ignores it
tags:
references:
---
```

`02 - Attachments/` holds files, not notes — no frontmatter there. Property types are declared in `.obsidian/types.json` (`date`, `status` text, `tags`, `references`/`files` multitext); adding a new property means adding it there too.

**Drafts are branches, not folders.** There is no Inbox or Incubation stage: Obsidian's unique-note command creates notes straight in `01 - Evergreen/` (named `YYYYMMDDHHmm` — rename to `Title-Case.md` before merging), daily notes are off, and pasted files land in `02 - Attachments/`. Work on a branch; a draft PR is the draft. **Merging to `main` is the act that publishes**, so nothing unfinished may be merged into `01 - Evergreen/`.

## The site is generated — constraints that will bite

`01 - Evergreen/` is built with [Quartz](https://quartz.jzhao.xyz) v5 and deployed to GitHub Pages at **https://civictechwr.github.io/core** on every push to `main` that touches it. `.github/workflows/deploy-site.yml`.

- **`01 - Evergreen/index.md` is the landing page.** Quartz serves it at `/`. Renaming it 404s the site root; the workflow fails the build rather than let that ship.
- **Quartz is pinned to a commit, not vendored.** The workflow clones `jackyzha0/quartz` at `QUARTZ_REF` and copies `site/quartz.config.yaml` plus the notes into that checkout. Upgrading = bump the SHA **and** re-read our config against the new `quartz.config.default.yaml`, because v5's config is a plugin list that upstream changes.
- **Config is `quartz.config.yaml` read from `process.cwd()`** — that is why the workflow copies it into the Quartz clone rather than passing a path.
- **`analytics: null` is deliberate.** Quartz's default template enables Plausible; leave it off.
- **Only `01 - Evergreen/` is published.** `02 - Attachments/` is not copied into the build, so `![[image.png]]` embeds render in Obsidian and are missing on the site.
- **Published notes carry `title:`** on top of the four template properties. Without it Quartz falls back to the filename and the tab reads `Process-Index`. The `article-title` plugin is disabled because every note already opens with its own H1 — enabling it renders two titles.
- **Nesting is allowed now.** The old GitHub Wiki forbade it; Quartz does not. Anything in this repo still asserting a flat namespace is stale.
- **Actions policy still binds.** The org allows GitHub-owned, Marketplace-verified, `peaceiris/*` and `ruby/*`. Every action in `deploy-site.yml` is `actions/*`, which is what made Quartz viable where most publishing options were not.
- **`npx quartz plugin install` fetches `@quartz-community/*` at build time.** Those are not pinned by our SHA. A plugin change upstream can change the site without a commit here.

The GitHub Wiki was retired on **2026-08-30**. `.github/workflows/retire-wiki.yml` is a one-shot, `workflow_dispatch`-only job that replaces every wiki page with `site/wiki-stub.md`. Run it once after the site is confirmed live, then it can be deleted. It is the only thing in this repo that writes to `core.wiki.git`.

## Verify before pushing

There is no test or lint step. Run the same guards the workflow enforces, plus a link check:

```bash
# workflow guards
[ -f "01 - Evergreen/index.md" ] || echo "FAIL: no index.md — site root would 404"
find "01 - Evergreen" -name '*.md' | wc -l

# every note has frontmatter, and every published note has a title
for f in "01 - Evergreen"/*.md; do
  head -1 "$f" | grep -q '^---$' || echo "FAIL: no frontmatter: $f"
done
for f in "01 - Evergreen"/*.md; do
  grep -q '^title:' "$f" || echo "FAIL: no title: $f"
  grep -qE '^status: (draft|current|archived)$' "$f" || echo "FAIL: status not draft|current|archived: $f"
done

# dangling [[wiki-links]] — published pages may only link to published pages
python3 -c "
import re,os,glob
pages={os.path.basename(f)[:-3] for f in glob.glob('01 - Evergreen/*.md')}
bad=[(os.path.basename(f),m) for f in glob.glob('01 - Evergreen/*.md') for m in re.findall(r'\[\[([^\]|#]+)',open(f).read()) if m.strip() not in pages]
print('dangling:', bad or 'none')"

# config still parses and still has the settings we care about
python3 -c "
import yaml; c=yaml.safe_load(open('site/quartz.config.yaml'))['configuration']
assert c['baseUrl']=='civictechwr.github.io/core', c['baseUrl']
assert c['analytics'] is None, c['analytics']
print('config ok')"
```

A full local build needs Node 22+ — see *Previewing locally* in `01 - Evergreen/Editing-These-Docs.md`.

To rebuild without a content change, run the **Deploy Site** workflow from the Actions tab (`workflow_dispatch` is enabled).

## Editing `01 - Evergreen/Process-Index.md` — recount afterwards

The Process Index is a table of every process and where it is defined, with a status marker per row (`✅` one home · `⚠️` several that agree · `❌` several that disagree · `📭` not written down).

**Adding, removing or re-marking a row invalidates five prose statements of those counts** — four in the Summary, one in the Marketing section. They have been wrong twice. Find them, then recount programmatically:

```bash
grep -nE '[0-9]+ processes\.|Not written down \| [0-9]+|(sixteen|seventeen|eighteen) gaps|accounts for [a-z]+ of the|of (fifteen|sixteen) processes' "01 - Evergreen/Process-Index.md"
```


```bash
python3 -c "
import collections
c=collections.Counter(); per=collections.defaultdict(collections.Counter); sec=None
for l in open('01 - Evergreen/Process-Index.md'):
    if l.startswith('## '): sec=l[3:].strip()
    if l.startswith('|'):
        x=[y.strip() for y in l.strip().strip('|').split('|')]
        if len(x)==3 and x[2] in ('✅','⚠️','❌','📭'): c[x[2]]+=1; per[sec][x[2]]+=1
print(dict(c), 'total', sum(c.values()))
print({s:dict(v) for s,v in per.items()})"
```

## The model these docs encode

Four ideas connect the pages. Changes that contradict them need a deliberate decision, not a silent edit.

**One owner per fact.** Each kind of fact has exactly one home; everywhere else links rather than restates. Luma owns event times, Discourse owns meeting notes and recaps, GitHub owns anything needing a review trail, Drive owns only what cannot legally leave it, the blog owns public narrative. `01 - Evergreen/Ownership-Model.md`.

**Prefer fetching over stating.** `ctwr-web/_plugins/fetch_luma_event.rb` pulls the next hacknight from Luma at build time, which is why the website is the only surface whose meeting time is never wrong. That is the pattern to extend.

**Register vs. board.** The docs hold the durable register; GitHub Projects hold what someone has actually picked up. Items graduate from `01 - Evergreen/Remediation-Checklist.md` to a board — the checklist marks them *"On the board."* rather than duplicating the detail.

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

Instagram, Facebook and Threads are not retrievable without account access — the public pages are JavaScript shells. LinkedIn exposes roughly ten recent posts to logged-out requests. See `02 - Attachments/README.md`.

**Measure recency by last *content* change, not `pushed_at`.** Two repos in this org look active in the GitHub listing while having had no content change in eleven months — the commits are deploy and CI churn. Use `gh api "repos/OWNER/REPO/commits?path=docs&per_page=5"`.

## Org constraint on GitHub Actions

The organization restricts Actions to GitHub-owned, Marketplace-verified, `peaceiris/*` and `ruby/*`. **A third-party action needs a policy exception.**

This is the sharpest constraint on the publishing pipeline, and it is why Quartz won over the alternatives: its GitHub Pages deploy uses `actions/checkout`, `actions/setup-node`, `actions/upload-pages-artifact` and `actions/deploy-pages` — all GitHub-owned. `deploy-site.yml` and `retire-wiki.yml` use `actions/*` and plain `git` only. Anything needing `peaceiris/actions-gh-pages` would also be allowed; everything else needs an exception first.

## Conventions

- Branch from `main`; PRs target `main`. Merging a change under `01 - Evergreen/` rebuilds and deploys the site.
- Write claims that can be checked, and check them. Nearly every finding in `01 - Evergreen/Drift-Findings.md` came from measuring behaviour rather than reading documentation — the season doc says 12 weeks because someone wrote an ideal; the seasons are 15.
- When correcting a claim already published in the wiki, correct it in place and say so in the commit message. `Marketing.md` once asserted a recap cadence that the data contradicted.
