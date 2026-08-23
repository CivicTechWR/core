# Process Index

Every process CivicTechWR runs, and where it is written down. Many are written down in more than one place — those rows are the work.

Compiled **2026-08-19**. Companion to [[Drift-Findings]]; the ownership rules this is meant to feed are on [[Ownership-Model]].

## Legend

| | Meaning |
| --- | --- |
| ✅ | One definition, one place |
| ⚠️ | Defined in several places that broadly agree — needs merging, not arbitration |
| ❌ | Defined in several places that **disagree** — someone must decide which is true |
| 📭 | Happens, but is not written down anywhere |

Locations are abbreviated:

- **org-docs** — `CTWR-Organization-Documentation/docs/`
- **template** — `CTWR-Project-Template-New/`
- **.github** — the org-wide `.github` repo
- **Discourse** — `discourse.ctwr.org` (login-gated)
- **Drive** — Google Drive, *CivicTechWR Root*

---

## Season and project lifecycle

| Process | Defined in | |
| --- | --- | --- |
| Season structure and length | org-docs `Guidelines_&_Templates/Guidline_Seasons.md` (2025-09) — says 12 weeks; **reality is ~15** | ❌ |
| Pitching a problem | org-docs `Template_Pitching.md` (2025-09)<br>template `docs/PROJECT_PITCH.md` (2026-08) — **same document**, one prose, one fill-in-the-blank | ⚠️ |
| Project intake | Drive `Organizing/Season 8/CTWR - Project Intake Form`<br>Drive `Season 8 Project Intake Form.gsheet`<br>Discourse — *Season 8 Project Discussion* (Internal Staff Discussion) | ⚠️ |
| Call for pitches | Drive `Organizing/Season 8/CivicTechWR Call for Pitches` | ✅ |
| Project setup and management | template `docs/PROJECT_MANAGEMENT.md`, `GETTING_STARTED.md`, `scripts/setup.sh` | ✅ |
| Demo day / showcase prep | org-docs `Demo_Slides_Template.md` (2025-09)<br>template `docs/DEMO_PREP.md` (2026-08) — 8-step structure, supersedes | ⚠️ |
| Showcase event logistics | Drive `Organizing/CTWR: Event Logistics for Product Demo Day` (2025-02) | ✅ |
| Season finale | Drive `Organizing/Season {1,3,4} Finale/` — per-season folders, no reusable process | 📭 |
| Season retrospective | Drive `OrganizerContent/CivicTechWR 2017 Retrospective` (2017) only | 📭 |

---

## Hacknights and events

| Process | Defined in | |
| --- | --- | --- |
| Running a hacknight | org-docs `Event_Planning_Guide.md` (2025-06) — generic 5-step outline<br>Discourse — *How to run a CivicTechWR hacknight?* (2026-04) — **stub**, "Template template template" | ❌ |
| Event roles on the night | org-docs `EventRoles.md` (2025-09) — 8 per-event roles<br>Discourse — *Volunteer Roles for Season 8* (2026-02) — 5 per-season roles | ❌ |
| Event planning checklist | org-docs `Event_Planning_Template.md` | ✅ |
| Meeting time and doors | ctwr-web live site — 5:30 PM (pulled from Luma)<br>ctwr-web `_includes/meeting-section.html` fallback — 6:00 PM<br>.github `CONTRIBUTING.md` — "Wednesdays 6:00–8:00 p.m."<br>Discourse hacknight topic — soft start 5:30, start 6:00 | ❌ |
| Creating the Luma event | Referenced as a duty in Discourse *Volunteer Roles*, defined nowhere | 📭 |
| Guest speaker coordination | Discourse — *Volunteer Roles for Season 8* (duties only)<br>Drive `Organizing/List of possible speakers` (2025-02)<br>Drive `Onboarding/Onboarding - CivicTech WR Speaker (COVID)` — **COVID-era** | ⚠️ |
| Writing hacknight recaps | org-docs `Recaps_Template.md` (template)<br>Discourse `Recaps` category (28 instances) | ⚠️ |
| Room setup and signage | Drive `OrganizerContent/Signs for Directions` | ✅ |
| Food and refreshments | Discourse — *Volunteer Roles for Season 8*<br>org-docs `EventRoles.md` § Food & Drink Setup | ⚠️ |

---

## Roles and volunteering

| Process | Defined in | |
| --- | --- | --- |
| **Who does what** | org-docs `EventRoles.md` — 8 per-event shifts<br>Discourse *Volunteer Roles for Season 8* — 5 per-season owners<br>Discourse *Organizer Groups and Roles* — 3 standing committees | ❌ |
| Joining the organizing team | Discourse — *Organizer Groups and Roles* (2026-03) | ✅ |
| New member onboarding at a hacknight | Gestured at in Discourse *Volunteer Roles* ("greet new members, help orient them"); no written flow | 📭 |
| GitHub org access and teams | .github `docs/governance/codeowners-branch-protection.md`<br>.github `docs/org-audit-2026-06-04.md` § 9 (the RBAC model as actually applied) | ⚠️ |
| Offboarding / removing inactive members | **Explicitly outstanding** — June 2026 audit item 7 says *"TODO: document offboarding cadence"* | 📭 |

