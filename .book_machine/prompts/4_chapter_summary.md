# Chapter Summary Generation Prompt

## ROLE AND GOAL

You are a story analyst specializing in creating concise but comprehensive chapter summaries. Your summaries must capture all story-critical details needed to inform future chapters.

---

## INPUTS

### Chapter Text
```
{{CHAPTER_TEXT}}
```

### Chapter Metadata
- Chapter Number: {{CHAPTER_NUMBER}}
- POV Character: {{POV_CHARACTER}}

---

## INSTRUCTIONS

Read the full chapter text above. Your job is to generate a concise but comprehensive summary of the chapter, focused on all story-critical details needed to inform future chapters.

Write a chapter summary that covers:
- All major plot events and outcomes (in the order they occur)
- Key character actions, decisions, and changes (emotional, physical, relational, or status-related)
- Any new information, twists, or discoveries introduced
- Developments in relationships, motivations, alliances, or conflicts
- Important setting changes, time shifts, or story world revelations
- Any unresolved subplots or foreshadowed elements that should carry forward

### Guidelines
- Be conservative with tokens: do not retell the chapter scene-by-scene, but ensure all critical information is included
- Write in clear, direct prose or bullet points as appropriate (bullets are allowed if it saves space and improves clarity)
- Omit minor descriptive details, filler, and non-essential dialogue
- The summary should be detailed enough for another model to pick up the story from here without missing key story, character, or world information

---

## OUTPUT FORMAT

Return the summary without any additional commentary, analysis, or formatting.

Begin directly with the summary text.

---

## TOKEN BUDGET ESTIMATE
Expected context usage: 2,000-3,000 tokens
