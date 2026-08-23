# Marketing Practices

What CivicTechWR actually publishes, drawn from every source we could retrieve on **2026-08-23**. This is the observed practice, not a proposal — the raw material sits in [`marketing/archive/`](https://github.com/CivicTechWR/core/tree/main/marketing/archive).

Decisions and tooling are on [[Marketing]]. This page is evidence.

---

## The headline

**Our content pipeline stopped in September 2025 and has not restarted.** Not the blog alone — recaps, blog and social all went quiet together.

| Season | Dates | Recaps written | Blog posts |
| --- | --- | --- | --- |
| 4 | Mar–Jun 2025 | 11 | 2 |
| 5 | Jun–Sep 2025 | 12 | 1 (finale) |
| 6 | Sep–Dec 2025 | **0** | **0** |
| 7 | Jan–Apr 2026 | 2 | **0** |
| 8 | May–Aug 2026 | 1 | **0** |

Seasons 4 and 5 had near-complete weekly recap coverage. Then it stops. The last recap is 2026-05-14 (Season 8 weeks 1–2); the season runs to 2026-08-26 with nothing since.

This matters for planning: there is **no running content engine to harvest**. Restarting the recap habit is itself a task, not a given.

---

## Channels, by actual use

| Channel | Reach | Output | State |
| --- | --- | --- | --- |
| **LinkedIn** | 213 followers | Regular, on-brand, best-produced | **The real channel** |
| **Luma** | — | 40 events, unbroken weekly cadence | Healthy |
| **Discourse** | Members only | 28 recaps, stalled since May | Stalled |
| **Blog** | Public | 11 posts ever, silent 11 months | Stalled |
| **Bluesky** | **8 followers, 1 post** | Created 2026-03-08, posted once | Effectively dead |
| Instagram / Threads / Facebook | Unknown | Not retrievable without login | Unmeasured |

Two things stand out. **LinkedIn is doing the real work** and is the only channel with a consistent voice. **Bluesky is linked prominently in the site footer and has one post and eight followers** — we are advertising a channel we do not use.

---

## Post types we already write

Derived from the LinkedIn archive. This is a de facto taxonomy — nobody wrote it down, but it is consistent.

| Type | Example | Reactions |
| --- | --- | --- |
| **Speaker announcement** (advance) | *"This month, we're welcoming guest speaker Kristy Guthrie…"* | 2 |
| **Speaker lineup / date change** | *"📅 Heads up: we have new dates for our guest speaker lineup!"* | 2–3 |
| **Speaker recap** (after) | *"We had a wonderful guest speaker last week…"* | **14** |
| **Season showcase promo** | *"Join us on August 26 for our Season 8 Showcase!"* + project list | **11** |
| **Countdown** | *"1 week! That's how long is left until our Season 7 Project Showcase"* | 9 |
| **Day-of reminder** | *"Today is the day! Join us TONIGHT…"* | 4 |
| **Mid-season call to action** | *"We're mid-season — the perfect time to jump in"* (carousel) | **10** |
| **Pitch night promo** | *"This week, we'll be hosting our Season 8 Pitch Night!"* | 2 |
| **Partner amplification** | Reshared CommuniHacks | 143 |

**What performs:** recaps and human interest (14), showcase promos naming real projects (11), mid-season "come join" carousels (10).
**What doesn't:** bare logistics — pitch night, day-of reminders, speaker announcements without a story (2–4).

The lesson is legible: **posts with a person or a project in them outperform posts with only a date in them by roughly 4×.**

---

## Conventions we already follow

Consistent enough to write down as-is.

**Emoji as field labels** — 📅 date · 📍 location · 📣 speaker · 🎤 talk · 🛠️ build · ✅ get involved · 👉 register · 👀 curiosity hook

**Standard event block**

```
📅 Wednesdays, 5:30 – 8:00 p.m.
📍 The Builders Club (165 King Street W)
👉 Register: <luma link>
```

**Speaker format** — `📣 Name | Date`, then one line on who they are and why it matters.

**Closing CTA** — every post ends with a link, usually Luma or an `lnkd.in` short link.

**Voice** — warm, plain, invitational. *"Whether you code, design, analyze, organize, or just care about the community, there's a seat for you at the table."* No jargon, no corporate register, occasional humour (*"PS there shall be food"*).

---

## Inconsistencies worth fixing in the guide

**Venue name — six variants across ten posts**
`The Builders Club` · `Builder's Club` · `the Builders Club in Kitchener (165 King St W)` · `The Builders Club at 165 King Street W` · `Downtown Kitchener Builder's Club` · `the Builder's Club in DTK`
Pick one, with and without the apostrophe settled.

**Event titles on Luma — renamed mid-stream**
`Civic Tech WR` for 12 events (Nov 2025 – Mar 2026), then `CivicTechWR Hacknight` from 2026-03-18 onward. Speaker events use three different separators: ` - with X of Y` · ` - Guest Speaker X, Y` · ` with guest speaker X`. Showcases use ` | Season N`.

**Start time — moved twice, and a sixth variant is in the wild**
Luma shows `19:00` (Nov 2025 – Feb 2026) → `18:30` (Feb–Mar 2026) → `17:30` (Mar 2026 onward).
A LinkedIn post from ~3 months ago says **"We meet on Wednesday at 5:45 PM"** — a time that appears in no other source. Other LinkedIn posts correctly say 5:30–8:00. See [[Drift-Findings]] finding 11.

**Link shorteners — three in use**
`luma.com/...` direct, `lnkd.in/...` (LinkedIn auto), and we self-host **Shlink** at `s.ctwr.org`, which is used for none of it and would give us click data.

---

## Event programming, observed

40 events, 2025-11-05 → 2026-08-26. Weekly Wednesdays with deliberate breaks (late December, Canada Day week, the week after a showcase).

| Type | Count |
| --- | --- |
| Hacknight | 27 |
| Showcase | 3 |
| Pitch Night | 3 |
| Speaker night | 3 |
| Hackathon (mini / ideation) | 2 |
| Social (holiday party) | 1 |
| Partner event | 1 |

**Season shape**, confirmed by our own marketing: Pitch Night → Ideation/Mini Hackathon → build weeks → Showcase. A LinkedIn post describes Season 7 as *"the last 16 weeks"* — which contradicts the documented 12-week season and matches the ~15–16 weeks measured in [[Drift-Findings]] finding 06. **Our public marketing is more accurate than our internal guideline.**

Roughly one guest speaker a month during a season, which matches the stated intent in the volunteer roles post.

---

## What this suggests for the guide

1. **Write the post-type taxonomy down** — nine types already exist and are used consistently. That is most of a guide.
2. **Lead with people and projects, not dates.** The engagement data is unambiguous.
3. **Fix the venue name and event-title conventions.** Cheap, and they are the most visible inconsistencies.
4. **Decide about Bluesky** — commit to it or remove it from the footer. One post and eight followers while linked from the homepage is the worst of both.
5. **Restart recaps before planning a blog cadence.** The recap habit was the input to everything else, and it is not currently running.
6. **Route links through Shlink** so posts become measurable at no extra cost.
