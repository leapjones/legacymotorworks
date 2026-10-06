# Legacy Motorworks Blog

Static pages served at `legacy-motorworks.com/blog`. Plain HTML and one stylesheet, deployable to Vercel (see `/vercel.json`, which serves `spec-e46-cost.html` at `/blog/spec-e46-cost`) or uploaded to a GHL custom site.

## Files

| File | What it is |
|---|---|
| `index.html` | Blog home: post list and checklist signup |
| `spec-e46-cost.html` | Draft: what it costs to race Spec E46 |
| `buying-a-used-spec-e46.html` | Draft: how to buy a used Spec E46 |
| `control-arm-bushings.html` | Draft: solid control arm bushings |
| `_post-template.html` | Copy this to start a new post |
| `blog.css` | Shared styles, built to tokens v2 |
| `feed.xml` | RSS feed |
| `sitemap.xml` | Blog sitemap |

## Every post carries

- One question it answers, in the `FAQPage` JSON-LD and the on-page "Short answer" block, with the same text in both
- `BlogPosting` JSON-LD with Peter as author and Legacy as publisher
- A canonical URL on `https://legacy-motorworks.com/blog/<slug>`
- A "Get your buying checklist" button to `/inspection-checklist`, and the author box with race results

## Publishing a post

A post goes live only after Peter signs off on every line.

1. Peter supplies every `[PJ: ...]` bracket. Delete the bracket span once the value is in.
2. Remove the `noindex` meta line and the red DRAFT banner.
3. Replace every `PUBLISH_DATE` (JSON-LD uses `YYYY-MM-DD`, the byline uses `Month D, YYYY`).
4. Add a `<pubDate>` to the item in `feed.xml` and a `<lastmod>` in `sitemap.xml`.
5. Remove `noindex` from `index.html` when the first post goes live.
6. Run the gate below. Zero hits.

```sh
grep -rniE "—|–|\bseen\b|luxury|premium|exclusive|unlock|hack|guru|leverage|holistic|delve|impactful|turnkey|game-changer|next level|elevate|honest|PUBLISH_DATE|\[PJ:" blog/*.html
```

## Hard rules

- Pages say what the Legacy Standard checks, never how. No build sheet or measurement method, ever.
- No number without a source or Peter's sign-off. Car prices are Legacy's market read and get rechecked.
- Class rules are attributed to NASA. Nothing implies Legacy governs the series.
- No competitor is named or criticized.
- The Build Journal and Phone-a-Friend aren't launched. No post mentions them.

## Still to wire up

- GHL form embed and delivery email on `/inspection-checklist.html` (name, email, interest level). It's the only form, so every post sends signups to one place
- Source link for the 2025 NASA NorCal championship (LJ-confirmed, no public link yet)
- Confirm the live site's contact page path (nav links to `/contact`)
- Add `Sitemap: https://legacy-motorworks.com/blog/sitemap.xml` to the main site's robots.txt
- Add a Blog link to the main site navigation
