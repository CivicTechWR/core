# Documentation Surfaces

An inventory of every place CivicTechWR keeps operating knowledge, as of **2026-08-19**.

Surfaces are ordered by how recently something *meaningful* changed. This is deliberately not the same as GitHub's "last updated" — two repos look active in the org listing but their recent commits are deploy and CI churn, with no content change in eleven months.

| Surface | Last content change | Age | State |
| --- | --- | --- | --- |
| [Discourse (CoLab)](https://discourse.ctwr.org) | 2026-08-15 | 4 days | Current, login-gated |
| [Website](https://civictechwr.org) | 2026-08-17 | 2 days | Current |
| Google Drive — *CivicTechWR Root* | 2026-05 | 3 months | Archive with one live corner |
| [Blog](https://civictechwr.github.io/blog/) | 2025-09-10 | 11 months | Stale |
| [Org documentation site](https://civictechwr.github.io/CTWR-Organization-Documentation/) | 2025-09-25 | 11 months | Stale, broken entry point |

---

## Discourse — CoLab

`discourse.ctwr.org` · **the de facto operational record**

Sixteen categories. The active ones:

- **Organizers Meetings** — 17 topics, running through 2026-08-15
- **Recaps** — 28 topics, Wednesday hacknight summaries
- **Events** — 29 topics, auto-synced from Luma
- **Ideas & Proposals**, **Ask the Community**, **Show & Tell**, **Links**, **Speakers**
- **CivicTechWR Wiki** — opened April 2026, one topic

**Category structure has drifted from the season model.** There are `Season 4 Projects` and `Season 5 Projects` categories, but Seasons 6, 7 and 8 never got one — Season 8 planning sits in `Internal Staff Discussion`. `Projects` and `Older Projects` are both empty.

**Everything here is behind a login.** This is the single most consequential fact about our documentation: the most current knowledge sits on the least visible surface. See [[Drift-Findings]] finding 08.

---

## Website — `ctwr-web`

`civictechwr.org` · **best-maintained surface**

Jekyll, with genuinely serious engineering around it: accessibility CI, CodeQL, pa11y, CSP inline linting, a CSS budget validator, Dependabot auto-merge, and a Ruby plugin (`_plugins/fetch_luma_event.rb`) that pulls the next hacknight live from Luma at build time.

**That Luma plugin is the model for everything else.** It is the one place where a fact that changes weekly is fetched rather than restated. See [[Ownership-Model]].

Structured content lives in `_data/` — `navigation.yml`, `projects.yml`, `partners.yml`.

---

## Google Drive — *CivicTechWR Root*

**Effectively an archive with one live corner, and nothing says so.**

| Folder | Contents | State |
| --- | --- | --- |
| `Organizing/Season 8/` | Intake forms, call for pitches, pitches | Current |
| `Organizing/Banking/` | Financial records | Current (Feb 2026) |
| `Organizing/` (rest) | Funding applications, media kit, outreach, sponsorship, past season finales 1/3/4 | 2024–25 |
| `Meeting Notes & Decks/` | Presenter decks 2017–2019, one 2024 doc | Superseded by Discourse |
| `Past Projects/` | FederalVote, HousingHoF, MappingWR, MunicipalVote, Open Data Kitchener, SmartCitiesWR | 2018–2020 |
| `Photos/` | March 2025, with visible duplicates | Archive |

Drive holds the things that **genuinely cannot live in Git** — banking, funding applications, signed venue agreements, sponsorship correspondence. That part is worth keeping and is correctly placed. The rest may have been superseded.

---

## Blog

`civictechwr.github.io/blog/` · Jekyll, deployed from `main` in the `blog` repo

Last published post: **Season 5 Finale, 2025-09-10**. Since then the org has run Season 6, Season 7 (showcase April 2026), and is now in Season 8 with a showcase on **2026-08-26**. None of it is written up.

This is the only public, un-gated *narrative* surface CivicTechWR has, and it is the one that stopped.

The repo also still carries roughly ten unremoved theme demo posts (`old_2020-01-01-french-wine.md`, `review-oscar`, `london`, `post-with-spoiler`), and several drafts that were never published.

---

## Org documentation site — `CTWR-Organization-Documentation`

MkDocs Material, deployed to GitHub Pages. **The designated home for policies, guidelines and templates — and it has had zero content commits since 2025-09-25.**

What is in it:

- **Policies** — Code of Conduct, Diversity & Inclusion, Privacy, Data Deletion
- **Guidelines & Templates** — event planning, event roles, seasons, pitching, communications, social media, recaps, demo slides, interview questions, outreach letter, feedback TOS
- **FAQ**
- **A second, parallel copy of the blog**

Its entry point is broken: `docs/index.md` is a "Land of the Lost Pages" 404 joke page that was never replaced. The nav entry is commented out with *"I dont think we want the index right now as it seems to be the error page,"* and the repo's homepage field routes around it straight to `/FAQ/`.

---

## GitHub — 38 repos

Not a documentation surface as such, but it carries real documentation:

- **`.github`** — the org-wide community-health baseline: Code of Conduct, contributing guide, security policy, seven issue templates, CODEOWNERS, gitleaks config. Also holds the **June 2026 org audit** with open action items.
- **`CTWR-Project-Template-New`** — a genuinely comprehensive starter: 12-week workflow, accessibility guide, impact tracking, user research templates, wiki templates, setup scripts.
- **`core`** — this repo. Now the home of this wiki.

Roughly a dozen live project repos, eight WRvotes repos spanning six election cycles, and eleven archived.
