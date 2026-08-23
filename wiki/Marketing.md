# Marketing

How CivicTechWR's outward-facing work — blog, social, photography, events, newsletter — is organised, what tooling already exists, and what still needs building.

This page carries the **narrative and the decisions**. The row-by-row inventory of which marketing process is defined where lives on [[Process-Index]] § Marketing, and the fixes are on [[Remediation-Checklist]] § Marketing. Nothing is restated across the three.

Compiled **2026-08-23**, during Season 8.

---

## Where the work is tracked

**[GitHub Project 46 — Marketing](https://github.com/orgs/CivicTechWR/projects/46)** is the working board. Items live in it as drafts or as issues in `core`.

**Fields**

| Field | Values |
| --- | --- |
| Content type | Blog · Social · Photo · Design asset · Newsletter · Outreach · Brand/guide |
| Channel | Blog · Instagram · LinkedIn · Bluesky · Threads · Facebook · Newsletter · Multiple |
| Start date / Publish date | The roadmap span — when work begins, when it ships |
| Effort | S (under an hour) · M (an evening) · L (multiple sessions) |

**Status** runs `Backlog → Ready → Drafting → Review → Scheduled → Published`.

`Scheduled` is its own column deliberately. "Written but not posted" is where volunteer content dies, and it should be visible rather than hidden inside "in progress".

**Views**

- **Triage** (table) — the inbox. New items get typed, dated and sized here.
- **Now** (board, by Status) — work in flight. Open this at organizers meetings.
- **Cadence** (roadmap, Start → Publish) — the view that shows gaps *before* they become silences.
- **Editorial** (board, Blog + Newsletter only) — long-form moves on a slower clock than social and gets crowded out when mixed with it.

---

## Tooling we already have

Two of these were discovered during the audit and are not referenced anywhere else in our documentation. **We are not short of tools. We are short of practice.**

| Tool | What it is | State |
| --- | --- | --- |
| **Postiz** | Self-hosted open-source social scheduler (a Buffer/Hootsuite equivalent). Runs in the `ctwr-apps` stack. | Running, unused for marketing |
| **Shlink** | Self-hosted URL shortener with click analytics. Also in `ctwr-apps`. | Running, not wired to anything |
| **Luma** | Event platform. Upstream of the website and Discourse — see below. | In active use |
| **Mailchimp** | Newsletter list. Signup form is live on the homepage. | Collecting addresses, **no sends** |
| **MediaKit** | Brandmarks (SVG + PNG), pre-sized social images, sticker PDF, favicons. Google Drive `Organizing/MediaKit/`. | Present, sized for channels we left |
| **Blog** | Jekyll, authors configured, author boxes, categories, pagination. | Built for cadence; silent since 2025-09 |

Service configuration lives in the private `ctwr-apps` repo.

**Postiz is the significant find.** It covers most of what we would otherwise build ourselves, and it already runs. **Shlink answers the "we don't measure anything" gap** — link tracking is a solved problem here, just an unused one.

Observed output across every channel is inventoried on [[Marketing-Practices]].

---

## How events flow today

Luma is not a peer channel. It is the **upstream node** everything else derives from.

```
Luma calendar ──► civictechwr.org next-meeting block   (fetch_luma_event.rb, at build)
              └─► Discourse Events category            (daily sync, ~10:00 UTC)
```

Both consumers read Luma's **public ICS feed**, which needs no API key.

**The facts propagate. The narrative does not.** Date, time, location and URL flow automatically to both surfaces. The description, the image and the framing land only on Luma and get retyped by hand for social — or never written at all.

That is the strongest argument for treating Luma as part of marketing rather than as event admin: it is the one artifact where writing good copy once improves three surfaces for free.

### The Discourse sync

Not a plugin. An external script calling the Discourse API as the `system` user, daily, creating a topic per new Luma event with `discourse-calendar` markup so each topic carries real event metadata.

**Its source is not in any CivicTechWR repository.** A scheduled job runs against production Discourse with an admin API key and nobody can point at the code. If it breaks, we cannot fix it; if the key leaks, we do not know where it is used. See [[Drift-Findings]].

### Per-event-type times

Luma publishes different times by event type — hacknights start **5:30 PM** (doors), showcases **6:00 PM**. Hardcoded copies elsewhere encode "hacknight proper" at 6:00 PM and are consequently half an hour off. Luma is the source of truth; nothing should restate it.

---

## Automating publishing: adopt or build

We can drive publishing from automation. The question is whether to route through Postiz or write our own integrations.

### What each platform actually allows

| Target | Feasible | Gate |
| --- | --- | --- |
| Bluesky | Yes, easily | None — free API, app passwords, no review |
| Instagram | Yes | Meta app; **no App Review needed** when posting to our own account |
| Threads | Yes | Same Meta path |
| Facebook Page | Yes | Same Meta path; 25 posts/day |
| LinkedIn (org page) | Hard | Community Management API partner programme — application + verified page |
| Luma — **read** | Yes, already do | None. Public ICS |
| Luma — **write** | Yes | **Luma Plus, $59/month billed annually** |

### Option A — route through Postiz

Postiz already holds the platform integrations. Automation calls one API instead of five, and we sidestep the Meta app and the LinkedIn partner programme entirely.

Costs: another self-hosted service to keep alive, and scheduling state lives outside version control.

### Option B — build our own

GitHub Actions calling each platform directly. Everything in version control and reviewable in a PR; no extra service.

Costs: we own five integrations and their token rotations. Realistically this means Bluesky first — free and trivial — and stalling on Meta and LinkedIn.

### Option C — both, split by job

Recommended. **Postiz for publishing**, since it already solves the hard part. **GitHub Actions for the parts Postiz does not do**: reading the Luma ICS to generate board items, link-checking drift-prone facts, and eventually minting Shlink URLs so posts are measurable.

Whatever we choose, two constraints hold:

- **Never auto-post on merge.** A bad merge must not reach the public. Use manual dispatch or a required reviewer, the same way the wiki publish workflow refuses to run on a broken source.
- **Actions cron is imprecise.** Scheduled runs can be delayed well past their slot. Fine for "sometime Thursday", wrong for "9:00 sharp".

### Terraform

Not for posts. Terraform models resources with a create/update/destroy lifecycle; a post is an *event*, with no meaningful update and a genuinely bad `destroy` semantic.

It **would** fit our GitHub org — repo settings, teams, branch protection, org security — which are exactly the June 2026 audit items still open and still manual. That is an infrastructure decision, not a marketing one.

---

## Processes: built, and to build

Detail and current locations are on [[Process-Index]]. Summary of state:

**Built**

- Marketing work intake and tracking — Project 46, with fields, four views and a status lifecycle
- Brand assets and boilerplate copy — in the MediaKit, usable today

**To build, in rough order**

1. **Blog contribution process** — `blog/README.md` links to a `CONTRIBUTING.md` that does not exist. This is the one process that would rebuild blog cadence and it currently 404s.
2. **Event page checklist** — creating the Luma event is named as a duty and defined nowhere. Needs a title convention (we have three separators doing the same job), description structure, image, and how far ahead to publish.
3. **Photo shot list and storage convention** — `Photos/YYYY/YYYY-MM-DD-event/`, plus a five-line shot list so a volunteer knows when they are done.
4. **Photo consent practice** — see Risks.
5. **Restart recaps, then build the recap → post pipeline.** Recaps are *not* currently running: 11 in Season 4, 12 in Season 5, then **0 in Season 6**, 2 in Season 7, 1 in Season 8. The habit stopped alongside the blog in late 2025. A recap is most of a short post already, but the input has to exist first. See [[Marketing-Practices]].
6. **Brand voice and tone** — one page. Nothing exists.
7. **Channel guidance** — which channel gets what. The current guide names channels we left and omits two we use.
8. **Measurement** — decide whether we measure reach at all. Shlink makes this cheap if we do.
9. **Per-season recurring items** — generate photo and promo items at season start rather than relying on weekly recall.

---

## Risks

Three items here are not backlog. They are exposure.

**No photo consent practice.** We assign a volunteer to photograph attendees at every event and publish the results, and `PrivacyPolicy.md` does not mention photos, images, video or likeness. Minimum viable: a line on the Luma event page, a sign at the door, a mention in the welcome — the Emcee role already greets newcomers. Close this before the next event shoot, not after.

**A newsletter nobody sends.** A live Mailchimp form collects addresses from people who then hear nothing. Note that **Luma already emails registrants** — so this may be redundant rather than neglected, and "take the form down" may be the honest call rather than the sad one. Compare list sizes before deciding.

**An unsourced production script.** Covered above. Highest bus-factor item found in the audit.

---

## One structural note

The marketing job is defined once, in the Season 8 volunteer roles post, and it **bundles four unrelated jobs into one slot**: maintain the Luma calendar, maintain social accounts, maintain the blog *and* newsletter, and take hacknight notes.

Three of those are weekly and time-boxed. The blog is the one that can silently slip — which is a plausible mechanic for why it went quiet in September 2025 while everything else kept running. Not neglect: the droppable item in an overloaded role.

Splitting the blog out is probably worth more than any tooling decision on this page.
