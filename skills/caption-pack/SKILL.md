---
name: caption-pack
description: Generate platform-optimized captions and hashtag sets for a piece of content. Different lengths, different voices, platform-specific conventions for IG, TikTok, LinkedIn, X, YouTube Shorts.
---

# Caption Pack

Same content + same caption everywhere = mediocre engagement on everywhere. This skill writes platform-specific captions, each tuned to that platform's culture and length conventions.

## Instructions for Claude

### Step 1: Gather Inputs

Ask for:

1. **Content** — what's the post? (Paste the script, describe the video, or summarize the carousel)
2. **Platforms** — which ones? (default: all)
3. **CTA** — what should the viewer do?
4. **Voice profile** (optional) — load a saved brand voice if mentioned
5. **Audience** (optional) — who's this for? Helps tune hashtags and tone

### Step 2: Identify the Single Most Quotable Line

Before writing platform-specific captions, extract the ONE line from the content that would stop a scroll. This becomes the core of every caption — re-framed per platform.

Display:
```
**The line I'm building captions around**: "[line]"

If this isn't the right line, tell me which is.
```

### Step 3: Generate Platform-Specific Captions

#### Instagram (post or Reel)

```
## Instagram caption

**[Hook line — usually the quotable line, or a curiosity-gap reframe]**

[1–3 short paragraphs separated by blank lines.]
[Build with line breaks — IG truncates after ~125 chars; the hook line must do its job before "more".]

[Optional: a list of 2–4 short bullet points or short lines.]

[CTA paragraph — one short line.]

.
.
.

#hashtag1 #hashtag2 #hashtag3 [...8–15 total]
```

**IG hashtag strategy**: 8–15 hashtags. Mix of:
- 2–3 broad (millions of posts)
- 4–6 medium (10k–500k posts)
- 3–6 niche (under 10k)

Place hashtags at the bottom with `.` line breaks above them, OR in the first comment. Don't pepper them through the caption.

---

#### TikTok caption

```
## TikTok caption

[1–2 sentences max. The first 3–5 words must hook because TikTok cuts off captions hard.]

[Optional: 1 short CTA line.]

#hashtag1 #hashtag2 #hashtag3 [3–5 total]
```

**TikTok hashtag strategy**: 3–5 hashtags. Keep it focused. Trending hashtags only if genuinely relevant — TikTok algo punishes irrelevant trends.

---

#### LinkedIn caption / post

```
## LinkedIn post

[Hook line — story-open or contrarian usually outperforms]

[Empty line]

[Setup paragraph — 2–4 sentences. Specific, narrative, first-person.]

[Empty line]

[Body — could be short paragraphs OR a 3–7 line bulleted/numbered list. Don't mix without reason.]

[Empty line]

[Lesson / takeaway — 1–2 lines]

[Empty line]

[Final line — often a question that invites comments, OR a single-line CTA]

[0 hashtags, OR 3 max — appended at the end on their own line]
```

**LinkedIn hashtag strategy**: 0 or 3 max. The algorithm doesn't reward stuffing. Use #ContentMarketing #BuildInPublic #SaaS — broad professional tags only.

**LinkedIn length**: ~600–1300 chars is the sweet spot. Too short = low dwell. Too long = "see more" cuts off.

---

#### X / Twitter

```
## X / Twitter (single tweet)

[≤240 chars. The tweet IS the caption. No hashtags.]
```

**If a thread is more appropriate**:
```
## X / Twitter (thread)

**Tweet 1** (hook): [≤240 chars]
**Tweet 2**: [≤240 chars]
[... 3–7 tweets total]
```

**X hashtag strategy**: 0 hashtags by default. They reduce engagement on X. Exception: a single, branded, or live-event hashtag is fine.

---

#### YouTube Shorts

```
## YouTube Shorts caption

[2–3 sentences. More descriptive than TikTok — YT is a search platform, so include searchable language.]

[CTA line.]

#hashtag1 #hashtag2 #hashtag3 [3–5 total, plus #shorts]
```

**YouTube hashtag strategy**: Include `#shorts` always. 3–5 other hashtags. Searchable keywords matter more than trends here.

---

### Step 4: Output

Group all captions in a single output, clearly labeled per platform:

```markdown
# Caption pack

**Content**: [1-line description]
**Quotable line**: "[the line]"
**Voice profile**: [name or "default"]

---

## Instagram
[caption]

---

## TikTok
[caption]

---

## LinkedIn
[caption]

---

## X / Twitter
[caption]

---

## YouTube Shorts
[caption]

---

## Notes

- [Any platform-specific note — e.g., "LinkedIn version emphasizes the lesson; TikTok version emphasizes the moment"]
- [Hashtag rationale if non-obvious]
```

## Hard Rules

1. **Different captions per platform.** Don't paste the same caption across platforms. If a platform's caption could be lifted to another, you haven't done the work.

2. **Honor character / length norms.**
   - IG: long-ish OK, but hook in first 125 chars
   - TikTok: 1–2 sentences max
   - LinkedIn: 600–1300 chars
   - X: ≤240 per tweet
   - YouTube Shorts: 2–3 sentences

3. **Hashtag conventions per platform** (see strategies above). Don't stuff hashtags on LinkedIn or X. Don't under-tag on IG.

4. **Use the voice profile** if loaded. Apply tone, sentence patterns, vocabulary signatures.

5. **Don't fabricate details.** If the user said the video is about "switching from Webflow", don't invent a specific dollar amount they saved unless they told you.

6. **CTAs must be specific.** "Like and follow" is dead. "Comment 'starter pack' for the Notion template" or "Save this for later — you'll forget" works.

## Voice Profile Loading

If user mentions a saved voice (e.g., "in my mintlooks voice"):

```bash
cat .claude/brand-voices/[brand].md 2>/dev/null || cat ~/.claude/brand-voices/[brand].md
```

Apply the voice across all platforms. The voice's rules don't change per platform — only the format does.

## Error Handling

**Content description too vague:**
```
"My new video" isn't enough to write captions around. Tell me:
- The hook (what's said first)
- The core idea (what the viewer learns / feels)
- One specific moment or detail

I'll write platform-specific captions from there.
```

**User wants the same caption everywhere:**
```
You can do that — but you'll lose engagement. Each platform's audience expects
different framing. Want me to:
1. Generate one caption you can paste everywhere (lower performance)
2. Generate platform-specific captions (recommended)
```

## Integration with Other Skills

- **Before**: `/repurpose-planner` to plan the actual content per platform — captions follow naturally
- **Voice**: `/brand-voice` to load the brand profile
