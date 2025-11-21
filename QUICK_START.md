# Quick Start Guide

Welcome to the Dynamic Outline Book Machine! This guide will get you writing in 5 steps.

---

## Step 1: Create Your Project Files (30-60 minutes)

Create these 4 files in the `project/` directory:

### 1. `project/master_outline.md`
Use `project/master_outline.EXAMPLE.md` as your template.

**What to include:**
- Story overview (full plot in 1-2 paragraphs)
- 10-15 plot pillars (major beats like Inciting Incident, Midpoint, Climax)
- Character arc maps (4-act progression for main characters)
- Act summaries (what each act accomplishes)

**Time estimate:** 20-30 minutes

### 2. `project/story_dossier.md`
Use `project/story_dossier.EXAMPLE.md` as your template.

**What to include:**
- Project essentials (genre, tone, theme)
- Character roster (all major characters with details)
- Key world rules and details
- Subplots and relationship dynamics

**Time estimate:** 15-20 minutes

### 3. `project/writing_style.md`
Use `project/writing_style.EXAMPLE.md` as your template.

**What to include:**
- POV and tense
- Prose style preferences
- Dialogue guidelines
- Pacing techniques

**Time estimate:** 5-10 minutes

### 4. `project/character_voice.md`
Use `project/character_voice.EXAMPLE.md` as your template.

**What to include:**
- How each POV character's voice differs
- Example passages in each character's POV

**Time estimate:** 5-10 minutes

---

## Step 2: Review Configuration (2 minutes)

Check `.book_machine/config.json` and adjust if needed:

```json
{
  "book_structure": {
    "total_acts": 4,                    // Change if not using 4 acts
    "chapters_per_act": 7,              // Adjust chapters per act
    "target_chapter_word_count_min": 1500,
    "target_chapter_word_count_max": 2500
  }
}
```

---

## Step 3: Initialize (30 seconds)

Say to Claude Code:

```
"Initialize new book project"
```

Claude Code will check your files and confirm setup.

---

## Step 4: Generate Act 1 Outline (2-3 minutes)

Say to Claude Code:

```
"Start Act 1"
```

Claude Code will:
1. Read your master outline and dossier
2. Generate 6-7 detailed chapter blocks for Act 1
3. Show you the outline for review

**Review it and:**
- If you like it: Say "Approve"
- If you want changes: Describe what to adjust
- If you want to try again: Say "Regenerate"

---

## Step 5: Write Your First Chapter (3-5 minutes)

Say to Claude Code:

```
"Write next chapter"
```

Claude Code will:
1. Generate a briefing packet
2. Write Chapter 1 (1500-2500 words)
3. Generate a summary
4. Show you the chapter for review

**Review it and:**
- If you like it: Say "Approve"
- If you want edits: Describe changes
- If you want to regenerate: Say "Regenerate"

After approval, Claude Code will automatically check if the outline needs adjustments based on what was written.

---

## Step 6: Keep Going!

Just keep saying:

```
"Write next chapter"
```

Claude Code will:
- Write each chapter in sequence
- Check for outline adjustments after each
- Move to next act when current act completes
- Generate new act outline as needed
- Track progress automatically

---

## Typical Session Flow

```
You: "Write next chapter"

Claude Code:
  → Generates briefing
  → Writes Chapter 2
  → Generates summary
  → "Here's Chapter 2 for your review..."

You: "Approve"

Claude Code:
  → Checks outline adjustments
  → "No changes needed. Ready for Chapter 3."

You: "Write next chapter"

[Repeat until book complete]
```

---

## Helpful Commands

| Say This | Claude Code Does This |
|----------|----------------------|
| `"Show status"` | Shows current progress (Act 2, Chapter 9, etc.) |
| `"Write next chapter"` | Continues the workflow |
| `"Start Act 2"` | Generates outline for Act 2 |
| `"Regenerate chapter"` | Writes current chapter again |
| `"Skip adjustment check"` | Proceeds without checking outline |

---

## What to Expect

### Time Estimates (per chapter):
- **Briefing generation:** 30-60 seconds
- **Chapter writing:** 60-120 seconds (1500-2500 words)
- **Summary generation:** 15-30 seconds
- **Adjustment check:** 30-60 seconds
- **Your review time:** 5-10 minutes

**Total per chapter:** ~10-15 minutes including your review

**Total for 28-chapter book:** ~5-7 hours of active work (spread over days/weeks as you prefer)

### What You Review:
1. **Act outlines** (every 6-7 chapters)
2. **Written chapters** (every chapter)
3. **Outline adjustments** (when proposed)

### What Happens Automatically:
1. Briefing packet generation
2. Chapter writing
3. Summary generation
4. Adjustment checking
5. State tracking
6. File management

---

## Pro Tips

### For Better Act Outlines:
- Be specific in your master outline about character emotional arcs
- Note which mysteries/reveals happen when
- Track setup/payoff pairs clearly

### For Better Chapters:
- Refine writing_style.md with specific examples
- Show character voice differences clearly in character_voice.md
- Include sensory details in story_dossier.md

### For Smoother Workflow:
- Review chapters promptly (don't let them pile up)
- Trust the adjustment check (it's smart about when to propose changes)
- Keep notes on ideas that come up during writing
- Don't be afraid to regenerate if something feels off

---

## Troubleshooting

**"I don't like the act outline"**
→ Request specific changes or regenerate with more guidance

**"Chapter doesn't match my style"**
→ Add more specific examples to writing_style.md and regenerate

**"Too many outline adjustments"**
→ Story is evolving naturally - this is okay! Or tighten master outline.

**"Not enough outline adjustments"**
→ Manually edit outline if you see divergence system missed

**"I want to change something in the master outline mid-book"**
→ Go ahead! Edit master_outline.md and tell Claude Code when generating next act.

---

## Ready?

1. ✅ Create your 4 project files
2. ✅ Check config.json
3. ✅ Say: "Initialize new book project"
4. ✅ Say: "Start Act 1"
5. ✅ Say: "Write next chapter"

**That's it! You're writing a book with AI assistance.** 📚✨

---

## Need More Help?

- Read **README.md** for comprehensive documentation
- Check **ORCHESTRATOR_GUIDE.md** to understand how Claude Code orchestrates
- Look at **.EXAMPLE.md** files for format guidance
- Review **.book_machine/prompts/** to see what each subagent does

**Happy writing!** 🎉
