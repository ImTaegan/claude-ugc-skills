---
name: ugc-script
description: Turn a hook + brief into a 30s–90s UGC script with timestamps, shot types, B-roll cues, and on-screen text. Inserts placeholders for real results — never invents them.
---

# UGC Script Writer

Generates a shootable script. The script is a *plan for the shoot*, not a retelling of what happened — the skill never invents results, errors, numbers, or testimonials.

## Instructions for Claude

### Step 1: Gather Inputs

Ask for (or parse from the user's first message):

1. **Hook** — the chosen hook line
2. **Topic / story** — what's the video actually about? (3–5 sentences from the creator)
3. **Length** — 15s / 30s / 60s / 90s (default 60s)
4. **Format** — TikTok-style talking head / Reels with B-roll / cinematic UGC / desk POV / screenshare
5. **CTA** — what should the viewer do at the end? (follow / comment / link in bio / DM keyword / nothing)
6. **Voice profile** (optional) — if the user mentions a saved brand voice, load it from `~/.claude/brand-voices/[brand].md` or `.claude/brand-voices/[brand].md`

### Step 2: Identify the "Real Things" the Creator Must Provide

Before writing the script, scan the topic for things the script will need to reference but that ONLY the creator knows:

- **Specific numbers** (revenue, time saved, bugs fixed, hours)
- **Specific tools / brand names** in their actual workflow
- **Specific moments** ("the moment I realized...")
- **Specific quotes** (something a customer / boss / friend said)
- **Specific results** ("after 30 days, X happened")
- **Errors / failures** (the actual error message, the actual mistake)

For each of these, the script will use a `[YOUR ___ HERE]` placeholder, NOT a fabricated value.

### Step 3: Structure the Script

Use this beat structure, scaled to the chosen length:

| Length | Hook | Setup | Body | Payoff/CTA |
|---|---|---|---|---|
| 15s | 0–2s | 2–4s | 4–12s | 12–15s |
| 30s | 0–3s | 3–7s | 7–25s | 25–30s |
| 60s | 0–3s | 3–10s | 10–50s | 50–60s |
| 90s | 0–3s | 3–12s | 12–75s | 75–90s |

### Step 4: Write the Script

Output format:

```markdown
# Script: [video title / first 6 words of hook]

**Length**: [N]s
**Format**: [format]
**Hook**: [the chosen hook]

---

## Beat 1 — Hook (0–3s)

**Spoken**: "[Hook line, exactly as it'll be said]"

**Shot**: [shot type — e.g., "Talking head, eye-level, phone in hand"]

**On-screen text**: [text overlay — usually the hook in shorter form, plus any visual emphasis]

**B-roll**: [if any]

---

## Beat 2 — Setup (3–10s)

**Spoken**: "[Lines]"

> [SCRIPT NOTE: Insert YOUR specific [thing] here. Don't read the placeholder — say the actual [thing].]

**Shot**: [shot type]

**On-screen text**: [text]

**B-roll**: [B-roll suggestion]

---

[... repeat for each beat ...]

---

## Beat N — Payoff / CTA (last X seconds)

**Spoken**: "[Lines]"

**CTA**: [the actual CTA — "Follow for more" / "Comment '[keyword]' for the link" / etc.]

**Shot**: [final shot — often back to talking head with eye contact]

**On-screen text**: [strong final text]

---

## B-roll shot list

Things to capture besides the talking head, in order of importance:

1. [Shot description] — captures: [what it shows]
2. [Shot description] — captures: [what it shows]
3. [Shot description] — captures: [what it shows]

---

## Alternate hooks (for re-edits / A/B testing)

If the original hook doesn't perform, these are pre-cut alternates that fit the same body:

1. "[Alternate hook 1]" — same length, swappable
2. "[Alternate hook 2]" — same length, swappable
3. "[Alternate hook 3]" — same length, swappable

---

## What you need to bring to the shoot

The script has placeholders for things only YOU know. Before shooting, answer:

- [ ] [YOUR NUMBER] in Beat X — what's the real number?
- [ ] [YOUR TOOL NAME] in Beat Y — which tool do you actually use?
- [ ] [YOUR MOMENT] in Beat Z — what specifically happened?

Replace these in the script, then shoot.
```

## Hard Rules

1. **Never invent specifics.** No fabricated numbers, results, errors, customer quotes, or moments. Use `[YOUR ___ HERE]` placeholders.

2. **Spoken vs. on-screen text are different.** People talk differently than they read. Spoken lines should sound natural when said out loud — read them aloud as you write. On-screen text should be punchier and shorter than the spoken line.

3. **Shot types must be shootable.** Don't say "drone shot of city skyline" if the format is a TikTok talking head. Match shot suggestions to the user's likely setup.

4. **Match length precisely.** A 30s script that reads as 45s when spoken is broken. Aim for ~2.5 words per second of spoken content. (Slower than that = boring. Faster than that = unreadable on TikTok.)

5. **B-roll should illustrate, not decorate.** Each B-roll suggestion must have a clear "captures: [X]" reason.

6. **The CTA must be specific.** "Like and subscribe" is not a CTA. "Comment 'starter pack' and I'll DM you the Notion template" is.

7. **Use the loaded brand voice** if one was provided. Tone words, sentence patterns, and vocabulary signatures from the voice profile must be honored.

## Voice Profile Loading

If the user mentions a saved voice (e.g., "use my mintlooks voice"):

```bash
# Try project-local first, then global
cat .claude/brand-voices/[brand].md 2>/dev/null || cat ~/.claude/brand-voices/[brand].md
```

If not found, ask the user if they want to:
1. Run `/brand-voice` first to extract the voice from samples
2. Continue without a voice profile (default voice)

## Format-Specific Adjustments

**TikTok talking head**:
- Shots default to vertical, eye-level, phone-distance
- B-roll cuts every 2–3 seconds for retention
- On-screen text appears at most beats

**Cinematic UGC**:
- More B-roll, fewer talking-head moments
- Shot variety matters more
- Music/sound design notes welcome

**Desk POV** (e.g., screenshare-style):
- Talking head is overlay/PIP
- Most "shots" are actually UI captures
- B-roll = different screens / cursor movements

**Screenshare** (e.g., dev tutorial):
- Almost all body beats are screen-captures
- Talking head only at hook + payoff
- Mention specific UI states to show

## Error Handling

**No hook provided:**
```
I need a hook to script around. Run /hook-generator first, or paste a hook
you've already chosen.
```

**Topic too vague:**
```
The topic is too thin to script. Tell me:
- What specifically happens in this video?
- What's the audience supposed to learn / feel / do?
- What's the one moment that should land hardest?
```

**User asks me to "make up the numbers" or "fill in fake details":**
```
I won't fabricate specifics — viewers can smell fake numbers, and getting
caught lying is the fastest way to lose trust. Tell me the real number (or
ballpark) and I'll write around it. If you don't have a real number yet,
I'll keep the placeholder so you can fill it in before shooting.
```

## Integration with Other Skills

- **Before**: `/hook-generator` to pick a hook
- **Voice**: `/brand-voice` to load a brand voice profile
- **After shooting**: `/repurpose-planner` and `/caption-pack`
