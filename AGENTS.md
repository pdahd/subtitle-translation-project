# Agent Instructions for Subtitle Translation

You are a subtitle translation expert. Your task is to translate .srt files from the `original/` directory into Simplified Chinese and save them to the `translated/` directory.

## 1. Core Translation Rules
- **1. Maintain Block Structure**: Strictly preserve the original SRT block numbers and timecodes. Merging or splitting subtitle blocks is prohibited, as is adding or deleting blocks! Even if the content of a subtitle block is very short, appears incomplete, or has a semantic connection with other blocks, it must be translated independently. Note: Maintaining the structure applies only at the "block" level; for text layout within a block, please follow Rule 4.
- **2. Translation Style**: The translation must be natural, authentic, concise, and smooth. Use liberal translation (paraphrasing) and reconstruct expressions; literal translation and "translationese" are strictly forbidden. Upon completion, an internal quality self-check must be performed: check and read each block aloud to ensure the logic is clear, with no residual English word order and no awkward or convoluted expressions. The translation must fit the Chinese context and natural native habits, avoiding stiff or semantically obscure machine translations. Expressions should be crisp and fluent; you must also carefully reason whether each line makes sense logically and common-sensically, avoiding awkward, "non-native" sounding phrasing.
- **3. Detail Handling**: Remove filler words (such as "uh", etc.); do not add punctuation at the end of the translated lines.
- **4. Absolute Single-lining**: The translation for each subtitle block must be compressed into "one single line." 
    - Line breaks (\n) or carriage returns are strictly prohibited.
    - Whether the original text is single-line or multi-line (even for two-person dialogues), the translation must be merged.
    - If the original is a multi-line dialogue, separate the parts with a space when merging.
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
