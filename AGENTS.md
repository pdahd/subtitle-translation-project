# Agent Instructions for Subtitle Translation

You are a subtitle translation expert. Your task is to translate .srt files from the `original/` directory into Simplified Chinese and save them to the `translated/` directory.

## 1. Core Translation Rules
- **Block Structure**: Strictly preserve block indices and timecodes. Do NOT merge, split, add, or delete blocks. Each block must be translated individually, even if it seems incomplete or short.
- **Translation Style**: Natural, idiomatic, and concise (Free Translation/意译). Avoid literal translation. Ensure the tone fits the Chinese context and remains smooth.
- **Detail Handling**: 
    - Remove filler words (e.g., 'uh', 'um', 'well').
    - Do NOT add any punctuation at the end of translated sentences.
- **Absolute Single-Line**: Each block's translation MUST be a single line.
    - No newlines (\n) or carriage returns are allowed within a block.
    - If the source is multi-line or a dialogue, merge them into one line separated by a space.
- **Output Requirement**: The final output should contain only the SRT content. Do not include any explanations, notes, or code block markers within the file.

## 2. Context Awareness (Crucial)
- **Reference Context**: Before translating an `.srt` file, always check for a corresponding `.txt` or `.context.txt` file with the same name in the `original/` folder.
- **Usage**: Use the provided video summary, plot analysis, and key terms to ensure the translation is contextually accurate (e.g., proper names of places, characters, or specific cultural references).

## 3. Operational Workflow
1. Read `AGENTS.md` to understand the constraints.
2. Locate the target `.srt` file in `original/`.
3. Read the corresponding context file if it exists.
4. Process the translation according to the rules above.
5. Write the output to `translated/[filename].srt` using UTF-8 encoding.
6. Provide a summary of the changes in the commit message.
