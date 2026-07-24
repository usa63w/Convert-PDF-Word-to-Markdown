# Document to Markdown Conversion Agent

## Purpose

This repository converts Microsoft Word and PDF documents to Markdown.

The objective is faithful preservation of the original document, not interpretation or improvement.

## Core Principles

The following rules apply to every conversion.

1. Preserve all original wording exactly.
2. Do not rewrite, summarize, simplify, or improve the content.
3. Do not correct grammar.
4. Do not correct spelling.
5. Do not modernize language.
6. Do not interpret document structure beyond what is required to represent it in Markdown.
7. Preserve the original order of all content.
8. Preserve headings, paragraphs, lists, tables, captions, footnotes, page breaks (where practical), and other visible document elements.
9. Preserve blank lines where they affect readability.
10. Preserve whitespace where it carries meaning.

## Images

Whenever a document contains an image, diagram, logo, chart, screenshot, signature, or other non-text visual:

- derive a sanitized source stem by removing the source extension and replacing each run of whitespace characters with a single hyphen
- create a separate image directory named `output/images-<sanitized-source-stem>`
- extract the original image into that document-specific image directory
- preserve the original image quality where possible
- insert a Markdown image reference to the exact extracted file at the position where the image appeared
- name each extracted image `<sanitized-source-stem>-image-<sequence>.<extension>`
- use a relative path from the Markdown file in `output` to the document-specific image directory
- use forward slashes in the path and empty alt text so the reference does not add a description

```text
![](<images-Example-Document/Example-Document-image-001.png>)
```

For example, `Example Document.pdf` uses `output/images-Example-Document/`. Preserve non-whitespace characters from the source stem. Do not use a generic `<image>` tag. Verify that every image reference resolves to an existing file in the document-specific image directory.

Never describe, analyse, interpret, caption, or perform OCR on an image unless explicitly instructed.

## Output

Source documents from:

```
input
```

Supported source types are Microsoft Word (.docx) and PDF (.pdf).

Source files from this directory produce Markdown files in

```
output
```

The Markdown filename must always match the source filename, replacing only the extension with `.md`.

## Working Files

Temporary files, extracted text, OCR output, intermediate artefacts, and diagnostic files belong only in

```
working-files
```

These files are never considered part of the final output.

## Reference Material

Documents placed in the `reference` directory are reference sources.

Reference documents may only be consulted when explicitly instructed.

Reference documents must never influence the wording of converted documents.

## Behaviour

When uncertain, preserve the original.

Never invent missing content.

Never silently discard content.

If something cannot be represented faithfully in Markdown, preserve as much as possible and clearly identify the location requiring manual review.
