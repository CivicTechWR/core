# Editing This Wiki

## ⚠️ Do not edit pages here directly

This wiki is **generated**. The source of truth is the [`wiki/`](https://github.com/CivicTechWR/core/tree/main/wiki) directory of the [`core`](https://github.com/CivicTechWR/core) repo.

Anything you type into GitHub's wiki editor will be **silently overwritten** the next time someone merges to `main`. Edit the source instead.

---

## How to change a page

1. Edit the matching file in [`core/wiki/`](https://github.com/CivicTechWR/core/tree/main/wiki) — `Drift-Findings.md` on GitHub becomes the *Drift Findings* page here.
2. Open a pull request.
3. Merge to `main`. The wiki updates within about a minute.

To add a page, drop a new `.md` file in `wiki/` and add it to `_Sidebar.md`.

**Naming:** the filename becomes the page title, with hyphens shown as spaces. `Ownership-Model.md` → *Ownership Model*. Link between pages with double brackets: `[[Ownership-Model]]`.

---

## How publishing works

[`.github/workflows/publish-wiki.yml`](https://github.com/CivicTechWR/core/blob/main/.github/workflows/publish-wiki.yml) runs on every push to `main` that touches `wiki/`. It mirrors the directory into the wiki's own git repo — `core.wiki.git` — including deletions, then pushes.

Three deliberate choices:

- **No third-party actions.** The org restricts Actions to GitHub-owned, Marketplace-verified, `peaceiris/*` and `ruby/*`. The workflow uses `actions/checkout` plus plain `git`, so it needs no policy exception and nothing to audit.
- **It refuses to publish an empty directory.** A mistake that deletes `wiki/` would otherwise wipe the whole wiki in one merge.
- **It detects the wiki's default branch** rather than assuming. Today that branch is `master`.

### Why the wiki's branch is `master`

GitHub wiki repos are hardwired to `master` and there is no setting — UI or API — to change it. Pushing a `main` branch succeeds but `HEAD` stays on `master` and the wiki keeps serving `master`, so the new branch is simply ignored.

The workflow reads the wiki's actual default branch at run time, so it works today and will keep working if GitHub ever lifts this.

### Running it by hand

The workflow has `workflow_dispatch` enabled — run it from the Actions tab to force a republish without a code change.

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
