---
title: "Editing These Docs"
date: "2026-08-19"
reviewed: false
tags:
references:
---
# Editing These Docs

## Where these pages come from

This site is **generated**. The source of truth is the [`03 - Evergreen/`](https://github.com/CivicTechWR/core/tree/main/03%20-%20Evergreen) folder of the [`core`](https://github.com/CivicTechWR/core) repo, which is an Obsidian vault.

Notes move **`01 - Inbox` → `02 - Incubation` → `03 - Evergreen`**, and only the evergreen layer is published. Promoting a note *is* the act of publishing it.

---

## How to change a page

1. Edit the matching file in [`core/03 - Evergreen/`](https://github.com/CivicTechWR/core/tree/main/03%20-%20Evergreen) — `Drift-Findings.md` becomes the *Drift Findings* page here.
2. Open a pull request.
3. Merge to `main`. The site rebuilds and deploys in a couple of minutes.

To add a page, drop a new `.md` file in `03 - Evergreen/`. There is no navigation file to update — the sidebar is generated from the folder.

**Frontmatter.** Every note starts with a YAML block, copied from `05 - Templates/unique.md`:

```yaml
---
title: "Ownership Model"
date: "2026-08-19"
reviewed: false
tags:
references:
---
```

`title` is what the browser tab, the sidebar and search results show; without it they fall back to the filename, hyphens and all. The other four are the vault's own properties, declared in `.obsidian/types.json`.

**Linking.** Double brackets, by filename: `[[Ownership-Model]]`. Obsidian resolves these as you type and the site resolves them on build.

**Only link to pages that are published.** A double-bracket link to a note in `01 - Inbox/` or `02 - Incubation/` resolves inside Obsidian but dangles on the site, which publishes `03 - Evergreen/` alone.

**`index.md` is the landing page.** Quartz serves it at `/`. Do not rename it.

---

## How publishing works

[`.github/workflows/deploy-site.yml`](https://github.com/CivicTechWR/core/blob/main/.github/workflows/deploy-site.yml) runs on every push to `main` that touches `03 - Evergreen/`. It builds the folder with [Quartz](https://quartz.jzhao.xyz) and deploys the result to GitHub Pages.

Four deliberate choices:

- **No third-party actions.** The org restricts Actions to GitHub-owned, Marketplace-verified, `peaceiris/*` and `ruby/*`. Every action in the workflow is `actions/*`, so it needs no policy exception. This ruled out most off-the-shelf publishing options and was the main reason Quartz won.
- **Quartz is pinned to a commit, not a branch.** Quartz expects to be forked; we clone it at a fixed SHA instead and copy our config (`site/quartz.config.yaml`) and our notes into that checkout. Upgrading is a deliberate bump of `QUARTZ_REF`, reviewed like any other change.
- **It refuses to build an empty or unlabelled source.** No pages, no `index.md`, or a note missing its frontmatter block all fail the build rather than deploying a broken site.
- **No analytics.** Quartz ships with Plausible enabled by default; the config sets `analytics: null`. This is an operating record, not a funnel.

### What Quartz gives us that the wiki could not

The GitHub Wiki was the first home for these pages and was retired on **2026-08-30**. It could not nest folders, could not read frontmatter, and had no backlinks, no graph and no real search. Quartz has all four, and renders Mermaid diagrams — see [[Process-Modelling]].

Old `github.com/CivicTechWR/core/wiki/...` links no longer resolve to content; the wiki now holds a single page pointing here.

### Previewing locally

Needs Node 22 or newer. From a clone of the `core` repo:

```bash
git clone https://github.com/jackyzha0/quartz.git /tmp/quartz
cd /tmp/quartz && git checkout 075afd3f712da0088a07f5284a7b3aba37dd61b6
npm ci
cp /path/to/core/site/quartz.config.yaml quartz.config.yaml
rm -rf content && mkdir content && cp -R "/path/to/core/03 - Evergreen/." content/
npx quartz build --serve
```

Then open http://localhost:8080. Do not run `npx quartz plugin install` — it needs a `quartz.lock.json` that a fresh clone does not have, and the build resolves plugins on its own.

### Running the deploy by hand

The workflow has `workflow_dispatch` enabled — run **Deploy Site** from the Actions tab to rebuild without a content change.

---

## Re-running the audit

The findings on [[Drift-Findings]] are a snapshot dated **2026-08-19**. Suggested cadence for refreshing them is once per season, at the finale.

What the original pass covered:

| Source | How |
| --- | --- |
| `civictechwr.org` | Fetched the live site; read `ctwr-web` source for `_data/`, `_includes/`, `_config.yaml` |
| Blog | Listed `blog/_posts/`; compared against the live index |
| Discourse | Read-only API key against `categories.json`, `latest.json`, `search.json`, `t/{id}.json` |
| GitHub | `gh repo list` across all 38 repos; recursive trees; **per-file commit dates**, not repo `pushed_at` |
| Google Drive | Walked the mounted `CivicTechWR Root` shortcut |

**The one methodological point that matters:** measure recency by *last content change*, not last push. Two repos in this org look active in the GitHub listing while having had no content change in eleven months — the commits are deploy and CI churn. Use `gh api "repos/OWNER/REPO/commits?path=docs&per_page=5"` rather than the repo's `pushed_at` field.

A Discourse read-only API key is needed for the forum — the JSON endpoints return 403 anonymously. Send it as an `Api-Key` header **with no `Api-Username` header**; adding one fails.
