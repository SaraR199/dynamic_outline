# Dynamic Outline Book Machine

**Version:** 1.0
**Author:** Built for AI-assisted creative writers
**Platform:** Claude Code

---

## What Is This?

The Dynamic Outline Book Machine is a workflow system that leverages Claude Code to write full-length novels (24-28 chapters) using **progressive dynamic outlining** instead of pre-planning every detail.

### Traditional Workflow Problem:
- You create detailed chapter-by-chapter outlines upfront
- When writing deviates (character makes unexpected but good choice), you manually replan
- LLM has access to all future plot points, making it hard to write from limited POV

### This System's Solution:
- You provide high-level story guidance (master outline with 10-15 pillars)
- System generates **one act at a time** (6-7 chapters) with detailed chapter blocks
- After each chapter is written, system **automatically checks** if remaining chapters need adjustment
- **Spoiler protection**: Briefing packets exclude future plot reveals, forcing authentic POV writing
- **Dynamic adaptation**: Outline evolves with the story naturally

---

## Key Features

✅ **4-Act Structure** - Plans 6-7 chapters per act
✅ **Progressive Generation** - Only outlines what's needed next
✅ **Automatic Adjustment Checks** - Updates outline after each chapter if needed
✅ **Spoiler-Protected Briefing** - Writer AI never sees future plot points
✅ **Context Optimized** - Orchestrator uses minimal context, subagents read full docs
✅ **Extended Thinking** - All stages use thinking for quality
✅ **User Control** - Review/approve at every major step

---

## Using the Dedicated Agent (Recommended)

This system includes a specialized Claude Code agent (`book-machine-orchestrator`) that knows the workflow automatically.

**Quick Start with Agent:**
```bash
claude-code --agent book-machine-orchestrator
```

Then just say: `"Initialize new book project"`

The agent handles all orchestration, subagent spawning, and state management for you.

**📖 See [AGENT_SETUP.md](AGENT_SETUP.md) for installation and usage details.**

---

## How It Works

### The Workflow Loop

```
1. Generate Act Outline (6-7 chapters)
   ↓
2. User Reviews & Approves
   ↓
3. FOR EACH CHAPTER:
   ├─ Generate Briefing Packet (spoiler-free)
   ├─ Write Chapter
   ├─ Generate Summary
   ├─ User Reviews Chapter
   ├─ Check if Outline Needs Adjustments
   └─ User Reviews Adjustments (if any)
   ↓
4. Next Chapter or Next Act
   ↓
5. Book Complete! 🎉
```

### The Architecture

```
You ←→ Claude Code (Orchestrator)
           ↓
    Spawns Subagents via Task Tool:
           ├─ Act Outline Generator
           ├─ Chapter Briefing Generator
           ├─ Chapter Writer
           ├─ Chapter Summarizer
           └─ Outline Adjustment Checker
```

**Why this architecture?**
- Orchestrator stays lightweight (minimal context)
- Subagents read full documents for their specific tasks
- Context doesn't accumulate over time
- Each subagent has fresh context budget

---

## Setup Instructions

### Step 1: Understand the File Structure

```
/dynamic_outline/
├── README.md                          ← You are here
├── ORCHESTRATOR_GUIDE.md             ← Instructions for Claude Code
├── .book_machine/                    ← System files
│   ├── state.json                    ← Workflow state
│   ├── config.json                   ← Configuration
│   └── prompts/                      ← Subagent prompts (5 files)
│
└── project/                          ← YOUR BOOK CONTENT
    ├── master_outline.md            ← High-level story guidance
    ├── story_dossier.md             ← Characters, world, essentials
    ├── writing_style.md             ← Prose style guide
    ├── character_voice.md           ← POV voice profiles
    │
    ├── outlines/                    ← Generated (system creates)
    ├── chapters/                    ← Generated (system creates)
    ├── summaries/                   ← Generated (system creates)
    └── briefings/                   ← Generated (system creates)
```

### Step 2: Create Your Project Files

You need to create **4 core files** in the `project/` directory:

#### 1. `project/master_outline.md`
- See `project/master_outline.EXAMPLE.md` for structure
- Include:
  - Story overview (1-2 paragraphs of full story)
  - 10-15 plot pillars (major beats)
  - Character arc maps (Act 1-4 progression)
  - Mystery lifecycle (if applicable)
  - Setup/payoff tracker
  - Act summaries (what each act accomplishes)

