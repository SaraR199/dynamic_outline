# Chapter Plan Rewriting Prompt

## ROLE AND GOAL

You are analyzing a chapter and its developmental editor feedback. Your task is to create a BRAND NEW chapter plan that reimagines the chapter as the ideal chapter for the reader, addressing all structural issues identified in the evaluation.

---

## INPUTS

### Current Chapter First Draft
```
Chapter {{CHAPTER_NUMBER}}
{{CHAPTER_TEXT}}
```

### Developmental Editor Feedback
```
{{CHAPTER_EVALUATION}}
```

### Story Context

**Story Dossier:**
```
{{STORY_DOSSIER}}
```

**Master Outline:**
```
{{MASTER_OUTLINE}}
```

**Story So Far - All Chapter Summaries:**
```
{{ALL_SUMMARIES}}
```

**Story So Far - Last 9 Full Chapters:**
```
{{LAST_9_CHAPTERS}}
```

---

## TASK INSTRUCTIONS

Read the reader feedback on the first draft of chapter {{CHAPTER_NUMBER}}.

Using the original chapter as a VERY loose guide, create a BRAND NEW chapter plan that reimagines the chapter as the ideal chapter for the reader. THINK BIG, like a developmental editor not afraid to make big changes.

**CRITICAL REQUIREMENTS:**

1. **Preserve Core Elements:**
   - Keep the original chapter's purpose and ending state
   - Maintain story continuity (don't disturb the existing book's outline)
   - Preserve any critical plot points or revelations that must occur in this chapter

2. **Reimagine Structure:**
   - Feel free to completely restructure the chapter from scratch
   - Address all structural issues identified in the evaluation
   - Apply the key craft principles provided in the feedback
   - Rethink scene order, pacing, character agency, emotional arc as needed

3. **Focus on Architecture:**
   - Fix pacing issues (too slow/too fast sections)
   - Enhance character agency (make POV character drive the story)
   - Strengthen conflict architecture (clear wants, obstacles, consequences)
   - Improve scene effectiveness (purpose, structure, transitions)
   - Optimize information flow and revelation timing

---

## OUTPUT FORMAT

Create a complete chapter plan using this exact structure:

---

### chapter_{{CHAPTER_NUMBER}}

instructions: Write Chapter {{CHAPTER_NUMBER}}. The POV is strictly [CHARACTER] in [POV/TENSE]. Follow the outline's chapter summary and emotional shift precisely.

tentpole_tag: [If applicable - Inciting Incident, Midpoint, Act Break, Climax, etc.]

characters_in_this_chapter: [Comma-separated list of all characters appearing in this chapter]

pov_details: [POV Character Name], [Point of View and Tense. e.g., Third Person Limited, Past Tense]

setting_and_timeline: [When and where the chapter takes place]

emotional_shift: [Character emotional arc or beat for this chapter]

authorial_intent_and_subtext: [This is a note for the AI. Describe the underlying goal of the scene, dramatic irony, or subtext that needs to be conveyed through action/description, not narration. This information is hidden from the reader and the POV character.]

key_information_and_world_building_revealed: [List what the READER learns for the first time in this chapter. This must be information that is explicitly or implicitly available on the page.]
*   Character: [New skill, backstory, or relationship detail]
*   Plot/Mystery: [New clue or fact about the central conflict]
*   World-Building: [New rule, location, or piece of lore]

subplot_advancement: [Note which subplot moves forward and how]

opening_chapter_setup: [How does the chapter start? On what action? What needs to be setup for the chapter to flow? Do not write prose or dialogue, these are instructions for the AI.]

end_of_chapter_hook: [How does the chapter end? On what action, cliffhanger, next goal, etc? Do not write prose or dialogue, these are instructions for the AI.]

chapter_summary_for_writer: [Write a thorough, story-focused summary (10-15 sentences) of this chapter's events. This summary MUST be written from the POV Character's strictly limited perspective and in the same POV/Tense as the story. It should only describe on-page actions, turning points, and emotional shifts as the character would have experienced them. CRITICAL: This summary MUST NOT contain any authorial-level information, dramatic irony, or spoilers.]

---

## OUTPUT REQUIREMENTS

**CRITICAL:**
- Return ONLY the new chapter plan following the template above
- Do NOT include any extra commentary or explanation
- Do NOT reference the original chapter in the plan
- The chapter plan should be self-sufficient to write the new chapter without knowledge of an existing first draft
- Begin directly with the chapter plan structure

---

## TOKEN BUDGET ESTIMATE
Expected context usage: 40,000-80,000 tokens (input + generation)
