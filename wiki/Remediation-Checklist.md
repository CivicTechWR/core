# Remediation Checklist

Fixes derived from [[Drift-Findings]] and [[Process-Index]], ordered by cost-to-fix ratio. Nothing here is assigned yet — owners and dates go in the table as they are picked up at an organizers meeting.

Check items off by editing [`wiki/Remediation-Checklist.md`](https://github.com/CivicTechWR/core/blob/main/wiki/Remediation-Checklist.md) in the `core` repo and merging to `main`.

---

## First pass — highest value, lowest effort

- [ ] **Pick one Slack invite and purge the other.**
  Eight files across three repos (`ctwr-web`, `.github`, org-docs). Verify which invite is live *first* — generate a fresh one if neither is. → finding 01
- [ ] **Fix the FAQ's Meetup references.**
  Replace with Luma in `docs/FAQ.md`, both occurrences. → finding 02
- [ ] **Fix the Event Roles channel list.**
  `EventRoles.md` tells marketing volunteers to update Eventbrite and Meetup. Replace with the channels actually in use. → finding 02
- [ ] **Replace `docs/index.md` with a real table of contents** and uncomment the nav entry in `mkdocs.yml`. → finding 03
- [ ] **Correct the season length** in `Guidline_Seasons.md` to match reality (~15 weeks), and rename the file to fix the spelling. → finding 06
- [ ] **Consolidate the project templates.**
  Delete `CTWR-Template`, rename `CTWR-Project-Template-New` → `CTWR-Project-Template`, fix the dead `ProjectTemplate` link in the org-docs README. → finding 07
- [ ] **Delete the duplicate blog** under `CTWR-Organization-Documentation/docs/blog/` — after moving the four unpublished drafts into the `blog` repo. Remove the committed `.obsidian/` folder. → finding 05
- [ ] **Add a `README` at the Google Drive root** stating what is archive and where the live equivalent lives. → [[Documentation-Surfaces]]

---

## Second pass — needs a decision at an organizers meeting

- [ ] **Adopt the ownership map** in [[Ownership-Model]], or amend it. Everything below assumes it is adopted.
- [ ] **Decide the fate of the blog.** Assign an owner and a cadence, or retire it publicly. Three seasons of silence is the status quo option. → finding 04
- [ ] **Decide where process documentation lives** — this wiki or the MkDocs site — and point the other at it. → findings 08, 09
- [ ] **Point the Discourse `CivicTechWR Wiki` category here** rather than growing it, once the above is decided. → finding 09
- [ ] **Fix the meeting-time fallback** in `_includes/meeting-section.html` to 5:30 PM, and state the soft-start/start distinction somewhere public. → finding 11
- [ ] **Remove the Code of Conduct copies** that shadow the org-level `.github` one — starting with the project template, so new repos stop inheriting the duplication. → finding 10
- [ ] **Clean the ~10 theme demo posts** out of the `blog` repo. → [[Documentation-Surfaces]]
- [ ] **Add per-season Discourse categories** for Seasons 6–8, or drop the per-season category pattern entirely. Move Season 8 out of `Internal Staff Discussion`. → [[Documentation-Surfaces]]

---

## Marketing

Day-to-day content work — posts, photography, design assets — is tracked on **[Project 46](https://github.com/orgs/CivicTechWR/projects/46)**, not here. This section carries only the marketing items that are documentation or policy gaps, or that need a decision rather than a doer.

Background and trade-offs for these are on [[Marketing]].

Applying [[Ownership-Model]]: where an item is already on the board, this list points at it instead of restating the detail. Marked *on the board* below.

**Needs a decision — carries risk**

- [ ] **Adopt a photo consent practice.** We assign a volunteer to photograph attendees at every event and publish the results, and `PrivacyPolicy.md` does not mention photos, images, video or likeness. Minimum viable: a line on the Luma event page, a sign at the door, and a mention in the hacknight welcome — the Emcee role already greets newcomers. Worth closing *before* the next event shoot. → [[Process-Index]]
- [ ] **Decide the newsletter question.** A live Mailchimp signup is collecting addresses from people who then hear nothing. Adopt it with an owner and a cadence, or take the form down. Leaving it as-is is the worst of the three. *On the board.*

**Documentation gaps**

- [ ] **Write the blog's missing `CONTRIBUTING.md`.** `blog/README.md` links to it and the link 404s, so nobody can follow the one process that would rebuild blog cadence. *On the board.*
- [ ] **Correct the channel list in `SocialMedia_Guidelines.md`** — Twitter and Meetup out, Bluesky and Threads in. *On the board.*
- [ ] **Write a photo storage convention and a shot list.** `Photos/YYYY/YYYY-MM-DD-event/` for storage; a five-line shot list so a volunteer knows when they are done. Drive currently holds 50 undifferentiated files from one day in 2025, with duplicates.
- [ ] **Write down a brand voice and tone**, even a single page. Nothing exists anywhere in the org.
- [ ] **Refresh the MediaKit** for the channels actually in use. *On the board.*

**Later — after the pipeline is proven**

- [ ] **Set the actual publishing cadence** — only once the blog has shipped a post or two. Whether to keep the blog at all is the Second pass item above; this is the follow-on to it. Committing to a number before the pipeline is proven is how the last one died.
- [ ] **Create recurring photo items at the start of each season**, one per hacknight, rather than relying on someone remembering weekly. The absence of this is the same mechanism that killed the blog.
- [ ] **Decide whether to measure reach at all** — and if so, what. Currently nothing is measured.

---

## Carried over from the June 2026 org audit

These were open in `.github/docs/org-audit-2026-06-04.md` and have not moved. → finding 12

- [ ] **Enable 2FA requirement** org-wide — pending Slack announcement and notice period
- [ ] **Scope the Slack app's permissions** — currently all repositories with `contents: write` + `workflows: write`
- [ ] **Enable secret scanning + push protection** org-wide
- [ ] **Enable Dependabot alerts** org-wide
- [ ] **Document offboarding cadence** — the audit's own follow-up item
- [ ] **Batch-remove ~50 inactive members** after the 2FA notice window closes

---

## Ongoing

- [ ] **Add a link-checking job to `core`** covering the drift-prone facts: Slack invite validity, event-channel URLs, cross-repo links. Findings 01, 02 and 07 are all things a machine should have caught.
- [ ] **Find and vendor the Luma → Discourse sync script.** It runs daily against production with an admin API key and its source is in no repository. Get it into `core`, then rotate the key. → finding 13
- [ ] **Re-audit, per pillar.** Once per season, at the finale — each pillar re-audits its own Process Index section rather than one person re-auditing all 68. Tracked as [Theme: Season re-audit](https://github.com/CivicTechWR/core/issues/24) on Project 47. Method is on [[Editing-This-Wiki]].

---

## Assignments

| Item | Owner | Target | Done |
| --- | --- | --- | --- |
| | | | |

*Last reviewed: 2026-08-19*
