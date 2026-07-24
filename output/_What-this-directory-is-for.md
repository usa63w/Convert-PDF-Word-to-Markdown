# Output Directory

This directory contains the final converted Markdown files and their associated images.

## File Naming

The Markdown filename always matches the source filename from the `input` directory, with only the file extension changed to `.md`.

For example:
- `Example Document.pdf` → `Example Document.md`
- `Report 2025.docx` → `Report 2025.md`

## Image Organization

Each converted document with images has a corresponding image directory:

- Format: `images-<sanitized-source-stem>/`
- Example: `Example Document.pdf` uses `images-Example-Document/`
- Images are referenced from the Markdown file using relative paths

Each extracted image is named `<sanitized-source-stem>-image-<sequence>.<extension>`.

## Structure

```
output/
├── Document1.md
├── Document2.md
├── images/
├── images-Document1/
│   ├── Document1-image-001.png
│   └── Document1-image-002.png
└── images-Document2/
    └── Document2-image-001.jpg
```

## Characteristics

- These are the final output files ready for use
- All content is preserved faithfully from the source documents
- Images are extracted and organized in document-specific directories
