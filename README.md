# claude-ugc-skills

> Claude Code skills for UGC creators and short-form content makers. Hooks, scripts, brand voice, repurposing, captions — built by a creator who got tired of staring at blank docs.

I'm a UGC creator AND a developer. Most "AI content tools" treat content like a prompt completion problem — generate something, hope it sounds human, ship it. That misses everything that actually makes UGC work: a *real* hook, a *real* shot list, a voice that doesn't read like ChatGPT.

These skills are how I write content for [MintLooks Studio](https://mintlooks.studio) and my own channels. Each one is opinionated, narrow, and built around the way creators actually think.

## What you get

| Skill | What it does |
|---|---|
| `/hook-generator` | Give it a video idea + audience. Get 10 hooks across proven frameworks (curiosity gap, contrarian, before/after, story open, callout). Each tagged with the framework so you know *why* it works. |
| `/ugc-script` | Turns a brief into a 30s–90s UGC script with timestamps, shot types, B-roll cues, and on-screen text suggestions. **Won't invent results, errors, or testimonials** — asks you for the real thing. |
| `/brand-voice` | Loads a brand voice from 5+ writing samples, then helps you write new content in that voice. Saves voice profiles per brand so you don't re-train every time. |
| `/repurpose-planner` | Long-form content (a video, blog post, podcast clip, talk) → platform-specific repurposing plan: TikTok shorts, IG carousels, LinkedIn posts, X threads, YouTube shorts, newsletter. Each with an actual angle, not just "post a clip". |
| `/caption-pack` | Generates platform-optimized captions and hashtag sets for a piece of content. Different lengths and voices for IG, TikTok, LinkedIn, X, YouTube — no copy-paste-the-same-thing. |

## Why these are different

Most AI content tools fabricate. They invent stats, make up "results," put words in your mouth.

These skills do the opposite — they're **plans, not retellings**:

- A script is a *plan* for the video you're about to shoot. It points at where YOUR result, error, or testimonial goes — it doesn't invent one.
- A hook is a *frame* for the idea you already have. The skill picks the framework; you bring the substance.
- A brand voice is a *learned profile* from real samples you provide. No vibes, no "I think your brand is friendly and modern."

If you've ever felt the cringe of an AI-generated post, that's because the AI was guessing. These skills don't guess.

## Requirements

- [Claude Code](https://claude.com/claude-code) installed
- That's it. No API keys. No paid services.

## Install

### Option 1: User-level skills (recommended)

```bash
git clone https://github.com/ImTaegan/claude-ugc-skills.git
cp -r claude-ugc-skills/skills/* ~/.claude/skills/
```

Now `/hook-generator`, `/ugc-script`, etc. are available globally.

### Option 2: Per-project

```bash
cd your-content-folder
mkdir -p .claude/skills
cp -r path/to/claude-ugc-skills/skills/* .claude/skills/
```

## A typical content session

```
/hook-generator
  Idea: [your video idea, 1-3 sentences]
  Audience: [who this is for]
  Concrete detail: [a number, tool, or moment that anchors the story]
  → 10 hooks across 7 frameworks, each tagged with why it should work

/ugc-script
  Hook: [the one you picked]
  Length: 60s
  Format: TikTok / IG Reel
  → 60s script with timestamps, shot list, B-roll cues
    (asks you for the real numbers and moments — never invents them)

  ...shoot the video...

/repurpose-planner
  Source: your new 60s video transcript
  → Platform-specific plans: IG carousel, LinkedIn post, X thread, newsletter

/caption-pack
  Content: your new 60s video
  → Platform-specific captions + hashtag sets for each platform
```

## Skills in depth

### `/hook-generator`

Frameworks it pulls from:
- **Curiosity gap** — "I found out X and it changed Y"
- **Contrarian** — "Everyone says X. I think they're wrong."
- **Before/after** — "I used to X. Now I Y."
- **Story open** — "Last [time period], [specific event]..."
- **Callout** — "If you're [audience], stop [behavior]."
- **Numbered list** — "3 reasons X" / "I tried X. Here are 5 things..."
- **Question** — "What if X?" / "Why does X?"

Returns 10 hooks across these frameworks, tagged with which framework + why it should work for your audience.

### `/ugc-script`

Output format includes:
- Hook (0–3s) with on-screen text
- Setup (3–10s) — context for the audience
- Body — the actual content with shot type per beat
- Payoff / CTA (last 5–10s)
- B-roll list — what to shoot besides the talking head
- Hooks for re-edit — alternate first lines you can swap in for A/B testing

**Hard rule**: when the script needs a real result, error, testimonial, or number, it inserts a `[YOUR RESULT HERE]` placeholder — never invents one.

### `/brand-voice`

The first time you run it for a brand:
1. Asks for 5+ writing samples (LinkedIn posts, captions, brand guidelines, anything)
2. Extracts a voice profile: tone words, sentence length patterns, do's, don'ts, vocabulary signatures
3. Saves to `.claude/brand-voices/[brand-name].md` (per-project) or `~/.claude/brand-voices/` (global)

Subsequent runs:
- Pick a saved voice
- Pass content (a script, a caption, a post draft)
- Output in that voice

### `/repurpose-planner`

Doesn't just say "make a clip". Generates an actual repurposing *plan*:

- **TikTok / IG Reels short** — which moment becomes a 30s short, with a re-edited hook
- **IG carousel** — 5–10 slide outline with text per slide
- **LinkedIn post** — 600–1000 char version with the LinkedIn-specific framing
- **X / Twitter thread** — tweet-by-tweet outline (5–9 tweets)
- **YouTube short** — 60s vertical version
- **Newsletter section** — 200–400 word write-up

Each output includes the *unique angle* that platform's audience wants — not just the same content reformatted.

### `/caption-pack`

Platform-aware captions:
- **Instagram** — 1–3 short paragraphs, line breaks, hook → value → CTA, 8–15 hashtags
- **TikTok** — 1–2 sentences max, 3–5 hashtags
- **LinkedIn** — story-driven, hook + 3–5 short paragraphs, no hashtags or 3 max
- **X** — single tweet, no hashtags
- **YouTube Shorts** — descriptive, 1–2 sentences, 3–5 hashtags

## Voice profiles

Save voice profiles as markdown in `~/.claude/brand-voices/` so all your skills can use them. Format:

```markdown
---
brand: Your Brand Name
---

## Voice signature
- Tone: [list]
- Sentence length: [pattern]
- Vocabulary: [signatures]

## Do
- [list]

## Don't
- [list]

## Examples
[5+ real samples]
```

The `/brand-voice` skill writes these for you — you don't have to fill them in by hand.

## Philosophy

A few rules baked in:

1. **Plans, not retellings.** Scripts plan a shoot. They don't fabricate what happened in the shoot.
2. **The hook is the deliverable.** A bad hook kills good content. The skills spend disproportionate effort on hooks.
3. **Platform-native, not platform-aware.** Same content on every platform = no content. The repurposer rewrites for each platform's actual audience.
4. **Voice ≠ vibes.** Brand voice is extracted from samples, not described in adjectives.
5. **The creator is the source.** AI doesn't know your story. Skills ask for it; they don't invent it.

## Contributing

Have a hook framework I missed? A platform format I'm not handling well? Open a PR — these are just markdown.

## License

MIT — fork them, build on them, ship things.

---

Built by [@ImTaegan](https://github.com/ImTaegan) — UGC creator + web developer at [MintLooks Studio](https://mintlooks.studio).

Find me on [TikTok](https://tiktok.com/@taegan.dev) · [Instagram](https://instagram.com/taegan.dev) · [LinkedIn](https://linkedin.com/in/taegan-murphy-108453386) · [YouTube](https://youtube.com/@taegan.builds) · [X](https://x.com/taegan_dev).
