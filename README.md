# Research Vault - Workflow Guide

## Purpose
This Obsidian vault is designed for:
- Collecting interesting articles from across the internet
- Conducting research and learning from curated articles
- Writing summaries and organizing concepts for future reference
- Creating a mind map of connected ideas
- Keeping the vault tidy and easy to navigate

## Folder Structure

```
Dashboard.md    - Quick overview of current work and inbox tracking
/Articles       - Processed article notes with summaries
/Concepts       - Atomic notes on individual ideas/concepts
/Projects       - Ongoing personal projects and work
/Maps           - MOCs (Maps of Content) connecting related concepts
/Daily          - Daily notes for quick captures (optional)
/Templates      - Note templates for consistency
```

## Workflows

### 1. Article Capture & Processing
1. Save article links to `/Inbox` with minimal metadata (URL, date found, initial interest)
2. When ready to process: Use Claude to fetch the article, create a summary, extract key concepts
3. Move processed notes to `/Articles` with standardized frontmatter

### 2. Concept Extraction
- As articles are processed, create individual notes in `/Concepts` for each unique idea
- Each concept note should be atomic (one idea per note)
- Link concept notes to their source articles and related concepts using [[wikilinks]]

### 3. Research Sessions with Claude
- Provide article URLs → Claude fetches, summarizes, identifies key concepts
- Claude creates properly formatted Obsidian notes with [[wikilinks]] between concepts
- Claude suggests connections to existing concepts in the vault

### 4. Periodic Organization
- **Weekly**: Review `/Inbox`, process pending articles
- **Monthly**: Create/update Maps of Content to connect related concepts
- Use consistent tags (e.g., #to-review, #ai, #philosophy, #research)

### 5. Mind Mapping via MOCs
- Create Map of Content notes in `/Maps` that link related concepts by theme
- Example: "AI Ethics MOC" linking all ethics-related concepts and articles
- MOCs serve as navigational hubs for exploring connected ideas

## Working with Claude

When asking Claude to help with this vault:
- Claude can read this README to understand the vault structure and workflows
- Claude can fetch articles, create summaries, and generate properly formatted notes
- Claude can suggest connections between new concepts and existing notes
- Claude can help maintain organization and identify orphaned notes

## Tags Convention

- `#to-review` - Articles/concepts that need further review
- `#processed` - Articles that have been fully processed
- `#key-concept` - Important concepts worth revisiting
- `#needs-links` - Notes that need more connections to other concepts
- Subject-specific tags as needed (e.g., #ai, #philosophy, #neuroscience)