#### 2. `project/story_dossier.md`
- See `project/story_dossier.EXAMPLE.md` for structure
- Include:
  - Project essentials (genre, tone, theme)
  - Character roster (all major characters with details)
  - World-building (key_world_rules, key_world_details)
  - Subplot information
  - Relationship dynamics
- **Note:** Section names can vary - system searches adaptively

#### 3. `project/writing_style.md`
- See `project/writing_style.EXAMPLE.md` for structure
- Define:
  - Narrative voice (POV, tense)
  - Prose style preferences
  - Dialogue style
  - Pacing techniques
  - What to avoid/embrace

#### 4. `project/character_voice.md`
- See `project/character_voice.EXAMPLE.md` for structure
- Define:
  - How each POV character's voice differs
  - Vocabulary, what they notice, how they process
  - Example passages in each character's voice

### Step 3: Review Configuration

Check `.book_machine/config.json` and adjust if needed:
- `chapters_per_act`: Default 7, adjust for your structure
- `target_chapter_word_count_min/max`: Default 1500-2500
- `include_last_n_full_chapters`: Default 9 (for context)

### Step 4: Initialize the Workflow

Talk to Claude Code and say:

```
"Initialize new book project"
```

Claude Code will:
- Check that all required files exist
- Update `state.json` to "ready_for_act_generation"
- Confirm initialization

---

## Using the System

### Starting Act 1

Say to Claude Code:
```
"Start Act 1"
```

Claude Code will:
1. Read your master outline, dossier, and config
2. Spawn an Act Outline Generation subagent
3. Generate 6-7 chapter blocks for Act 1
4. Present the outline to you for review

**Review the outline and:**
- Option A: Approve (proceed to chapter writing)
- Option B: Request changes (describe what to adjust)
- Option C: Regenerate (try again with any additional guidance)

### Writing Chapters

Say to Claude Code:
```
"Write next chapter"
```

Claude Code will:
1. Generate briefing packet (spoiler-free context)
2. Write the chapter (1500-2500 words)
3. Generate chapter summary
4. Present chapter to you for review

**Review the chapter and:**
- Option A: Approve as-is (proceed to adjustment check)
- Option B: Request specific edits (Claude Code will revise)
- Option C: Regenerate completely (new attempt)
- Option D: Provide manual edit (you edit, Claude Code saves it)

### Automatic Outline Adjustment

After you approve a chapter, Claude Code automatically:
1. Spawns Adjustment Check subagent
2. Analyzes if the written chapter requires outline changes
3. Presents results:
   - **"NO CHANGES NEEDED"** + reasoning → Proceeds to next chapter
   - **"ADJUSTMENTS REQUIRED"** + updated chapter blocks → You review

If adjustments are proposed:
- Option A: Approve (outline is updated)
- Option B: Modify (you describe changes)
- Option C: Reject (keep original outline)

### Continuing the Workflow

Keep saying:
```
"Write next chapter"
```

Claude Code tracks state and automatically:
- Writes the next chapter in sequence
- Checks for adjustments after each
- Moves to next act when current act completes
- Generates new act outline when needed

### Checking Status

At any time, say:
```
"Show status"
```

Claude Code will show:
- Current act and chapter
- Workflow stage
- Progress summary

---

## Commands Reference

| Command | What It Does |
|---------|-------------|
| `"Initialize new book project"` | Set up workflow, check files |
| `"Start Act [N]"` | Generate outline for Act N |
| `"Write next chapter"` | Continue workflow (briefing → write → summarize → adjust) |
| `"Show status"` | Display current progress |
| `"Regenerate [component]"` | Redo a specific step |
| `"Skip adjustment check"` | Proceed without checking adjustments |
| `"Edit outline"` | Manually edit current act outline |

---

## Understanding the Workflow Stages

### Stage 1: Act Outline Generation
**What happens:** System reads master outline + dossier + completed summaries, generates detailed chapter blocks for next 6-7 chapters

**Token usage:** 37k-104k (varies by project size)

