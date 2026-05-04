---
name: repurpose-planner
description: Turn one piece of long-form content into platform-specific repurposing plans (TikTok, IG carousel, LinkedIn, X thread, YouTube short, newsletter). Each output has a unique angle for that platform, not just a reformatted clip.
---

# Repurpose Planner

Most "repurposing" is dropping the same content on every platform. That doesn't work — each platform's audience wants something different. This skill generates *platform-native* plans, each with its own angle.

## Instructions for Claude

### Step 1: Get the Source Content

Ask the user for ONE of:
1. **Paste the content directly** (transcript, article, post)
2. **Summarize it** in 5–10 sentences (the user's choice)
3. **Path to a file** in the project directory (transcript, doc)

If the user describes the content vaguely ("my new video about productivity"), push for the actual content — you can't repurpose what you can't read.

### Step 2: Identify the Core Insight

Read the source. Extract:

- **The single most quotable sentence** (the line that, on its own, would stop a scroll)
- **The strongest 1–2 specific moments** (a number, a story, a result)
- **The 3–5 distinct ideas** within the source
- **Who the source was originally for** (audience hint from the framing)

Display this back to the user briefly:
```
## Source content — what I'm working with

**The single most quotable line**: "[line]"
**Strongest moments**: [list]
**Distinct ideas inside**: [list]
**Original audience**: [audience]

Confirm this before I plan? Type "go" or correct anything off.
```

### Step 3: Pick Target Platforms

Ask:
```
Which platforms should I plan for? (Pick any combination.)
- TikTok / IG Reels short (60s vertical)
- IG carousel (5–10 slides)
- LinkedIn post (long-form text)
- X / Twitter thread (5–9 tweets)
- YouTube Shorts (60s vertical, slightly different from TikTok)
- Newsletter section (200–400 words)

Default: all of them. Type a list to narrow.
```

### Step 4: Generate Platform-Specific Plans

For EACH selected platform, generate a plan using the conventions below. Critically: **each plan must have a unique angle**. The same content, framed differently per audience.

---

#### TikTok / IG Reels short

```
## TikTok / IG Reel — 60s

**Angle for this platform**: [what the TikTok audience cares about]
**Pulled from source**: [which moment / idea]

**New hook (re-edited)**: "[hook]"
**Shot list**:
1. [Shot] — [purpose]
2. [Shot] — [purpose]

**Spoken script** (approx 60s):
[Full script with timing — this is mostly a re-cut of the source, but with a new hook for the algorithm]

**On-screen text key beats**:
- 0–2s: [text]
- [Nbeat]: [text]

**Caption**: [1–2 sentences max]
**Hashtags**: [3–5]
```

TikTok angle bias: tease + payoff, fast cuts, specific moments, less "context", more "here's the thing". Audiences scroll fast — earn the second second.

---

#### IG carousel

```
## IG Carousel — [N] slides

**Angle for this platform**: [why this works as a carousel — usually because it benefits from slow-pace, swipeable structure]
**Pulled from source**: [which idea]

**Slide 1 — Hook slide**
Title: "[Hook title]"
Body: [1 line]
Visual cue: [bold text / number / question]

**Slide 2 — [Section name]**
[Title and body]

[... slides ...]

**Final slide — CTA / payoff**
[Wrap with the takeaway and a soft CTA]

**Caption (long)**: [3–5 short paragraphs, expands on what the carousel doesn't fit]
**Hashtags**: [10–15]
```

IG carousel angle bias: educational, listicle-friendly, swipe rewards. Make slides visually scannable.

---

#### LinkedIn post

```
## LinkedIn post — [N] words

**Angle for this platform**: [LinkedIn audience wants opinions + lessons + stories, not videos]
**Pulled from source**: [which moment]

**Post**:

[Hook line — story open or contrarian works best]

[Empty line]

[2–4 short paragraphs — usually first-person narrative, then a takeaway, then 3–5 line spaced bullets if applicable]

[Empty line]

[Final line — often a question to invite comments, or a single-line takeaway]

**Hashtags**: [0 or 3 max — LinkedIn does NOT like hashtag stuffing]
**Best post time**: Tue/Wed/Thu morning EST is the standard recommendation.
```

LinkedIn angle bias: story → lesson → takeaway. First-person + specific = credibility. Don't repost a TikTok caption.

---

#### X / Twitter thread

```
## X thread — [N] tweets

**Angle for this platform**: [X audience wants compressed, punchy ideas — threads work when each tweet earns the next]
**Pulled from source**: [which idea]

**Tweet 1** — Hook tweet
"[Hook, ≤240 chars, often ends with a setup like 'Here's how:']"

**Tweet 2** — [section]
"[Body, ≤240 chars]"

[... continue ...]

**Final tweet** — CTA / loop-back
"[Often references the hook again, then a soft CTA like 'follow for more' or 'reply with a [thing] and I'll DM the [resource]']"
```

X thread angle bias: each tweet is a deliverable. No throat-clearing. Numbered or labeled tweets often outperform.

---

#### YouTube Shorts

```
## YouTube Short — 60s

**Angle for this platform**: [YouTube algo rewards completion + retention — Shorts hooks are slightly more "click-y" than TikTok]
**Pulled from source**: [which moment]

**Hook** (often more clickbait-y than TikTok): "[hook]"

**Beats**:
[Same structure as TikTok script but tilted toward completion — list-style content, before/after, specific countdowns work well here]

**Title**: "[≤60 chars]"
**Description**: "[2–3 sentences, hashtag-light]"
**Hashtags**: [3–5]
```

YouTube Shorts angle bias: clearer titles than TikTok, list/countdown formats, completion is the goal.

---

#### Newsletter section

```
## Newsletter — 200–400 words

**Angle for this platform**: [Subscribers chose to be there — they want depth, the parts you couldn't fit in a 60s clip]
**Pulled from source**: [which idea + which depth]

**Section title**: "[Title]"

[Opening paragraph — different from the video hook; can assume the reader wants to be there]

[Middle paragraphs — the depth the video skipped, OR the meta lesson behind the video]

[Closing paragraph — connect to a CTA: a link to the video, a tool you use, a follow-up post]
```

Newsletter angle bias: depth + meta. Video tells the story; newsletter tells the *lesson behind* the story.

---

### Step 5: Highlight What's NOT a Repurpose

After the plans, add:

```
## What I deliberately didn't repurpose

[1–2 things from the source that DON'T translate well, with brief reason]

Example:
- The 3-minute technical deep-dive in the middle is too long for short-form
  and too narrow for LinkedIn. It belongs in a blog post or a longer YouTube
  video, not in any of these formats.
```

This signals taste and stops the user from spamming the same content blindly.

## Hard Rules

1. **Each platform plan must have its own angle.** If you can copy-paste the same content across platforms, you've failed. The angle line at the top of each plan must be platform-specific.

2. **Don't fabricate details from the source.** If the source doesn't have a specific number, don't invent one. Use the source's actual language for quotes/moments.

3. **Honor each platform's culture:**
   - TikTok: short, specific, tease + payoff
   - IG carousel: visual + listicle
   - LinkedIn: story → lesson, no hashtag spam
   - X: each tweet earns the next, compressed
   - YouTube Shorts: completion-driven, list/countdown friendly
   - Newsletter: depth + meta, hyperlink-friendly

4. **The user's original audience matters.** A dev's content shouldn't be repurposed for a fashion audience. Stay near the original audience unless asked.

5. **Mention what NOT to repurpose.** Section at the end. Shows judgment.

## Error Handling

**Source content too short to repurpose meaningfully:**
```
This source is [N] words / sentences — too thin to repurpose into platform-
specific plans without padding. Either:
1. Send a longer source (transcript, article, post)
2. Pick fewer platforms (for a 30-word source, 1 LinkedIn post or 1 X thread
   is the realistic max)
```

**User wants me to "just rewrite it for each platform":**
```
Same content rewritten = the trap most repurposing tools fall into. Different
platforms want different *parts* of the source. Let me pick the part for each
platform — that's what makes it work.
```

## Integration with Other Skills

- **Captions**: After repurposing, use `/caption-pack` for tighter platform-specific captions on the actual posts
- **Voice**: Apply `/brand-voice` to make all outputs match a saved profile
