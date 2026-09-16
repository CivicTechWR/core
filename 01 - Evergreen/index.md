---
title: "Documentation"
date: "2026-08-19"
reviewed: false
tags:
references:
---
# CivicTechWR Documentation

These docs are the working record of **where CivicTechWR keeps its operating knowledge**, what state each surface is in, and which surface owns which facts.

This site is built with [Quartz](https://quartz.jzhao.xyz) from the [`01 - Evergreen/`](https://github.com/CivicTechWR/core/tree/main/01%20-%20Evergreen) folder of the `core` repo — the vault's *evergreen* layer. Edit there, open a PR, and merging to `main` rebuilds this site. See [[Editing-These-Docs]].

---

## Start here

| Page | What it answers |
| --- | --- |
| [[Documentation-Surfaces]] | Where do our docs live, and which surfaces are actually current? |
| [[Process-Index]] | Every process we run, and where each one is written down. |
| [[Process-Modelling]] | What a written-down process should look like — BPMN, CMMN, DMN, and what fits us. |
| [[Drift-Findings]] | What is out of date, contradictory, or duplicated right now? |
| [[Marketing]] | What tooling we already have, what still needs building, and where the risk is. |
| [[Marketing-Practices]] | What we actually publish — post types, conventions, and what performs. |
| [[Ownership-Model]] | Which surface owns which fact — and what to do instead of restating it? |
| [[Remediation-Checklist]] | What are we fixing, in what order, and who has it? |
| [[Editing-These-Docs]] | How to change these pages and how publishing works. |

---

## The short version

CivicTechWR maintains five documentation surfaces. Three are current, two have been frozen since September 2025 — and the frozen ones are the public-facing ones that newcomers and search engines find first.

| Surface | Last meaningful change | State |
| --- | --- | --- |
| Discourse (CoLab) | 2026-08-15 | Current — but login-gated |
| Website (`ctwr-web`) | 2026-08-17 | Current |
| Google Drive | 2026-05 (Season 8 only) | Archive, unmarked |
| Blog | 2025-09-10 | Stale — 3 seasons behind |
| Org documentation site | 2025-09-25 | Stale — index is a 404 page |

**Recency is measured by last content change, not last push.** Several repos show recent GitHub activity that is deploy or CI commits only.

The problem is not neglect. The website and Discourse are both well tended. The problem is that **five surfaces exist with no rule about which one owns a given fact**, so volunteers write wherever it is easiest and everything else quietly rots. That is what [[Ownership-Model]] is meant to fix.

---

## Cost of the drift, concretely

- Two different Slack invite links are live at once. Some fraction of people trying to join are bouncing silently.
- The FAQ tells people to find hacknights on Meetup. Events moved to Luma. Follow the FAQ and you never find a meeting.
- The documentation site's homepage is a joke 404 page that was never replaced.

Full list on [[Drift-Findings]].

---

*Audit date: 2026-08-19. Season 8, week 15. To re-run the audit, see [[Editing-These-Docs]].*
