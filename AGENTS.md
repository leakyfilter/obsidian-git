# Instructions for AI Agents

## Git Commit Guidelines
- Never add self-citations or "Generated with AI" attributions
- Keep commit messages clean and focused on the changes made
- Use conventional commit format when appropriate

## Privacy & Security
- **NEVER** commit private information to this repository
- This is a public/open-source repository - assume all content will be publicly visible
- Approved public information:
  - Username: `leakyfilter`
  - Email: `leakyfilter@icloud.com`
- **DO NOT** include:
  - API keys, tokens, or credentials
  - Personal details (phone numbers, addresses, private emails)
  - Proprietary or confidential information
  - Any content not intended for public consumption
- When in doubt, ask the user before committing potentially sensitive information

## Article Fetching Workflow
- Always try fetching articles first using available tools
- If initial fetch fails (403, JavaScript required, etc.), automatically fall back to browser automation if available
- This applies especially to Twitter/X articles and other JavaScript-heavy sites
- No need to ask user - just handle the fallback automatically

## Article Processing Guidelines
- Create article note in `/Articles` using Article Template concepts
- Extract atomic concept notes into `/Concepts`
- Only create concept notes for genuinely new concepts, not every noun in the article
- Interlink using `[[wikilinks]]`

## Cross-Article Connections
- Only create connections between articles when there is a **direct, practical relationship**
- Avoid philosophical or abstract connections (e.g., "both discuss invisible work")
- Good connection: Article A mentions specific companies/tools discussed in Article B
- Bad connection: Both articles share a thematic similarity or high-level concept

## Dashboard Workflow

**Article Processing Flow**:
1. User adds article URLs to Dashboard's "Inbox" section when they find interesting content
2. When user asks to "process inbox" or "process article X":
   - Remove the article from Dashboard Inbox
   - Process it (fetch content, create article note in /Articles, extract concepts to /Concepts)
   - Add the processed article to Dashboard's "Articles In Progress" section
3. User reads the processed article in their own time
4. User removes article from "Articles In Progress" when done (either manually or by asking an agent)

**Important**: Do not auto-update Dashboard without user request. It's their personal workspace.

## General Rules
- Follow the workflow documented in README.md
- Maintain consistency with existing vault structure and templates

---

## Agent-Specific Notes

### Claude Code
- Use `WebFetch` tool for fetching articles
- Fall back to `mcp__claude-in-chrome` browser automation for JavaScript-heavy sites
- Has access to full tool suite for file operations and web content

### Other Agents
- Add agent-specific notes as you integrate new agents
- Document any tool differences or capabilities
