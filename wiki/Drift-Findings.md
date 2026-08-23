# Drift Findings

Thirteen findings from the **2026-08-19** audit, ordered by what a newcomer or volunteer hits first. Number 01 is the one that costs us people.

Finding 13 was added on 2026-08-23 and is numbered last because it was found last. **By severity it belongs at the top** — it is numbered this way only so the references from [[Remediation-Checklist]] stay stable.

Each finding is tagged: **Broken path** (someone following our docs ends up nowhere), **Contradicted** (two surfaces disagree), **Duplicate** (the same fact maintained in several places), **Stale** (accurate once), **Structural** (a problem with the arrangement, not the content).

Fixes and ownership are tracked on [[Remediation-Checklist]].

---

### 01 — Two different Slack invite links are live
**Broken path**

The website and the org's GitHub profile hand out different Slack invites. Whichever one has expired, some fraction of people trying to join are bouncing silently and we never hear about it.

| Link | Appears in |
| --- | --- |
| `zt-2hk4c93hv…` | `ctwr-web`: `index.html`, `_includes/footer.html`, `_config.yaml` |
| `zt-2ldijjy0i…` | `.github`: `profile/README.md`, `CONTRIBUTING.md`<br>org-docs: `FAQ.md`, `mkdocs.yml`, `docs/overrides/main.html` |

Eight files, three repos. Highest cost-to-fix ratio in this audit.

---

### 02 — The FAQ sends people to Meetup
**Broken path**

The org documentation FAQ names `meetup.com/civictechwr` as the place to find the schedule and venue, and repeats it under "how do I stay updated." Events moved to Luma long ago — the website's own config maps `meetup:` straight to `luma.com/civictechwr`. Anyone following the FAQ never finds a hacknight.

Last touched **2025-01-06**. Related: `EventRoles.md` still instructs the marketing volunteer to *"update Eventbrite or Meetup listings"* — neither channel is in use.

---

### 03 — The documentation site opens on a 404 page
**Broken path**

The index of the org's documentation site is a joke error page — *"look who took a wrong turn on the internet highway."* It was never replaced. The nav entry for it is commented out, and the repo's homepage link skips past it to `/FAQ/`. Anyone reaching the site root gets a dead end where the table of contents should be.

---

### 04 — The blog stopped three seasons ago
**Stale**

Last published post is **Season 5 Finale, 2025-09-10**. Season 6, Season 7 (showcase April 2026) and Season 8 (showcase 2026-08-26) have no coverage at all.

The blog is our only public, un-gated narrative surface. It is the thing that shows an outsider we are alive.

---

### 05 — The blog exists twice
**Duplicate**

There is a Jekyll blog in the `blog` repo (the live one) and a second MkDocs blog inside `CTWR-Organization-Documentation/docs/blog/`, with the blog plugin enabled. Roughly a dozen posts exist in both.

Four posts exist **only** in the docs copy and were never published anywhere:

- One Year of CivicTech WR
- Update — Introducing Season Format
- Season 4 Recap
- End of Season DRAFT

Also committed into the docs copy: an `.obsidian/` workspace folder.

---

### 06 — The documented season is 12 weeks; the real one is 15
**Contradicted**

`Guidline_Seasons.md` defines Week 1 pitching, Week 2 mini-hackathon, Week 3 buffer, Weeks 4–11 build, Week 12 demo day.

Reality:

- **Season 8** — Pitch Night 2026-05-13, showcase 2026-08-26. Fifteen weeks.
- **Season 7** — recaps reached Week 11 on 2026-03-18, showcase five weeks later on 2026-04-22.

This is the single most-referenced document for anyone joining a project team, and it sets the wrong expectation about how long they are committing to. The filename is also misspelled (`Guidline`), as is the content (*"prottyping"*).

---

### 07 — Three project templates, none canonical
**Duplicate**

| Repo | State | Description says |
| --- | --- | --- |
| `CTWR-ProjectTemplate` | Archived, 2020 | *"All projects should start from here"* |
| `CTWR-Template` | 2024, contains only LICENSE + README | *"All projects should start from here"* |
| `CTWR-Project-Template-New` | 2026, comprehensive and good | — |

The real one is named as though it is provisional. Meanwhile the org-docs README links to `github.com/CivicTechWR/ProjectTemplate` — **a repo that does not exist**.