**This is the sharpest conflict in the whole index.** Three role models coexist and they are structurally different — per-event shifts, per-season ownership, standing committees — not three stale copies of one list. A volunteer asking "what can I sign up for?" gets a different answer depending on which one they find. The repo version is the most detailed and the most wrong: it still says to update Eventbrite and Meetup listings.

---

## Communications and outreach

| Process | Defined in | |
| --- | --- | --- |
| **Which channel to use** | org-docs `Communication_Guidelines.md` (2025-01) — lists Slack, Email, GitHub, **Meetup**; omits Discourse<br>.github `CONTRIBUTING.md` § Communication Channels — Slack, GitHub issues, Email, organizers team; omits Discourse<br>Discourse — *How to Use the Slack ↔ Discourse Integration* (2026-02) — the only one that covers Discourse, and login-gated | ❌ |
| Slack ↔ Discourse integration | Discourse — *How to Use the Slack ↔ Discourse Integration* | ✅ |
| Community outreach interviews | org-docs `InterviewQuestions.md` | ✅ |
| Outreach email | org-docs `OutreachLetter.md`<br>Drive `OrganizerContent/Outreach.gsheet` (tracking) | ⚠️ |
| Meeting notes | Discourse `Meeting Notes` category + auto-populating template (2026-02)<br>Discourse `Organizers Meetings` category (17 topics — where they actually go)<br>Drive `Organizing/ Meeting notes/` (through 2025-01) | ⚠️ |

---

## Marketing and content

Narrative, tooling and decisions are on [[Marketing]]; this is the inventory only.

