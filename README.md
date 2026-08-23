# core

A repo to manage CivicTechWR.

## Wiki

[**github.com/CivicTechWR/core/wiki**](https://github.com/CivicTechWR/core/wiki) — where CivicTechWR keeps its operating knowledge, what state each surface is in, and which surface owns which facts.

The wiki is **generated from [`wiki/`](wiki) in this repo**. Edit the markdown there and open a PR; merging to `main` republishes the wiki automatically via [`.github/workflows/publish-wiki.yml`](.github/workflows/publish-wiki.yml).

Direct edits in the GitHub wiki UI are overwritten on the next merge.

| Page | What it answers |
| --- | --- |
| [Documentation Surfaces](wiki/Documentation-Surfaces.md) | Where our docs live, and which are actually current |
| [Process Index](wiki/Process-Index.md) | Every process we run, and where each one is defined |
| [Drift Findings](wiki/Drift-Findings.md) | What is out of date, contradictory, or duplicated |
| [Marketing](wiki/Marketing.md) | Tooling we have, what needs building, where the risk is |
| [Marketing Practices](wiki/Marketing-Practices.md) | What we actually publish, and what performs |
| [Ownership Model](wiki/Ownership-Model.md) | Which surface owns which fact |
| [Remediation Checklist](wiki/Remediation-Checklist.md) | What we're fixing, in what order |
| [Editing This Wiki](wiki/Editing-This-Wiki.md) | How to change pages and how publishing works |

## Layout

```
wiki/                            source for the GitHub wiki (flat — one .md per page)
.github/workflows/publish-wiki.yml   mirrors wiki/ to core.wiki.git on merge to main
```
