---
name: devdroid-blog-publisher
description: Research, draft, review, and publish sourced bilingual articles for the devdroid.club blog. Use when Codex needs to monitor technology sources, propose blog topics, prepare Russian-first EN/RU posts, verify claims and dates, connect a post to a d.d.c. service, add or edit BLOG_POSTS in index.html, validate a blog change, or prepare publication through GitHub Pages.
---

# Devdroid Blog Publisher

Create useful editorial analysis for d.d.c., not a generic news feed. Treat Russian as the drafting language and English as an adaptation. Never publish, commit, merge, or push without explicit user approval.

## Load project context

Before blog work, read:

1. `design.md` for the locked design system and blog variant.
2. `index.html` around `BLOG_POSTS`, blog rendering, routing, and i18n.
3. `llms.txt` and `sitemap.xml` when publication or information architecture may change.
4. [references/editorial-policy.md](references/editorial-policy.md) for topic selection and quality gates.
5. [references/sources.md](references/sources.md) when discovering or verifying a topic.
6. [references/post-schema.md](references/post-schema.md) when drafting or editing a post.

Use Hallmark as well when changing blog UI or layout. Do not redesign during a content-only task.

## Choose the operation

- **Discover:** collect recent candidates, verify dates, score relevance, and return a shortlist. Do not edit.
- **Draft:** write a Russian-first draft and English adaptation with sources. Do not edit production unless asked.
- **Prepare:** add or update structured post data, then validate locally. Do not commit or push.
- **Publish:** prepare the change, show the exact article and checks, then require explicit approval before commit or push.
- **Automate:** design or maintain a draft-to-PR pipeline. Default to pull requests and human approval; never direct scheduled pushes to `main`.

## Research workflow

1. Start from service directions: product, websites, bots/automation, AI, MVP, support, or audit.
2. Give priority to AI and development for sports venues, sports clubs, booking systems, membership sales, schedules, CRM, access control, analytics, and online platforms.
3. Use discovery sources to find leads, then open the cited primary source. A Habr, Reddit, KOD, or awards post is not sufficient evidence by itself when an official announcement, documentation, repository, paper, or project page exists.
4. Confirm the event date and publication date. Treat relative dates as unsafe; record exact dates.
5. Cross-check material claims with at least one primary source. Use two independent sources for security, benchmark, market, legal, or financial claims.
6. Reject rumors, unsourced metrics, disguised advertising, duplicate topics, and stories with no concrete consequence for the audience.
7. Never copy an article. Summarize facts and add d.d.c.'s practical analysis. Keep quotes short and attributed.

## Drafting workflow

1. Pick one primary service and at most two secondary services.
2. State what happened, why it matters, where it applies, limitations, and what a business should check next.
3. Draft Russian first for a Russian-speaking audience. Explain foreign and niche terms in plain Russian.
4. Adapt into natural English; do not translate mechanically.
5. Keep the tone calm, technical, and useful. Avoid hype, invented certainty, promotional adjectives, fake urgency, and fabricated metrics.
6. Include a source label and direct source URL. Distinguish source facts from d.d.c. inference.
7. Follow the schema and checklist in `references/post-schema.md`.

## Publication safety

- Treat every generated post as `draft` until the user approves it.
- Do not modify unrelated page copy, styles, routes, or existing posts.
- Preserve the current vanilla HTML/CSS/JS architecture unless the user approves a migration.
- Never expose credentials or place API keys in repository files.
- For automation, store secrets only in the hosting platform's secret store.
- Do not send messages, create PRs, commit, merge, or push unless the user explicitly requests that external action.
- Before any requested publish action, show: slug, RU/EN titles, source URLs, files changed, validation results, and destination branch.

## Validation

For a prepared content change:

1. Check the embedded JavaScript syntax.
2. Check slug uniqueness and valid `#/blog/<slug>` routing.
3. Check that RU and EN fields are complete and source URLs use HTTPS.
4. Check claims against the cited sources.
5. Open the blog index and post on desktop and mobile when browser control is available.
6. Check both language modes, long-title wrapping, source link, back navigation, keyboard navigation, and reduced motion.
7. Check `git diff` and confirm no unrelated changes.

Report validation honestly. If browser verification is unavailable, say so instead of claiming a visual pass.

## Automation target

Prefer this lifecycle:

```text
scheduled discovery -> scored candidates -> RU draft -> source check
-> EN adaptation -> validation -> preview/PR -> human approval -> merge -> Pages
```

The first implementation may keep `BLOG_POSTS` in `index.html`. For reliable recurring automation, recommend moving post data to a dedicated structured file, then later generating crawlable `/blog/<slug>/` pages with per-post metadata. Do not make either migration implicitly.
