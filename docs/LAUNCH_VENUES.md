# Launch venues for CodexIsland

Researched 2026-05-06 by directly fetching each platform's rules.
Sites are categorized by **friction**, not by **reach** — a 250k-sub
sub you can post in today is worth more than a 6M-sub one that bans
the post on submit.

Use UTM links so the PostHog dashboard ("DMG downloads by referrer")
attributes correctly:

```
https://codexisland.com?utm_source=<venue>&utm_campaign=launch_v0_1
```

Suggested `utm_source` values: `hn`, `reddit_macapps`, `reddit_claudecode`,
`x`, `linkedin`, `ph`, `awesome_claude_code`, etc.

---

## 🟢 GREEN — post today, no friction

| Venue | Reach | Format / where | Notes |
|---|---|---|---|
| **Show HN** | giant (HN front page = 50-200k impressions on hit) | Submit at https://news.ycombinator.com/submit. Title: `Show HN: CodexIsland – Claude Code & Codex usage in your MacBook notch`. URL: GitHub repo OR `codexisland.com`. First comment: 2-3 paragraphs explaining why you built it. | No karma/age requirement. Don't ask for upvotes (algo penalty). Tue/Wed 9-11AM PT typically peak window. Shows on `/shownew` first, then `/show` after small point threshold. |
| **r/SideProject** (704k) | medium-large, indie-friendly | Direct post, GIF or screenshot in image field, link in body | No formal self-promo restrictions in rules. Best fit Reddit-side for "I built this". |
| **r/ClaudeCode** (260k) | exact audience | Required flair. Disclosure required: state what it does, who it's for, any costs (free OSS), your relationship (built it). | "Stay on Topic — coding workflows, agents, MCP, tutorials, troubleshooting, or developer practices" — CodexIsland fits. |
| **r/AnthropicAi** (2.2k) | tiny but exact | Direct post | No real rules listed; small sub, won't move the needle alone but easy +. |
| **X (Twitter)** | algo-dependent | Thread: hook tweet with notch GIF, 3-4 tweets walking through the spend screen, last tweet = install link | No platform rules. Add UTM. Reply to your own thread within 5 min for engagement boost. |
| **LinkedIn** | network-dependent | Single post with notch GIF + GitHub link | Low-friction, mostly reaches your network. |
| **Indie Hackers** "Show IH" | medium | https://www.indiehackers.com — use **SHOW IH** flair | 1 promo per product. Some posts mention 45-day account-age soft rule; check if your account is old enough. |

---

## 🟡 YELLOW — post with caveats

| Venue | Reach | Caveat | Action |
|---|---|---|---|
| **r/ClaudeAI** (820k) | massive, exact audience | "Showcase your project... must be clear the project was built with Claude/Claude Code OR specifically for Claude users" | Frame as: "I built this *with* Claude Code *for* Claude Code users — local-only Claude usage tracker." Use the showcase flair. |
| **r/macapps** (224k) | exact audience | **10 LOCAL karma required first** — must comment 10 helpful comments in r/macapps before posting. **1 promo per developer per 30 days.** GitHub releases qualify as "official distribution channel". | Spend 1-2 days commenting helpfully on other people's macapp posts to earn karma, then post. |
| **r/MacOS** (568k) | broad Mac audience | **Promotional posts ONLY on SATURDAYS (UTC).** Limited to MAS apps OR "reputable, established GitHub repositories" — your repo qualifies but is brand new, mod judgment call. | Schedule for next Saturday UTC. Lead with the privacy story (local-only) to differentiate. |
| **r/apple** (6.3M) | broad Apple audience | **Self-promo ONLY on SUNDAYS, devs only.** | Schedule for next Sunday. Be ready for downvote brigades — apple sub is hostile to anything not first-party. |
| **r/OpenAI** (2.7M) | massive, half-relevant | 1/10 self-promo rule. Concise, accurate titles. | Lead with the Codex angle, not the Claude angle. Frame as "Track your ChatGPT Pro / Codex CLI usage in the notch." |
| **r/opensource** (349k) | OSS-friendly | Use "Promotional" flair. Code must have LICENSE (MIT ✓). | Title should match repo title ("CodexIsland"), not editorialize. |
| **PR → `hesreallyhim/awesome-claude-code`** (42.6k stars) | high — list traffic + GitHub stars compound | Add CodexIsland to the relevant section (probably "Apps" or "Tools" — check current README structure). | One PR, low effort. Big list = sustained passive traffic. |
| **PR → `jaywcjlove/awesome-mac`** | medium-high — high-trust list | Add to "Menu Bar Tools" section under Developer Tools. Follow contributing guide. | One PR, low effort. |
| **AlternativeTo** | low per-day, sustained | Submit a new app entry at alternativeto.net (free, account required). List as alternative to Raycast, BetterTouchTool usage tracking, etc. | One-time setup. Compounds over months. |
| **Anthropic Discord / OpenAI Discord** | moderate | Each typically has a `#self-promo` or `#community-projects` channel. Rules vary — confirm before posting. | Post in self-promo channels only. Don't DM. |
| **Product Hunt** | very high if hits #1 | Account 7+ days old. Compete by upvotes within 24h window. Featured at midnight PT. | Don't fire off casually — needs prep: thumbnail, gallery shots, maker comment, soft network warm-up. Plan a separate launch day for this. |

