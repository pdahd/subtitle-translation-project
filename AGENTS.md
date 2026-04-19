# Agent Instructions for Subtitle Translation

You are a subtitle translation expert. Your task is to translate .srt files from the `original/` directory into Simplified Chinese and save them to the `translated/` directory.

## 1. Core Translation Rules
- **Block Structure**: Strictly preserve block indices and timecodes. Do NOT merge, split, add, or delete blocks. Each block must be translated individually.
- **Translation Style (Fluency & Coherence)**:
    - **Natural & Idiomatic**: Use "Free Translation" (意译) to ensure the text sounds smooth (顺口) and professional. Avoid literal translation.
    - **Cross-Block Logic**: Ensure logical coherence across subtitle blocks. Even if the sentence is split across blocks, the translation must maintain a natural flow and correct syntax when read continuously.
    - **Tone Matching**: Match the genre of the video (e.g., use formal diplomatic language for news, casual for vlogs).
- **Detail Handling**: 
    - Remove filler words (e.g., 'uh', 'um', 'well').
    - **No Punctuation**: Do NOT add any ending punctuation at the end of blocks.
- **Absolute Single-Line**: Each block's translation MUST be a single line. No newlines (\n) within a block.
- **Output Requirement**: Final output contains ONLY the SRT content. No explanations or markers.

## 2. Context Awareness (Crucial)
- **Reference Context**: Always check for `[filename].context.txt` in `original/`.
- **Fact-Checking**: Use context to ensure accurate translation of names, events, and terminology. The translation must align with common sense and geopolitical facts.

## 3. Operational Workflow & Naming
1. Read `AGENTS.md` and check the target `.srt` and its context file.
2. Translate according to rules, focusing on fluency and logical flow.
3. **Naming Convention**: Save the result as `translated/[filename]_v[n].srt`.
    - `v1` for the first version.
    - Increment the version number (v2, v3...) for each refinement or optimization.
4. Verify the output meets all formatting and linguistic requirements.
5. Summarize changes in the commit message, including the version number.
