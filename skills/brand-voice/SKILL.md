---
name: brand-voice
description: Extract a brand voice from real writing samples and save it as a reusable profile. Apply saved voices to new content. No vibes — voices are learned from samples, not described in adjectives.
---

# Brand Voice

Most "brand voice" is vibes — "friendly, modern, approachable". That's useless. This skill extracts a *learned profile* from 5+ real writing samples, then applies it to new content.

## Instructions for Claude

This skill has three modes: **extract** (build a new voice profile), **apply** (use a saved profile), **list** (show saved profiles).

Detect mode from the user's input. If unclear, ask.

---

## Mode: Extract

### Step 1: Identify the Brand and Where to Save

Ask:
1. **Brand name** (used as the filename, e.g., "mintlooks" → `mintlooks.md`)
2. **Save location**: project (`.claude/brand-voices/`) or global (`~/.claude/brand-voices/`)?

### Step 2: Collect Samples

Ask for AT LEAST 5 writing samples. More is better. Tell the user:

```
I need at least 5 samples to extract a voice. The more diverse the better:
- LinkedIn posts
- Instagram captions
- Newsletter excerpts
- Brand guidelines
- Customer-facing emails
- Existing video scripts

Paste them here, one per message or all in one — your call. Tell me when
you're done.
```

If the user provides fewer than 5, push back:
```
That's [N] samples — fewer than I'd want for a reliable profile. With this
few I'll guess more than I learn. Either:
1. Send more samples (recommended)
2. Continue with what we have, knowing the profile will be rougher
```

### Step 3: Extract the Profile

Read all samples carefully. Extract:

**Tone signature** (3–5 words):
Look at HOW the brand says things, not what they say. Examples:
- "Casual + technical" (Linear's docs)
- "Earnest + builder-first" (Vercel)
- "Sardonic + plain-spoken" (Honest Co's old captions)

**Sentence structure patterns**:
- Average sentence length (count from a few samples)
- Are paragraphs short or long?
- Does the brand use sentence fragments? Single-word sentences?
- Does it ask rhetorical questions? Use second-person ("you")?

**Vocabulary signatures**:
- Words/phrases the brand uses repeatedly (e.g., "ship", "build", "we")
- Words the brand seems to avoid (look for absent-but-expected — e.g., a tech brand never saying "synergy" or "leverage")
- Punctuation tics (em-dashes, semicolons, ellipses, line breaks as paragraphs)

**Rhetorical moves**:
- Does it open posts with stories? Stats? Questions? Bold claims?
- Does it use lists or prose?
- Does it use first-person ("I"), royal-we ("we"), or impersonal voice?
- Where does it land emotionally — humor, conviction, vulnerability, authority?

**Do / Don't rules** (3–5 each):
Concrete behaviors, not vibes. "Do: open with a specific moment, not a general statement" beats "Do: be authentic".

### Step 4: Write the Profile

Save to `[location]/brand-voices/[brand].md`:

```markdown
---
brand: [Brand Name]
extracted: [date]
samples: [N]
---

# [Brand Name] — voice profile

## Tone signature
[3–5 word phrase]

## Sentence structure
- Avg sentence length: [N] words
- Paragraph style: [short/medium/long, line-break-heavy/prose]
- Fragments: [used/avoided] — [example if used]
- Questions: [rhetorical/genuine/avoided]
- POV: [I / we / you / impersonal]

## Vocabulary signatures
**Uses repeatedly:**
- [word/phrase]
- [word/phrase]

**Avoids:**
- [word/phrase] — [why we noticed]

**Punctuation tics:**
- [tic]

## Rhetorical moves
**Opens posts with**: [pattern]
**Builds arguments via**: [stories / lists / claims]
**Emotional register**: [where it lands]

## Do
- [concrete rule]
- [concrete rule]
- [concrete rule]

## Don't
- [concrete rule]
- [concrete rule]
- [concrete rule]

## Example reframings

The same idea, written 3 ways — only the third is on-brand.

**Idea**: [generic statement]

**Off-brand**: "[generic version]"
**Off-brand**: "[different generic version]"
**On-brand**: "[in the voice]"

## Source samples

[Quote a 1–2 line excerpt from each sample, with a tag like "LinkedIn post, Mar 2026"]
```

### Step 5: Confirm and Save

Show the profile to the user. Ask:
```
Here's the profile I extracted. Anything off? I can refine it before saving.

Save to: [path]
```

On confirmation, write the file.

```bash
mkdir -p [location]/brand-voices
# Write the profile file
```

---

## Mode: Apply

### Step 1: Identify the Voice and the Content

Ask:
1. Which voice? (Or auto-detect from `[user input] in [brand] voice`.)
2. What content needs to be in that voice? (Paste or describe.)

### Step 2: Load the Profile

```bash
# Try project-local first, then global
cat .claude/brand-voices/[brand].md 2>/dev/null || cat ~/.claude/brand-voices/[brand].md
```

If not found:
```
No voice profile found for "[brand]". Either:
1. Run /brand-voice extract to build one
2. List available voices: /brand-voice list
```

### Step 3: Rewrite

Apply the profile to the content. Show:
- The original (for reference)
- The rewritten version
- 1–2 sentences explaining what you changed and why (which rules from the profile drove the changes)

### Step 4: Iterate

Offer:
```
Want me to:
1. Adjust toward [more/less of some quality]
2. Try a different voice
3. Done
```

---

## Mode: List

```bash
ls -la ~/.claude/brand-voices/ 2>/dev/null
ls -la .claude/brand-voices/ 2>/dev/null
```

Display the brands found, with a 1-line preview of the tone signature for each.

---

## Hard Rules

1. **Voice = patterns, not adjectives.** "Friendly" is not a voice. "Opens with a specific time + place, uses 'we' not 'I', never uses exclamation marks" is.

2. **Don't extract from <5 samples** without warning the user. Small sample = unreliable profile.

3. **Concrete rules only.** Every Do/Don't must be observable in writing. "Be authentic" fails this test. "Don't use the word 'authentic'" passes.

4. **The profile is a learning artifact, not a system.** When applying it, treat the rules as strong defaults but break them if the content demands it. Note when you broke a rule and why.

5. **Never invent samples.** When showing "source samples", quote real lines from what the user provided.

## Error Handling

**Brand profile already exists:**
```
A profile for "[brand]" exists at [path].

Options:
1. Overwrite — extract fresh from new samples
2. Append — add new samples to the existing profile
3. Cancel
```

**User asks for a voice they describe but don't have samples for:**
```
I can write in a *style* you describe (e.g., "punchy, contrarian, lots of
em-dashes"), but I won't save that as a "voice profile" — those need real
samples. Want me to:
1. Apply your description as a one-shot style (no save)
2. Help you collect samples and extract a real profile
```
