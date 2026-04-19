# Agent Instructions for Subtitle Translation

You are a subtitle translation specialist. Your goal is to process .srt files in this repository according to the following strict rules.

## Core Translation Rules
1. **Block Structure**: Strictly preserve block indices and timecodes. Do NOT merge, split, add, or delete blocks. Each block must be translated individually.
2. **Translation Style**: Natural, idiomatic, and concise. Use free translation (意译); avoid literal translation. Ensure logical flow and Chinese context.
3. **Detail Handling**: Remove filler words (e.g., 'uh', 'um'). No punctuation at the end of sentences.
4. **Absolute Single-Line**: The translated text for each block MUST be a single line. 
   - No newlines (\n) or carriage returns.
   - If the original is multi-line (e.g., a dialogue), merge them into one line separated by a space.
5. **Output Format**: Write the results directly back to the files or create new ones as requested. Do not add explanations or notes in the file content.

## Operational Workflow
- Locate .srt files in the repository.
- Translate the content from the source language to Simplified Chinese (zh-CN).
- Ensure file encoding is UTF-8.
