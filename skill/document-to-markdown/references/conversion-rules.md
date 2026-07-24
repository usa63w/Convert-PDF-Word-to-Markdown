# Conversion rules

## Objective

Convert each source document into a faithful Markdown representation.

Conversion means changing the file format only. It does not include editing, rewriting, interpretation, correction, or improvement.

## Source files

Process source files from:

```text
input/
```

Supported source types are:

- Microsoft Word (`.docx`)
- PDF (`.pdf`)

Do not process files from any other directory unless explicitly instructed.

## Output files

Write completed Markdown files to:

```text
output/
```

Retain the complete source filename and replace only its extension with `.md`.

Examples:

```text
input/Example Document.docx
output/Example Document.md
```

```text
input/Example Document.pdf
output/Example Document.md
```

Do not overwrite an existing Markdown file unless explicitly instructed.

## Text preservation

Preserve all source text exactly.

Do not:

- rewrite text
- summarize text
- improve text
- correct grammar
- correct spelling
- change punctuation
- change capitalization
- modernize language
- standardize terminology
- alter wording to match a style guide
- insert explanatory text
- omit repeated text because it appears redundant

Preserve visible text in its original reading order.

## Markdown structure

Represent document structure using standard Markdown where the equivalent is clear.

Preserve:

- headings and heading levels
- paragraphs
- numbered lists
- bulleted lists
- nested lists
- tables
- block quotations
- hyperlinks
- footnotes and endnotes
- captions
- horizontal separators
- visible page breaks where they materially affect the document
- bold, italic, and strikethrough formatting where present and reliably identifiable

Do not infer structure that is not visibly present in the source.

Do not use Markdown formatting merely because text appears important.

## Images and visual elements

Treat the following as visual elements:

- photographs
- illustrations
- diagrams
- charts
- screenshots
- logos
- icons
- signatures
- decorative graphics
- embedded objects that cannot be represented faithfully as text

Derive a sanitized source stem by:

- removing the source filename extension
- replacing each run of one or more whitespace characters with a single hyphen
- preserving all other characters

Create a separate image directory for each source document:

```text
output/images-<sanitized-source-stem>/
```

Name extracted images using the sanitized source stem followed by a sequential image number:

```text
<sanitized-source-stem>-image-001.png
<sanitized-source-stem>-image-002.jpeg
```

For example, `Example Document.pdf` uses:

```text
output/images-Example-Document/
```

and contains files such as:

```text
Example-Document-image-001.png
Example-Document-image-002.jpeg
```

Preserve the original image format and quality where practical.

Insert a Markdown image reference to the exact extracted file at the position where each visual element appears. Because completed Markdown files and their document-specific image directories are both in `output/`, use the image directory name as the relative path. Use forward slashes and empty alt text:

```text
![](<images-Example-Document/Example-Document-image-001.png>)
```

Replace the example directory and filename with the exact sanitized names for the source document. Enclose the destination in angle brackets.

The image reference must appear on its own line. Do not use a generic `<image>` tag.

Do not describe, interpret, summarize, caption, or perform OCR on a visual element unless explicitly instructed.

If a caption exists as document text, preserve the caption separately from the image reference.

## Tables

Convert tables to Markdown tables when their structure can be represented faithfully.

Preserve:

- row order
- column order
- cell wording
- blank cells
- repeated values
- captions and notes

Do not combine, split, rename, summarize, or reorder columns.

If merged cells, nested tables, or complex formatting cannot be represented faithfully using a Markdown table, preserve the content as closely as possible and flag the location for manual review.

## Headers and footers

Preserve header or footer text when it forms part of the document content.

Do not repeatedly insert identical running headers or footers on every page unless their repetition carries meaning.

Do not remove unique header or footer content, including document identifiers, version details, confidentiality markings, dates, or page-specific notes.

## Page numbers

Do not include page numbers that exist only for navigation.

Preserve page numbers when they form part of a citation, reference, table, form, or other meaningful content.

## Working files

Place all temporary and intermediate files in:

```text
working-files/
```

This includes:

- extracted document XML
- rendered PDF pages
- temporary image files
- diagnostic reports
- extraction logs
- intermediate Markdown
- comparison output

Do not place temporary files in `output/` or any `output/images-<sanitized-source-stem>/` directory.

## Uncertainty and manual review

Never guess at illegible, missing, obscured, or ambiguous content.

Where content cannot be converted reliably:

1. preserve all content that can be determined confidently
2. insert the following marker at the affected location:

```text
<!-- MANUAL REVIEW REQUIRED: reason -->
```

1. replace `reason` with a brief factual explanation
2. do not invent replacement content

## Validation

Before treating a conversion as complete, verify that:

- all source text is represented
- wording has not changed
- spelling has not changed
- punctuation has not changed
- content order is preserved
- headings and lists are represented
- tables are complete
- every visual element has a corresponding Markdown image reference containing the exact extracted filename
- extracted images exist in the correct `output/images-<sanitized-source-stem>/` directory
- every Markdown image reference resolves from `output/` to its corresponding document-specific image file
- no generic `<image>` tags remain
- no explanatory or interpretive content was introduced
- the output filename matches the source filename
- temporary files are confined to `working-files/`

Report any unresolved discrepancies rather than silently accepting them.
