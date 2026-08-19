# Ownership Model

## The problem this solves

Every finding on [[Drift-Findings]] has the same root cause. CivicTechWR has five documentation surfaces and **no rule about which one owns a given fact**. So a volunteer writes the meeting time wherever they happen to be, and now it exists in four places that will diverge.

The failure mode is not neglect — the website and Discourse are both actively tended. It is that nobody can tell, for any given fact, which copy is the real one.

---

## The options we considered

### Consolidate everything into Discourse

Lean into where people already are. Wiki-mode posts, low friction to edit, retire the MkDocs site.

**Why not:** it puts everything behind a login and loses Git history — public discoverability and a review trail are the two things a documentation site exists to provide. It would fix the drift by making the docs invisible.

### Revive the MkDocs site

Fix the 404 index, the FAQ and the season guide; point Discourse and Slack at it.

**Why not:** nothing changes structurally. The site already died once from exactly this state. PR-based editing is *why* volunteers went to Discourse instead — reviving it without changing that dynamic just resets the clock.

### Assign ownership per fact ← **chosen**

One surface owns each *kind* of fact. Everywhere else links rather than restates. Automate the facts that already demonstrably drift.

**Why:** it attacks the actual cause, requires no migration, and does not require declaring a winning platform. Each surface keeps doing what it is already good at.

---

## The ownership map

| Fact type | Owner | Everyone else |
| --- | --- | --- |
| Event times, dates, venue, RSVP | **Luma** | Fetch or link. Never restate. |
| Meeting notes, recaps, in-flight discussion | **Discourse** | Link. |
| Policies, guidelines, templates, process | **GitHub** (`.github` org repo + this wiki) | Link. |
| Banking, funding applications, signed agreements | **Google Drive** | Link. Nothing else belongs there. |
| Public narrative — what we did and why | **Blog** | Link. |
| Project code and project-specific docs | **The project repo** | Link. |

---

## The three rules

**1. One owner per fact.** If you are about to type our meeting time, our Slack invite, or our season length into a document, stop — link to the owner instead. A fact stated in two places is a fact that will be wrong in one of them.

**2. Prefer fetching over stating.** The website already proves this works: `_plugins/fetch_luma_event.rb` pulls the next hacknight from Luma at build time, which is why the website is the only surface whose meeting time is never wrong. Extend the same pull to Discourse and to any document that needs an event time.

**3. Mark what is archived.** A superseded document that does not say it is superseded is worse than a deleted one, because people still act on it. Drive's 2019 meeting decks and the org-docs FAQ are both currently doing damage in this way.

---

## Consequences worth naming

Adopting this means:

- **The org-docs MkDocs site loses its exclusive claim on process documentation.** Process that changes often should move here, to the `core` wiki, where editing is cheap. Policies with legal or review weight stay in `.github` where CODEOWNERS applies.
- **Discourse stops being a documentation destination** and goes back to being a discussion destination. The `CivicTechWR Wiki` category should be pointed here rather than grown — see [[Drift-Findings]] finding 09.
- **Drive shrinks deliberately** to only what cannot legally or practically live in Git.
- **Someone has to own the blog** or it should be honestly retired. Three seasons of silence on our only public narrative surface is itself a message.

---

## Keeping this honest

An audit of documentation drift that itself goes stale would be a poor joke. Two safeguards:

- This wiki is published from version control, so every change to it is reviewable and dated. See [[Editing-This-Wiki]].
- [[Remediation-Checklist]] carries a re-audit item. The drift-prone facts — Slack invites, event channels, season length — are exactly the ones that should eventually be checked by a link-checking job in this repo rather than by a person remembering.