---

### 08 — Discourse holds the real knowledge but nobody outside can read it
**Structural**

Org meeting notes, recaps, roles, and the how-to-run-a-hacknight page all live behind a login. The public documentation site — the thing search engines and newcomers find — is the frozen one.

**Our most current surface and our most visible surface are inverses of each other.** Every other finding on this page is downstream of that.

---

### 09 — The wiki fork has already started
**Structural**

A **CivicTechWR Wiki** category was created on Discourse in April 2026. Its single topic, *"How to run a CivicTechWR hacknight?"*, is a stub — soft start 5:30, start 6:00, *"Template template template."*

It re-opens ground that `EventRoles.md` and `Event_Planning_Guide.md` already cover in far more detail. Not because those are bad, but because they are eleven months stale and effectively invisible.

This is drift *in progress*. It resolves in one direction or the other over the next few months whether or not anyone decides deliberately.

---

### 10 — The Code of Conduct is in four places
**Duplicate**

- `.github/CODE_OF_CONDUCT.md` — org-wide default, automatically applies to every repo
- `ctwr-web/.github/CODE_OF_CONDUCT.md`
- `CTWR-Project-Template-New/CODE_OF_CONDUCT.md`
- `CTWR-Organization-Documentation/docs/policies/Code_of_Conduct.md`

Each per-repo copy silently shadows the org-level one. Because the template carries a copy, **every new project spawned from it adds a fifth, sixth, seventh** — this one gets worse on its own.

---

### 11 — The website's fallback meeting time is wrong
**Contradicted**

`_includes/meeting-section.html` defaults to **6:00 PM** when the Luma fetch returns nothing. The live site shows **5:30 PM**, pulled from Luma. The wrong fallback only appears when the sync fails — precisely when nobody is watching.

Reading the ICS directly (2026-08-23) shows Luma sets times **per event type**:

| Event | Luma says |
| --- | --- |
| Hacknight, 2026-08-19 | 5:30 – 8:00 PM ET |
| Project Showcase, 2026-08-26 | 6:00 – 9:00 PM ET |

So the hardcoded copies are not arbitrary — they encode "hacknight proper" at 6:00, while Luma publishes the **doors** time. Both are therefore half an hour off for hacknights: the `meeting-section.html` fallback, and `.github/CONTRIBUTING.md`'s "Wednesdays from 6:00–8:00 p.m."

Discourse's hacknight stub is the only place that states the distinction — *soft start 5:30, hacknight starts 6:00* — and it is login-gated. **Luma is the source of truth; nothing else should restate it.**

---

### 12 — The June audit's own follow-up was never written
**Stale**

The June 2026 org audit closed item 7 with *"TODO: document offboarding cadence in `CTWR-Organization-Documentation`."* That repo has had no content commit since September 2025.

Audit items 1, 3, 5 and 6 — 2FA enforcement, Slack app scoping, org-wide secret scanning, org-wide Dependabot alerts — remain marked waiting, all pending a Slack announcement and a Saturday org meeting.

---

### 13 — A production script runs daily with no source in version control
**Structural** · *found 2026-08-23*

The Discourse `Events` category is populated by an external script that calls the Discourse API as the `system` user (id −1), daily at about 10:00 UTC, creating one topic per new Luma event with `discourse-calendar` markup and a link to the specific Luma event page.

It is incremental — 12 topics on 2026-05-28, 4 on 2026-04-26, 1–2 on other runs — and was backfilled on 2026-02-04 when the category was created.

**The source code is not in any CivicTechWR repository.** The only Luma code in the org is `ctwr-web/_plugins/fetch_luma_event.rb`, which is the website's build-time fetch, not this. It is not in `ctwr-apps` either.

So a scheduled job runs against production Discourse holding an admin API key, and nobody can point at the code.

- If it breaks, we cannot fix it.
- If the key leaks or needs rotating, we do not know everywhere it is used.
- If the person running it steps back, the Events category silently stops.

The audit did not catch this by looking at documentation — it surfaced only by inspecting what the automation actually produced. Worth asking at an organizers meeting whose machine or account it runs from, then getting it into `core`.

See [[Marketing]] for how this fits the wider Luma → website → Discourse flow.
