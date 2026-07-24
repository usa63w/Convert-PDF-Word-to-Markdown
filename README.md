# Convert PDF & Word to Markdown

A tool for converting Microsoft Word (.docx) and PDF documents to Markdown format while preserving the faithful representation of the original documents.

## Core Principles

This conversion tool follows strict principles to ensure the integrity of your original documents:

1. **Preserve all original wording exactly** - No rewriting, summarizing, or simplification
2. **Preserve document structure** - Headings, paragraphs, lists, tables, captions, and footnotes are all maintained
3. **Preserve visual elements** - Images, diagrams, and other graphics are extracted and properly referenced
4. **Preserve formatting intent** - Blank lines and meaningful whitespace are retained
5. **No interpretation** - Grammar, spelling, and language are not corrected or modernized
6. **Original order maintained** - Content is presented exactly as it appears in the source document

## Directory Structure

### `/input`

Place your source Microsoft Word (.docx) or PDF (.pdf) documents here. See `_What-this-directory-is-for.md` for details.

### `/output`

Contains the final converted Markdown files and their associated images:

- Markdown files match the source filename with `.md` extension
- Images are organized in document-specific directories (e.g., `images-Document-Name/`)
- See `_What-this-directory-is-for.md` for details

### `/working-files`

Temporary files, intermediate artifacts, and diagnostic outputs used during conversion. These files are not part of the final output and can be safely deleted after conversion. See `_What-this-directory-is-for.md` for details.

### `/skill`

Contains the conversion agent specifications and reference materials.

## Image Handling

When documents contain images or diagrams:

- A document-specific image directory is created (e.g., `images-Example-Document/`)
- Images are extracted and preserved in their original quality
- Markdown image references use relative paths to the extracted files
- Each image is named with a sequence number: `<document-name>-image-<number>.<extension>`

Example:

```markdown
![](<images-Example-Document/Example-Document-image-001.png>)
```

## Usage

1. Add your source documents (.docx or .pdf) to the `/input` directory
2. Run the conversion pipeline
3. Find your converted Markdown files in the `/output` directory
4. Associated images will be in document-specific subdirectories within `/output`

## Output Verification

When uncertain about a conversion, the original content is always preserved. Manual review of specific sections may be required in complex cases, which will be clearly marked in the output.

## Git Configuration

This repository uses the following structure:

- Only `_What-this-directory-is-for.md` files are tracked in input/, output/, and working-files/ directories
- All other files in those directories are ignored to keep the repository lean
- The `.vscode/` directory is included for consistent VS Code configuration across the team
- Processed documents should be managed separately from this repository

---

For more information, see the principle documents and agent specifications in the `/skill` directory.
