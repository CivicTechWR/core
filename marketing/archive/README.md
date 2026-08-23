# Marketing archive

Snapshot of CivicTechWR's outward-facing output, captured **2026-08-23**. Raw material for [Marketing Practices](https://github.com/CivicTechWR/core/wiki/Marketing-Practices) and for anyone writing the marketing guide.

This is a point-in-time archive, not a live sync. Re-capture at season end.

## What's here

| File | Source | Coverage | Complete? |
| --- | --- | --- | --- |
| `luma-events.csv` | Luma ICS feeds (calendar + user), no auth | 40 events, 2025-11-05 → 2026-08-26 | Yes for this window |
| `linkedin-posts.md` | Public company page HTML | 10 posts, ~5 months | **No** — only what LinkedIn shows logged-out |
| `bluesky-posts.md` | AT Protocol public API | 1 post — the account's entire history | Yes |
| `discourse-recaps.csv` | Discourse API, Recaps category | 28 recaps, 2025-02-19 → 2026-05-14 | Yes |
| `blog-posts.csv` | `CivicTechWR/blog` repo, `_posts/` | 27 files: 11 published, 3 drafts, 12 theme demos, 1 undated | Yes |

## What's missing, and how to get it

**Instagram** — not retrievable without authentication. The public profile is a JavaScript shell: no `og:` tags, no post data, nothing to parse. Options:

1. **Meta Accounts Center → Download your information** — full export, no developer setup, needs account access. Easiest path.
2. **Instagram Graph API** — requires the Business/Creator account linked to a Facebook Page plus a Meta app. Posting to your own account needs no App Review, so this is less work than it sounds.

**LinkedIn (full history)** — the 10 posts here are only what the logged-out page exposes. A complete export needs page-admin access, or the Community Management API (partner-programme application).

**Facebook and Threads** — not attempted. Same Meta export path as Instagram.

**Postiz** — if any of this was scheduled through Postiz, it holds its own history. Worth checking before doing manual exports.

## Provenance

Feeds used, for re-capture:

- Luma calendar — `api2.luma.com/ics/get?entity=calendar&id=cal-BVpgpDCgYaCqcPx`
- Luma user — `api.luma.com/ics/get?entity=user&id=icssk-uDZAZcDKUakEUYt`
- Bluesky — `public.api.bsky.app/xrpc/app.bsky.feed.getAuthorFeed?actor=civictechwr.bsky.social`
- Discourse — API key, `/c/recaps/6.json`
- Blog — `gh api repos/CivicTechWR/blog/contents/_posts`

The two Luma feeds overlap; the calendar feed is the superset (40 vs 17 events). Merged and de-duplicated here.
