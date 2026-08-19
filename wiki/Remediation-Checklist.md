# Remediation Checklist

Fixes derived from [[Drift-Findings]], ordered by cost-to-fix ratio. Nothing here is assigned yet — owners and dates go in the table as they are picked up at an organizers meeting.

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
- [ ] **Re-audit.** Suggested cadence: once per season, at the finale. Method is documented on [[Editing-This-Wiki]].

---

## Assignments

| Item | Owner | Target | Done |
| --- | --- | --- | --- |
| | | | |

*Last reviewed: 2026-08-19*
