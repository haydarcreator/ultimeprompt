# ultimeprompt
the best skills for claude to write a prompt
Prompt Builder

Generate exhaustive, build-ready prompts that another LLM can execute to recreate a working version of a known product (game, app, website, tool, software).

The output is a markdown document containing a single long structured prompt — written in the second person, addressed to the LLM that will build the thing. The user copies this prompt into Claude / GPT / another AI to get a working implementation back.

Core principle

A good prompt-builder output is exhaustive by default. If the user asks for a prompt to recreate Minecraft, the output covers every menu, every block, every mob, every mechanic, every edge case — not a vague one-paragraph summary. The user is paying you to do the analysis work now so the downstream LLM doesn't have to guess.

Vague prompts produce vague apps. Exhaustive prompts produce working apps.

Workflow
Step 1 — Identify the target

Read the user's request and identify exactly what product they want a prompt for. If it's ambiguous (e.g., "build me a prompt for a chess app" — web? mobile? multiplayer? AI opponent?), ask one clarifying question before proceeding. If it's a well-known product (Minecraft, Spotify, Wordle, Tetris, Notion), don't ask — you know what it is.

Step 2 — Detect depth level

Default depth is exhaustive. Override only if the user explicitly says otherwise:

"court", "short", "bref", "rapide", "simple" → Short (~500-1000 words, core features only)
"standard", "moyen", "normal" → Standard (~1500-3000 words, all major features + key edge cases)
"exhaustif", "complet", "détaillé", "long", "tout", "everything", "exhaustive", "comprehensive", or no qualifier → Exhaustive (3000+ words, every feature, every screen, every edge case)
Step 3 — Analyze the target

Before writing, mentally walk through the product as if you were using it for the first time. Cover all of these angles — skip a section only if it genuinely does not apply:

Overview & purpose — what is this thing, who is it for, what problem does it solve
Entry points & first-run experience — splash screen, login, onboarding, tutorial
Main UI / navigation — every screen, every menu, every tab, every button
Core mechanics / features — the things that make this product this product
Secondary features — settings, preferences, accessibility, account management
Content / assets — every type of object, item, level, character, sound, image, font
Data model & state — what gets saved, where, in what format
Persistence & storage — local storage, database, cloud sync
Networking — API calls, multiplayer, real-time updates
Edge cases & error handling — empty states, errors, offline, loading
Visual design — color palette, typography, iconography, animations
Audio — music, sound effects, voice
Performance constraints — target framerate, load times, memory
Tech stack suggestion — appropriate languages, frameworks, libraries

For games specifically, add: physics, controls, levels/worlds, enemies/NPCs, scoring, progression, save system, win/loss conditions.

For apps specifically, add: user roles, notifications, search, filters, sorting, sharing, export.

Step 4 — Write the prompt

Write the prompt as a markdown document using the structure below. Address the LLM directly in the second person ("You will build...", "Your output should..."). Be concrete and prescriptive — say "the inventory bar has 9 slots" not "the inventory has some slots".

Use the structure in references/template.md as the skeleton. Adapt sections — drop ones that don't apply, add ones the product needs. Don't force a square peg into a round hole.

Step 5 — Save and present

Save the prompt as a .md file in /mnt/user-data/outputs/ with a filename based on the target (e.g., prompt-minecraft.md, prompt-spotify.md). Then call present_files to give the user direct access. After presenting, give a 2-3 sentence summary of what's in the prompt — don't restate the whole thing.

Output format

The generated prompt must:

Be written in markdown
Be addressed to an LLM in the second person
Open with a one-paragraph mission statement ("You will build a working clone of [X]...")
Use clear ## section headers matching the analysis angles above
Use concrete specifications (numbers, names, exact behaviors) — never "some", "various", "etc."
End with an Acceptance Criteria section listing what the finished build must demonstrate
Be self-contained — the downstream LLM should not need to ask follow-up questions
Language

Match the user's language. If they wrote in French, write the prompt in French. If they wrote in English, write in English. If they mixed (common for Faissal), default to French unless the target product is anglophone (e.g., Wordle).

What this skill does NOT do
It does not build the product — it builds the prompt that builds the product.
It does not generate images, sounds, or assets — it describes them in enough detail that the downstream LLM (or asset generator) can produce them.
It does not run the prompt itself afterwards. If the user wants the actual build, that's a separate request.
Reference

See references/template.md for the full prompt skeleton with all section headers and example phrasings.
