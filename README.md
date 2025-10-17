# Persona-Driven UX Testing with Playwright MCP

Run automated UX sessions from real user perspectives. This project uses Claude and Playwright MCP to simulate realistic browsing and generate clear UX reports.

<!-- Repo contains: CLAUDE.md and personas/ -->

## Prerequisites
- An MCP-compatible client that supports Playwright (e.g., Claude Desktop with Playwright MCP).
- Install the Playwright MCP server:
  ```bash
  claude mcp add playwright npx '@playwright/mcp@latest'
  ```
- Ensure Chromium (or another supported browser) is installed and available to Playwright.

## Quick Start
1. Enable Playwright MCP in your AI client.
   ```bash
   claude mcp add playwright npx '@playwright/mcp@latest'
   ```
2. Load `CLAUDE.md` as the system instruction file.
3. Choose a persona from `personas/` and paste it as the user prompt.
4. Run the session. The agent will launch a browser, follow the persona’s behavior, capture screenshots, and write a `report.md` with findings and recommendations.

Tip: If your MCP client supports a working directory, set it to this repository so reports and artifacts save here.

## How It Works
- System layer (`CLAUDE.md`): Sets testing flow, allowed Playwright commands, and output formats.
- Persona layer (`personas/*.md`): Defines the target site, mindset/behavior, mission, and success criteria.
- Output: `report.md` plus screenshots and traces (typically in `.playwright-mcp/`).

## Adding or Editing Personas
1. Copy a file in `personas/` and update:
   - Name and mindset
   - Target website
   - Mission and success criteria
   - Behavior profile
2. Keep instructions concise and literal. Optionally specify a device or viewport for mobile testing.

## Example Workflow
```bash
# Add Playwright MCP
claude mcp add playwright npx '@playwright/mcp@latest'

# Start a session
# - Load CLAUDE.md as system prompt
# - Load personas/visual-browser.md as user prompt

# Outputs
# - report.md (UX findings)
# - .playwright-mcp/screenshots/
# - .playwright-mcp/traces/
```