---

## 🔴 RED — won't accept this, skip

| Venue | Why |
|---|---|
| **r/programming** (6.8M) | Explicit "No Product Promotion / 'I Made This' Project Demo Posts" + "April Trial: No LLM-related posts" |
| **r/startups** (2M) | "No direct sales, advertisements, or promotional posts of any kind" |
| **r/MachineLearning** (3M) | Research-only sub; tools/products off-topic |
| **r/LocalLLaMA** (712k) | Sub is for **local** LLMs; CodexIsland tracks remote Claude/OpenAI APIs — off-topic |
| **r/SaaS** (680k) | CodexIsland is free OSS, not a SaaS. Off-topic. |
| **r/cursor** (135k) | Only marginally relevant (CodexIsland doesn't track Cursor's own usage); 1/10 rule + relevance gate |
| **Lobsters** | **Invite-only** (no signup). Need an existing user to invite you. |
| **Launch HN** | YC-funded companies only. |
| **r/MacOSBeta** | Audience is beta-testers, not productivity tool installers |

---

## Suggested launch sequence

If you have ~3-4 days of energy for this:

**Day 1 (Tuesday/Wednesday morning PT):**
- Show HN (the big swing — best ROI by far)
- r/SideProject + r/AnthropicAi + r/ClaudeCode (parallel, low friction)
- X thread (timed to coincide with Show HN)

**Day 2:**
- r/ClaudeAI (with Claude-Code framing)
- r/OpenAI (with Codex framing)
- r/opensource
- PR to `awesome-claude-code` and `awesome-mac`
- AlternativeTo listing

**Day 3 (Saturday UTC):**
- r/MacOS

**Day 4 (Sunday UTC):**
- r/apple

**Karma-grinding side track (start Day 1 in parallel):**
- Spend 30 min commenting helpfully on r/macapps posts each day. By Day 4-5 you have 10 local karma → can post there.

**Separate, planned launch day (week+ later):**
- Product Hunt — needs a real launch-day plan, not a casual fire-off.

---

## What NOT to do

- **Don't ask for upvotes.** HN, Reddit, PH all algo-detect this. Permanent shadow-ban risk.
- **Don't crosspost simultaneously.** Reddit detects this. Stagger by hours.
- **Don't editorialize titles.** "BLOWN AWAY by my new tool 🤯" gets removed by mods.
- **Don't link-shorten.** Many subs ban shortened URLs (r/macapps explicit).
- **Don't repost if the first one flopped.** That's mod-ban territory on most subs.
- **Don't reply defensively.** If someone says "this is just X", explain the difference once and move on.
