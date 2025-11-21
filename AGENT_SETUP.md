# Agent Setup Guide

This guide explains how to install and use the dedicated `book-machine-orchestrator` agent for the Dynamic Outline Book Machine workflow.

---

## What is the Agent?

The `book-machine-orchestrator` is a specialized Claude Code agent configured specifically for running the Dynamic Outline Book Machine workflow. It has:

- Built-in understanding of the workflow stages
- Instructions for spawning subagents efficiently
- State management logic
- All orchestrator commands pre-configured
- Conversational guidance optimized for book writing

**Think of it as:** A dedicated mode for Claude Code that "knows" how to run your book machine.

---

## Installation

### Option 1: Use from This Repository (Recommended)

If you're using Claude Code from the terminal in this repository, you can reference the agent directly:

```bash
# Start Claude Code with the book machine agent
claude-code --agent book-machine-orchestrator.agent.md
```

The agent file is in the repository root: `book-machine-orchestrator.agent.md`

### Option 2: Install Globally (Advanced)

If you want the agent available from any directory:

1. **Find your Claude Code agents directory:**
   ```bash
   # Usually located at:
   ~/.claude/agents/
   ```

2. **Copy the agent file:**
   ```bash
   cp book-machine-orchestrator.agent.md ~/.claude/agents/
   ```

3. **Use from anywhere:**
   ```bash
   claude-code --agent book-machine-orchestrator
   ```

### Option 3: Use from Web Interface

If using Claude Code from the web:

**The agent configuration is built into the system.** Simply interact with Claude Code naturally and say commands like:
- "Initialize new book project"
- "Start Act 1"
- "Write next chapter"

Claude Code will follow the orchestrator patterns automatically when you're in this repository.

---

## Agent Features

### Specialized Behavior

When using the `book-machine-orchestrator` agent, Claude Code:

✅ **Understands workflow commands:**
- "Initialize new book project"
- "Start Act 1"
- "Write next chapter"
- "Show status"

✅ **Spawns subagents efficiently:**
- Act Outline Generator
- Chapter Briefing Generator
- Chapter Writer
- Summary Generator
- Adjustment Checker

✅ **Manages state automatically:**
- Tracks current act and chapter
- Updates workflow stage
- Saves generated files to correct locations

✅ **Guides you conversationally:**
- Friendly encouragement
- Clear option presentation (A/B/C format)
- Progress updates
- Celebrates milestones

✅ **Stays lightweight:**
- Reads only state.json and config.json
- Delegates heavy operations to subagents
- Never accumulates context

### Visual Identity

The agent has:
- **Name:** `book-machine-orchestrator`
- **Model:** Sonnet (for extended thinking and quality)
- **Color:** Purple (in terminal with color support)

---

## Usage

### Starting a Session with the Agent

```bash
# Navigate to your book project
cd /path/to/dynamic_outline

# Start Claude Code with the agent
claude-code --agent book-machine-orchestrator

# Or if installed globally
claude-code --agent book-machine-orchestrator
```

### First Commands

```
You: "Initialize new book project"
Agent: [Checks files, sets up state]

You: "Start Act 1"
Agent: [Spawns subagent, generates outline]

You: "Approve"
Agent: [Updates state]

You: "Write next chapter"
Agent: [Runs full chapter workflow]
```

---

## Agent vs. Generic Claude Code

### With Generic Claude Code (No Agent)

You need to be explicit:
```
"Read the ORCHESTRATOR_GUIDE.md and act as the orchestrator.
Initialize new book project."
```

### With Book Machine Agent

Just say:
```
"Initialize new book project"
```

The agent already knows:
- What workflow to follow
- How to spawn subagents
- Where files are located
- What commands you can use

---

## Comparison with Other Agents

If you have other agents (like `fantasy-romance-editor`), here's when to use each:

### Use `book-machine-orchestrator` for:
- ✅ Running the full book writing workflow
- ✅ Generating act outlines
- ✅ Writing chapters progressively
- ✅ Managing workflow state
- ✅ Automatic outline adjustments

### Use `fantasy-romance-editor` (or similar) for:
- ✅ Reviewing/critiquing completed chapters
- ✅ Developmental editing feedback
- ✅ Analyzing romantic tension and pacing
- ✅ Worldbuilding refinement
- ✅ General editorial guidance

### Workflow Integration

You can use both agents together:

```bash
# Write chapters with book machine
claude-code --agent book-machine-orchestrator

You: "Write next chapter"
[Chapter generated]

# Switch to editorial agent for review
claude-code --agent fantasy-romance-editor

You: "Review this chapter for romantic tension and pacing"
[Get editorial feedback]

# Switch back to book machine to continue
claude-code --agent book-machine-orchestrator

You: "Write next chapter"
```

Or in a single session, you might say:
```
"I've written Chapter 5. Before I approve it, can you switch to
editorial mode and review it for romantic tension?"
```

---

## Customizing the Agent

The agent file is markdown and can be edited:

**Location:** `book-machine-orchestrator.agent.md`

### Customizable Sections:

```yaml
---
name: book-machine-orchestrator          # Change agent name
description: [...]                       # Edit when to use it
model: sonnet                           # Change model (sonnet/opus/haiku)
color: purple                           # Change terminal color
---
```

**System Prompt:** Everything after the `---` is the agent's system prompt. You can:
- Add specific instructions for your workflow
- Adjust the tone and style
- Add domain-specific guidance
- Modify workflow steps

### Example Customization

To make the agent more encouraging for fantasy romance:

```markdown
## Additional Guidance for Fantasy Romance

When reviewing chapters, also consider:
- Romantic tension and slow burn progression
- Fantasy worldbuilding integration
- Character chemistry and banter
- Balance of action vs. intimate moments
- Genre convention adherence

Be enthusiastic and encouraging about romantic beats!
```

---

## Troubleshooting

### "Agent not found"

**Problem:** `claude-code --agent book-machine-orchestrator` returns error

**Solutions:**
1. Use full path: `claude-code --agent ./book-machine-orchestrator.agent.md`
2. Copy to `~/.claude/agents/` directory
3. Check filename spelling

### "Agent doesn't respond to commands"

**Problem:** Agent doesn't understand "Start Act 1"

**Solution:** Check you're in the correct repository with project files

### "Want different behavior"

**Problem:** Agent's tone or approach doesn't match your preference

**Solution:** Edit `book-machine-orchestrator.agent.md` system prompt section

---

## Advanced: Multiple Agent Configurations

You can create variations of the book machine agent:

```bash
# Original
book-machine-orchestrator.agent.md

# Variations
book-machine-fast.agent.md          # Uses haiku model for speed
book-machine-detailed.agent.md      # Uses opus for maximum quality
book-machine-romance.agent.md       # Specialized for romance writing
```

Each can have different:
- Models (haiku/sonnet/opus)
- System prompts (more/less verbose)
- Workflow tweaks
- Domain specializations

---

## Best Practices

### 1. Start Each Session with the Agent

```bash
claude-code --agent book-machine-orchestrator
```

### 2. Use Consistent Commands

The agent is trained on specific commands:
- "Initialize new book project"
- "Start Act 1"
- "Write next chapter"
- "Show status"

### 3. Let the Agent Guide You

The agent will present options clearly:
- (A) Approve
- (B) Request changes
- (C) Regenerate

Just respond with your choice.

### 4. Trust the Workflow

The agent handles:
- State management
- Subagent spawning
- File organization
- Adjustment checks

You focus on:
- Reviewing outlines
- Approving chapters
- Making creative decisions

---

## Quick Reference

### Starting
```bash
claude-code --agent book-machine-orchestrator
```

### Essential Commands
```
"Initialize new book project"
"Start Act 1"
"Write next chapter"
"Show status"
"Approve"
"Regenerate"
```

### When to Use
- Progressive book writing workflow
- Need automatic outline adjustments
- Want context-optimized architecture
- Writing 24-28 chapter novels

### When NOT to Use
- Just want editorial feedback → use editorial agent
- Quick one-off writing → use generic Claude Code
- Not following the workflow → use generic Claude Code

---

## Summary

✅ **Created:** Specialized agent for book machine workflow
✅ **Located:** `book-machine-orchestrator.agent.md`
✅ **Usage:** `claude-code --agent book-machine-orchestrator`
✅ **Benefits:** Built-in workflow knowledge, efficient subagent spawning, conversational guidance
✅ **Customizable:** Edit the .agent.md file to adjust behavior

**Ready to write with the agent?**

```bash
claude-code --agent book-machine-orchestrator
```

Then say: `"Initialize new book project"`

Happy writing! 📚✨