| Process | Defined in | |
| --- | --- | --- |
| Marketing work intake and tracking | [GitHub Project 46 — *Marketing*](https://github.com/orgs/CivicTechWR/projects/46) (2026-08) — Triage / Now / Cadence / Editorial views, typed by Content type, Channel, dates and Effort | ✅ |
| **Social media posting** | org-docs `SocialMedia_Guidelines.md` (2025-01) — generic advice, and its channel list names **Twitter and Meetup** while omitting **Bluesky and Threads**, both live on the site<br>Drive `Organizing/Example Social Media Posts` (2024-11) | ❌ |
| Brand assets | Drive `Organizing/MediaKit/Branding/` — brandmarks (SVG + PNG), pre-sized social images, sticker PDF, favicons<br>Sized for `400_Twitter` and `180_Facebook`; nothing for Bluesky or Threads | ⚠️ |
| Boilerplate copy and blurbs | Drive `Organizing/MediaKit/CivicTechWRBlurbs` | ✅ |
| Brand voice and tone | — | 📭 |
| Visual design system (colour, type) | — nothing anywhere in the org beyond the logo files | 📭 |
| **Publishing a blog post** | `blog/README.md` links to a `CONTRIBUTING.md` that **does not exist** — the link 404s<br>Named as a duty in Discourse *Volunteer Roles* ("maintain the blog and newsletter"); no owner, no cadence, silent since 2025-09 | 📭 |
| Newsletter | ctwr-web `_includes/newsletter-signup.html` — a **live Mailchimp list** collecting addresses<br>No sends, no owner, no process | 📭 |
| Event photography | org-docs `EventRoles.md` § Photo & Social Media — the role exists, but no shot list, no storage convention<br>Drive `Photos/` is 50 undifferentiated files from 2025-03, with duplicates | 📭 |
| **Photo consent and likeness** | — nothing. `PrivacyPolicy.md` does not mention photos, images, video or likeness, though we assign a volunteer to photograph attendees and publish the results | 📭 |
| Content calendar and cadence | GitHub Project 46 *Cadence* view (2026-08) — the mechanism now exists; no cadence has been agreed | ⚠️ |
| Press and media relations | Drive `Organizing/MediaKit/`<br>Blog "In the news" posts (2018) — no current process | 📭 |
| Measuring reach or impact | — | 📭 |

Marketing is the least-documented area in this index: **eight of thirteen processes have nothing written down at all.** The two that carry risk rather than just drag:

- **Photo consent.** We assign someone to photograph attendees at every event and publish the results, and no policy anywhere covers it. Worth closing before photography ramps up, not after.
- **The newsletter.** A live Mailchimp form is collecting addresses from people who then hear nothing. Either adopt it or take the form down; leaving it is the worst of the three options.

---

## Projects — technical practice

| Process | Defined in | |
| --- | --- | --- |
| Contributing to a project | .github `CONTRIBUTING.md` (org-wide)<br>org-docs `Contribution_Guidelines.md`<br>template `docs/CONTRIBUTING.md` (per-project) | ⚠️ |
| User research | template `docs/USER_RESEARCH.md` | ✅ |
| Accessibility | template `docs/ACCESSIBILITY_GUIDE.md`<br>ctwr-web `.github/workflows/accessibility.yml`, `.pa11yci.json` (enforced) | ⚠️ |
| Impact tracking | template `docs/IMPACT_TRACKING.md` | ✅ |
| Technical design | template `docs/TECHNICAL_DESIGN.md` | ✅ |
| Repo security setup | template `docs/REPOSITORY_SECURITY.md`, `docs/SECURITY_GUIDE.md`, `scripts/setup-security.sh`<br>.github `SECURITY.md`, `.gitleaks.toml`, `docs/gitleaks-response.md` | ⚠️ |
| Branch protection / CODEOWNERS | .github `docs/governance/codeowners-branch-protection.md`<br>template `scripts/branch-protection.json` | ⚠️ |
| Deployments | ctwr-web `docs/deployments.md` (site-specific)<br>template `docs/GITHUB_PAGES.md` | ✅ |
| Dependency auto-merge | ctwr-web `docs/DEPENDABOT_AUTO_MERGE.md` | ✅ |
| Starting a new project repo | template `GETTING_STARTED.md` + `scripts/setup-project.sh`<br>**but** org-docs README points at `ProjectTemplate`, which does not exist, and two other template repos claim to be canonical | ❌ |

---

## Governance, policy and money

| Process | Defined in | |
| --- | --- | --- |
| Code of Conduct | .github `CODE_OF_CONDUCT.md` (org-wide default)<br>org-docs `policies/Code_of_Conduct.md`<br>ctwr-web `.github/CODE_OF_CONDUCT.md`<br>template `CODE_OF_CONDUCT.md` | ⚠️ |
| Diversity and inclusion | org-docs `policies/Diversity_and_Inclusion_Policy.md` | ✅ |
| Privacy | org-docs `policies/PrivacyPolicy.md` | ✅ |
| Data deletion | org-docs `policies/DataDeletion.md` | ✅ |
| Feedback portal terms | org-docs `FeedbackTOS.md` | ✅ |
| Security incident response | .github `SECURITY.md`, `docs/gitleaks-response.md` | ✅ |
| Org security posture review | .github `docs/org-audit-2026-06-04.md` — a one-off, no cadence set | ⚠️ |
| Sponsorship requests | Drive `OrganizerContent/Request for Sponsorship`<br>Discourse — *Creating a PlayBook to Request Free Services* (2026-02, **a proposal, not a process**) | ⚠️ |
| Grant and funding applications | Drive `Organizing/Funding Applications/` — four applications, no reusable process | 📭 |
| Expenses and budget approval | Drive `OrganizerContent/CivicTechWR Expenses.gsheet`<br>Drive `Organizing/Banking/`<br>"Expense Review" appears as a standing agenda item in Discourse org meetings | 📭 |

---

## Documentation itself

| Process | Defined in | |
| --- | --- | --- |
| Editing and publishing this wiki | [[Editing-This-Wiki]] + `core/.github/workflows/publish-wiki.yml` | ✅ |
| Editing the org-docs site | org-docs `CONTRIBUTING.md`, `README.md` (local MkDocs setup) | ✅ |
| Which surface owns which fact | [[Ownership-Model]] (proposed)<br>Discourse *Slack ↔ Discourse Integration* has a "use Discourse for… / use Slack for…" table that already agrees with it | ⚠️ |
| Re-auditing documentation drift | [[Editing-This-Wiki]] § Re-running the audit | ✅ |
| Marking Drive content as archived | — | 📭 |

---

## Summary

**66 processes.** Fewer than half have a single home.

| | Count |
| --- | --- |
| ❌ Conflicting definitions | 8 |
| ⚠️ Multiple locations, broadly agreeing | 19 |
| ✅ Single source | 23 |
| 📭 Not written down | 16 |

**The eight conflicts are the ones that need a decision**, not an edit: season length, hacknight procedure, event roles, meeting time, the role model, which channel to use, which social channels we are on, and which project template is canonical. Each has two or more good-faith answers written by different people at different times, and no rule for picking between them — which is the gap [[Ownership-Model]] exists to close.

**The sixteen gaps cluster in two places** — marketing, and money and endings. Marketing alone accounts for eight of them. The rest are offboarding, funding, expenses, retros, season finales: things that happen a few times a year, get done by whoever did them last, and were never written down.

Two of the gaps carry real risk rather than just friction, both in marketing: **no photo consent practice** while we photograph attendees and publish the results, and **a live newsletter signup** collecting addresses from people who then hear nothing.

One pattern worth naming: **where a process exists in both a repo and on Discourse, the Discourse copy is almost always more current and more correct.** Reference material stayed in Git and went stale; the live instances moved to Discourse and stayed accurate. That seam — templates in Git, instances on Discourse — is sensible and worth keeping deliberately rather than by accident.
