---
name: hook-generator
description: Generate 10 short-form video hooks across proven frameworks (curiosity gap, contrarian, before/after, story open, callout, list, question). Each hook is tagged with its framework and rationale.
---

# Hook Generator

Turn a video idea + audience into 10 hooks across proven frameworks. Hooks are the entire game in short-form — this skill spends disproportionate effort getting them right.

## Instructions for Claude

### Step 1: Gather Inputs

Ask the user for:

1. **Video idea** — what's the video about? (1–3 sentences)
2. **Audience** — who's it for? (specific is better than broad)
3. **Platform** — TikTok / Reels / Shorts / LinkedIn / Twitter (affects tone + length)
4. **Tone** (optional) — playful / serious / contrarian / educational / story-driven
5. **One concrete detail** the user wants to include — a number, a specific tool, a moment, a result. (This anchors the hooks in something real.)

If the user provides this in a single message, parse it and proceed. If anything's missing, ask only the missing parts.

### Step 2: Generate 10 Hooks Across 7 Frameworks

Generate AT LEAST one hook per framework. Total = 10 hooks.

**Framework definitions:**

#### 1. Curiosity gap
Tease that there's a payoff without revealing it. Format: "I [did/found/learned] X and it [unexpected outcome]."
- "I switched from Webflow to Next.js and saved $2,400/yr."
- "I tried X for 30 days. Here's what nobody tells you."

#### 2. Contrarian
Challenge a popular belief in the audience. Format: "Everyone says X. I think they're wrong." or "Stop doing X. Here's why."
- "Everyone says you need a Mac to code. I shipped my last 3 apps on a $400 Chromebook."
- "Stop using [popular tool]. Here's the one that actually works."

#### 3. Before/after
Show a state change. Format: "I used to X. Now I Y." or "[Time period] ago I was X. Today, Y."
- "Six months ago I'd never opened a terminal. Today I shipped my first SaaS."
- "I used to spend 4 hours a day writing captions. Now it takes 12 minutes."

#### 4. Story open
Drop into a moment. Format: "Last [time], I was [doing X] when [thing happened]." Specificity > vagueness.
- "Tuesday at 2am, I was 4 cups of coffee deep when Stripe finally let me charge cards."
- "Three weeks ago a recruiter sent me a take-home. Here's how I cheated (with permission)."

#### 5. Callout
Speak directly to a specific subset of the audience. Format: "If you're [audience descriptor], you need to see this."
- "If you're a designer-developer, this changes everything."
- "Indie devs spending more than $100/mo on infra — watch this."

#### 6. Numbered list
Promise a specific count of something useful. Format: "[N] [things] that [outcome]."
- "3 things I wish someone told me before I built my SaaS."
- "5 mistakes I made on my first UGC ad. Don't repeat them."

#### 7. Question
Provocative or genuinely curious. Format: "What if X?" / "Why does X?" / "How do I [do thing]?"
- "What if you didn't need a backend?"
- "Why does every dev tool look the same in 2026?"

### Step 3: Tag Each Hook

For each hook, include:

```
[Framework name]
"[The hook itself, ≤15 words for short-form, ≤30 for LinkedIn]"
Why it works: [1 sentence — what tension or curiosity it creates for THIS audience]
On-screen text suggestion: [the text version that appears on screen, often shorter]
```

### Step 4: Output Format

```markdown
# Hooks for: [video idea, one line]

**Audience**: [audience]
**Platform**: [platform]
**Anchored on**: [the concrete detail user provided]

---

## 1. Curiosity gap
"[Hook]"
- Why it works: [reason]
- On-screen: [text version]

## 2. Contrarian
"[Hook]"
- Why it works: [reason]
- On-screen: [text version]

[... 8 more ...]

---

## My recommended pick

**#[N]: [the hook]**

[1–2 sentence rationale — why this one given the audience and the concrete detail]

## Next step

Run `/ugc-script` with the hook you pick to turn it into a full script.
```

## Hard Rules

1. **Use the user's concrete detail.** Every hook should be GROUNDABLE in the detail they gave (a number, a tool, a moment). If the user said "I saved $2,400 switching from Webflow", at least 3 hooks must reference $2,400 or Webflow.

2. **No invented stats.** Never make up a number, percentage, or "study shows X". If you don't know it, leave a `[YOUR NUMBER]` placeholder.

3. **Length matters.** TikTok/Reels/Shorts hooks: ≤15 words. LinkedIn: ≤30 words. X: ≤140 chars. Match the platform.

4. **Specificity beats cleverness.** "Tuesday at 2am, 4 cups of coffee in" beats "Late one night while working hard". Push for specifics.

5. **No hype words** unless the user's tone explicitly calls for them: avoid "insane", "crazy", "shocking", "you won't believe".

## Recommendation Logic

When picking the recommended hook (Step 4), consider:
- Which framework matches the user's stated tone best
- Which hook is most grounded in the concrete detail
- Which one is most likely to hold the audience past 3 seconds (the scroll point)
- For LinkedIn specifically: prefer story open or contrarian (LinkedIn rewards narrative + opinion)
- For TikTok/Reels: prefer curiosity gap or specific story open
- For YouTube Shorts: prefer numbered list or before/after (algorithm rewards completion, lists drive completion)

## Error Handling

**If user provides no concrete detail:**
```
To generate hooks that don't sound generic, I need one specific thing about
this video — a number, a tool name, a moment, or a result. What's the one
detail that makes this story yours?
```

**If user's idea is vague (e.g., "make a video about productivity"):**
```
Productivity is a topic, not an idea. What specifically about productivity?
- A tool you use?
- A habit that changed something?
- A mistake you made?
- A counterintuitive thing you learned?

Give me the specific take, and I'll generate hooks.
```

## Integration with Other Skills

- **Next**: `/ugc-script` — turn the chosen hook into a full script
- **Voice**: `/brand-voice` — apply your saved brand voice to the hooks
- **After shooting**: `/repurpose-planner` and `/caption-pack`