**Output:** Act outline file with chapter blocks containing:
- Instructions for writer
- POV details
- Setting and timeline
- Emotional shift
- Authorial intent (hidden from POV character)
- Key information revealed
- Opening setup and ending hook
- Chapter summary (from POV character's limited perspective)

### Stage 2: Chapter Briefing Generation
**What happens:** System extracts ONLY information relevant to current chapter from dossier, excluding future spoilers

**Token usage:** 55k-110k

**Output:** Briefing packet containing:
- Writing style and voice guidelines
- Character roster (without arc spoilers)
- World rules and details
- Chapter-specific context
- Callbacks to previous chapters
- Current chapter outline block

**Critical:** This is spoiler protection. Writer AI only sees what POV character would know.

### Stage 3: Chapter Writing
**What happens:** System writes chapter using briefing packet + summaries + last 9 chapters

**Token usage:** 41k-53k

**Output:** 1500-2500 word chapter in your style, from POV character's limited perspective

### Stage 4: Chapter Summary
**What happens:** System summarizes chapter for future context

**Token usage:** 2k-3k

**Output:** Concise summary covering:
- Plot events and outcomes
- Character actions and changes
- New information revealed
- Relationship developments
- Unresolved threads

### Stage 5: Outline Adjustment Check
**What happens:** System compares written chapter to plan, determines if remaining chapters need changes

**Token usage:** 36k-103k

**Output:** Either:
- "NO CHANGES NEEDED" + reasoning
- "ADJUSTMENTS REQUIRED" + updated chapter blocks

**Philosophy:** Only proposes changes when meaningful divergence occurred. Respects natural story evolution.

---

## File Formats

### Act Outline Format

Each chapter block in an act outline looks like:

```markdown
### chapter_5

instructions: Write Chapter 5. The POV is strictly Thea Johansen in Third Person Limited, Past Tense. Follow the outline's chapter summary and emotional shift precisely.

tentpole_tag: First Major Complication

characters_in_this_chapter: Thea, Kyrian, Carolina

pov_details: Thea Johansen, Third Person Limited, Past Tense

setting_and_timeline: Chicago, Thea's apartment, late evening

emotional_shift: From defensive isolation to forced vulnerability

authorial_intent_and_subtext: This chapter reactivates the mate bond during physical combat, creating the central tension between Thea's need for autonomy and the bond's biological pull. The reader should feel the violation Thea experiences even as they understand Kyrian's perspective.

key_information_and_world_building_revealed:
*   Character: Thea can instinctively use ice magic when threatened
*   Plot/Mystery: Kyrian is being magically manipulated, not acting freely
*   World-Building: Mate bonds can go dormant but reactivate with proximity

subplot_advancement: Carolina's deteriorating health becomes urgent

opening_chapter_setup: Thea returns home to find Kyrian waiting in her apartment. She's exhausted from a double shift and has no patience for fae politics.

end_of_chapter_hook: The mate bond reactivates during their confrontation, and Thea experiences the full force of Kyrian's corrupted hatred through it.

chapter_summary_for_writer: I come home to find Kyrian in my apartment, which shouldn't be possible given the wards. He's different—colder, more dangerous—and when he moves toward me, I react instinctively. Ice forms on my hands without conscious thought. We fight, and it's brutal and personal in ways I didn't expect. During a moment when we're too close, something inside me snaps awake like a live wire—the mate bond, silent for months, roars back to life. Through it, I feel his hatred, his desire to hurt me, all twisted up with something that might have been love. I barely escape to Carolina's place, shaking and realizing the bond is back and it's worse than before.
```

### Chapter File Format

Just the prose, no metadata:

```markdown
[Chapter text begins immediately, no title or number]

The lock on my apartment door was intact, the wards I'd paid a small fortune for still humming with power. And yet, when I pushed the door open, Kyrian stood in my living room like he owned the place.

[... rest of chapter ...]
```

### Summary File Format

```markdown
Thea returns home to find Kyrian waiting in her apartment despite active wards. He's changed—colder and dangerous—and attacks her. Thea instinctively uses ice magic for the first time in combat. During close physical confrontation, the mate bond (dormant since Book 2) suddenly reactivates, flooding Thea with Kyrian's emotions: hatred, desire to harm her, all twisted with corrupted memories. Thea realizes he's being magically manipulated. She barely escapes to Carolina's place. The mate bond is now active and worse than before—she can feel his corrupted state. Carolina's health continues deteriorating, adding urgency to the situation.
```

---

## Tips for Success

### Writing Your Master Outline
- **Be strategic, not detailed:** Pillars are major beats, not scene-by-scene
- **Leave room for evolution:** System will fill in specifics
- **Track setups/payoffs:** Note what needs to come back
- **Character arcs matter:** Define emotional journey clearly

### Writing Your Story Dossier
- **Include more than you think:** Briefing Generator will filter appropriately
- **Avoid future spoilers:** Don't include plot_development or clues_twists_and_reveals sections
- **Character arcs separate:** Keep these out so briefings don't reveal future growth
- **Worldbuilding upfront:** key_world_rules should always be included

### During Workflow
- **Trust the system:** Adjustment checks are smart about when to propose changes
- **Review carefully:** You're the final arbiter of quality
- **Iterate when needed:** Regenerating is fine, don't settle for mediocre
- **Track your own notes:** Keep a separate doc of ideas/changes you want

### Context Management
- **Last 9 chapters is default:** Adjust in config if needed
- **Summaries are key:** They provide full story context cheaply
- **System handles optimization:** You don't need to worry about token counts

---

## Troubleshooting

### "Required file not found"
**Problem:** Missing master_outline.md or other core file
**Solution:** Create the file using .EXAMPLE as template

### "Outline doesn't match my vision"
**Problem:** Generated act outline diverges from master outline
**Solution:** Request specific changes, or regenerate with more guidance in master outline

### "Chapter feels off-voice"
**Problem:** Prose doesn't match your style
**Solution:** Refine writing_style.md and character_voice.md with more specific examples

### "Too many adjustments proposed"
**Problem:** System wants to change outline after every chapter
**Solution:** Either accept that story is evolving naturally, or tighten master outline guidance

### "Not enough adjustments"
**Problem:** Story diverged but system said no changes needed
**Solution:** Manually edit outline, or regenerate adjustment check with note about what diverged

### "Context issues / errors"
**Problem:** Subagent runs out of context
**Solution:** Reduce `include_last_n_full_chapters` in config, ensure summaries are concise

---

## Advanced Customization

### Modifying Prompts

All subagent prompts are in `.book_machine/prompts/`. You can edit them to:
- Change instructions
- Adjust output format
- Add new requirements
- Modify how placeholders are used

**Note:** If you change output format, update ORCHESTRATOR_GUIDE.md so Claude Code knows what to expect.

### Changing Chapter Structure

Edit `config.json`:
- Adjust `chapters_per_act` (default 7)
- Modify `total_acts` if not using 4-act structure
- Change word count targets

Then regenerate `state.json` to match new structure.

### Adding New Workflow Steps

To add a new stage (e.g., "beta reader feedback"):
1. Create new prompt template in `.book_machine/prompts/`
2. Update ORCHESTRATOR_GUIDE.md with new workflow step
3. Modify state.json to include new stage
4. Claude Code will follow updated guide

---

## Project Philosophy

This system is built on several principles:

1. **Progressive Discovery:** Don't plan everything upfront; discover the story as you write
2. **Spoiler Protection:** Force authentic POV by hiding future plot from writer AI
3. **Dynamic Adaptation:** Let outline evolve naturally with the story
4. **User Control:** Human reviews all major decisions
5. **Context Efficiency:** Orchestrator stays light, subagents do heavy lifting
6. **Quality Through Thinking:** Extended thinking at all stages for better results

---

## Credits & License

Built for AI-assisted creative writers who want to leverage thinking-capable LLMs for progressive outline generation.

**License:** MIT (use freely, modify as needed)

**Requirements:**
- Claude Code (for orchestration and Task tool)
- Access to extended thinking models
- Understanding of your own story structure

---

## Support & Feedback

This is an evolving system. Suggestions for improvement:
- File issues if you find bugs
- Share your master outline structure if you find better formats
- Document your workflow tweaks
- Help improve the prompts

---

## Quick Start Checklist

- [ ] **OPTIONAL:** Set up the dedicated agent (see [AGENT_SETUP.md](AGENT_SETUP.md))
- [ ] Read this README fully
- [ ] Review ORCHESTRATOR_GUIDE.md to understand system
- [ ] Look at .EXAMPLE files for structure guidance
- [ ] Create project/master_outline.md
- [ ] Create project/story_dossier.md
- [ ] Create project/writing_style.md
- [ ] Create project/character_voice.md
- [ ] Say to Claude Code: "Initialize new book project"
- [ ] Say to Claude Code: "Start Act 1"
- [ ] Review and approve act outline
- [ ] Say to Claude Code: "Write next chapter"
- [ ] Review chapter, approve or edit
- [ ] Review adjustments if any
- [ ] Repeat "Write next chapter" until book complete!

---

**Ready to write your book? Start with:** `"Initialize new book project"`

Good luck! 📚✨
