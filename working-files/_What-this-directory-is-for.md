# Working Files Directory

This directory contains temporary files, intermediate artifacts, and diagnostic outputs used during the document-to-Markdown conversion process.

## Purpose

- Temporary processing files
- Extracted text during conversion passes
- OCR output and intermediate processing steps
- Diagnostic files and validation reports
- Extracted images before final organization
- Chunked content for processing
- Build and validation artifacts

## Important Note

**These files are never considered part of the final output.** They are purely for internal processing and debugging purposes.

## Contents

- `dependencies/` - External libraries and dependencies required for processing
- `[document-name]/` - Document-specific working files and intermediate outputs
- `*.py` - Processing scripts for extraction and validation
- `*.json` - Diagnostic and validation reports
- `*.txt` - Extracted text output
- `*.md` - Intermediate Markdown drafts

## Cleanup

Files in this directory can be safely deleted after conversion is complete and the final output is validated.
