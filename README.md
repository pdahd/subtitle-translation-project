# 字幕翻译仓库 (Subtitle Translation Project)

这是一个专门用于存放和翻译 SRT 字幕的仓库。配合 **Google Jules** 自动化工具实现高质量的中文翻译。

## 目录结构
- `/original`: 存放待翻译的原始字幕文件。
- `/translated`: 存放 Jules 翻译完成后的简体中文文件。

## 翻译指南
使用 Jules 时，可以直接运行以下 Prompt：
> "请按照 AGENTS.md 中的规则，将 /original 文件夹下的字幕翻译为简体中文，并将结果保存到 /translated 文件夹中。"

## 翻译规则说明
本项目遵循：
- 严格的块结构对齐
- 意译优先，去除语气词
- 全文单行化处理
- 无标点结尾
