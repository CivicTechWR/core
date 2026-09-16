# core

A repo to manage CivicTechWR.

It is an **Obsidian vault**: notes move from `01 - Inbox` through `02 - Incubation` to `03 - Evergreen`, and `03 - Evergreen` is published as the docs site. Open the repo root as a vault; the shared configuration is committed in `.obsidian/`.

## Docs site

[**civictechwr.github.io/core**](https://civictechwr.github.io/core) — where CivicTechWR keeps its operating knowledge, what state each surface is in, and which surface owns which facts.

Built with [Quartz](https://quartz.jzhao.xyz) from [`03 - Evergreen/`](03%20-%20Evergreen) and deployed to GitHub Pages by [`.github/workflows/deploy-site.yml`](.github/workflows/deploy-site.yml) on every merge to `main`. Edit the markdown and open a PR.

> The GitHub Wiki that previously held these pages has been retired; it now holds a single page pointing here.

| Page | What it answers |
| --- | --- |
| [Documentation Surfaces](03%20-%20Evergreen/Documentation-Surfaces.md) | Where our docs live, and which are actually current |
| [Process Index](03%20-%20Evergreen/Process-Index.md) | Every process we run, and where each one is defined |
| [Process Modelling](03%20-%20Evergreen/Process-Modelling.md) | What a written-down process should look like |
| [Drift Findings](03%20-%20Evergreen/Drift-Findings.md) | What is out of date, contradictory, or duplicated |
| [Marketing](03%20-%20Evergreen/Marketing.md) | Tooling we have, what needs building, where the risk is |
| [Marketing Practices](03%20-%20Evergreen/Marketing-Practices.md) | What we actually publish, and what performs |
| [Ownership Model](03%20-%20Evergreen/Ownership-Model.md) | Which surface owns which fact |
| [Remediation Checklist](03%20-%20Evergreen/Remediation-Checklist.md) | What we're fixing, in what order |
| [Editing These Docs](03%20-%20Evergreen/Editing-These-Docs.md) | How to change pages and how publishing works |

## Layout

```
01 - Inbox/          capture — daily notes (YYYY-MM-DD) and timestamped drafts
02 - Incubation/     drafts being worked on; not yet the record
03 - Evergreen/      the register — published as the docs site (index.md is the landing page)
04 - Attachments/    data snapshots, exports, PDFs that notes point at; not notes
05 - Templates/      note templates (daily, unique)
site/                Quartz config for the site build, and the retired wiki's stub page
.obsidian/           vault configuration, committed so the format is shared
.github/workflows/deploy-site.yml    builds 03 - Evergreen/ with Quartz, deploys to Pages
.github/workflows/retire-wiki.yml    one-shot, manual: points the old wiki at the site
```

Every note carries the frontmatter block from `05 - Templates/unique.md` — `date`, `reviewed`, `tags`, `references` — plus a `title` on published pages. Files in `04 - Attachments/` are not notes and carry none.

A note is only published once it reaches `03 - Evergreen/`, so `[[wiki-links]]` on a published page must point at another page in that folder.
