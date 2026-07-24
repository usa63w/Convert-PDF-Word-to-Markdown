---
name: document-to-markdown
description: Convert Microsoft Word and PDF documents into faithful Markdown reproductions. Use this skill whenever a document must be converted without rewriting, summarizing, correcting, or interpreting its contents. Works with Copilot, Claude, Gemini, or OpenAI.
---

# Document to Markdown

This skill performs faithful document conversion.

Repository-wide behaviour is defined in:

`AGENTS.md`

This skill implements the document inspection, extraction, conversion, and validation process.

Source documents are selected from `input/` and processed by file type (`.docx` or `.pdf`).

Before performing or implementing any conversion, read and follow `references/conversion-rules.md`.

Use the separate per-document image-directory and sanitized filename convention defined in the conversion rules.

Detailed conversion guidance may be placed in the `references` directory.

Executable conversion utilities may be placed in the `scripts` directory.
