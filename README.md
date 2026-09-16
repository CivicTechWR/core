# core

A repo to manage CivicTechWR.

It is an **Obsidian vault**, and `01 - Evergreen` is published as the docs site. Drafts are branches, not folders: write on a branch, open a PR, and merging to `main` publishes. Open the repo root as a vault; the shared configuration is committed in `.obsidian/`.

## Docs site

[**civictechwr.github.io/core**](https://civictechwr.github.io/core) — where CivicTechWR keeps its operating knowledge, what state each surface is in, and which surface owns which facts.

Built with [Quartz](https://quartz.jzhao.xyz) from [`01 - Evergreen/`](01%20-%20Evergreen) and deployed to GitHub Pages by [`.github/workflows/deploy-site.yml`](.github/workflows/deploy-site.yml) on every merge to `main`. Edit the markdown and open a PR.

> The GitHub Wiki that previously held these pages has been retired; it now holds a single page pointing here.

| Page | What it answers |
| --- | --- |
| [Documentation Surfaces](01%20-%20Evergreen/Documentation-Surfaces.md) | Where our docs live, and which are actually current |
| [Process Index](01%20-%20Evergreen/Process-Index.md) | Every process we run, and where each one is defined |
| [Process Modelling](01%20-%20Evergreen/Process-Modelling.md) | What a written-down process should look like |
| [Drift Findings](01%20-%20Evergreen/Drift-Findings.md) | What is out of date, contradictory, or duplicated |
| [Marketing](01%20-%20Evergreen/Marketing.md) | Tooling we have, what needs building, where the risk is |
| [Marketing Practices](01%20-%20Evergreen/Marketing-Practices.md) | What we actually publish, and what performs |
| [Ownership Model](01%20-%20Evergreen/Ownership-Model.md) | Which surface owns which fact |
| [Remediation Checklist](01%20-%20Evergreen/Remediation-Checklist.md) | What we're fixing, in what order |
| [Editing These Docs](01%20-%20Evergreen/Editing-These-Docs.md) | How to change pages and how publishing works |

## Layout

```
01 - Evergreen/      the register — published as the docs site (index.md is the landing page)
02 - Attachments/    data snapshots, exports, PDFs that notes point at; not notes
03 - Templates/      the note template (unique.md)
site/                Quartz config for the site build, and the retired wiki's stub page
.obsidian/           vault configuration, committed so the format is shared
.github/workflows/deploy-site.yml    builds 01 - Evergreen/ with Quartz, deploys to Pages
.github/workflows/retire-wiki.yml    one-shot, manual: points the old wiki at the site
```

Every note carries the frontmatter block from `03 - Templates/unique.md` — `date`, `status` (`draft` · `current` · `archived`), `tags`, `references` — plus a `title` on published pages. Files in `02 - Attachments/` are not notes and carry none.

Everything in `01 - Evergreen/` on `main` is published, so `[[wiki-links]]` must point at another page in that folder. Images and files in `02 - Attachments/` are not published: embed one and it renders in Obsidian but is missing on the site.
