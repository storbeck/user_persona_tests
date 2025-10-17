# Persona-Driven UX Testing with Playwright MCP

**Run automated UX sessions through real user perspectives.**
This project uses **Claude + Playwright MCP** to simulate realistic browsing behavior and generate structured UX reports.

---

## 📂 What’s Inside

| File/Folder                 | Purpose                                                                                    |
| --------------------------- | ------------------------------------------------------------------------------------------ |
| `CLAUDE.md`                 | Core system instructions for the autonomous UX evaluator (load as your **system prompt**). |
| `personas/`                 | User profiles and missions that define how the agent behaves and what it tries to achieve. |
| ├ `cautious-newcomer.md`  | A tentative first-time visitor who values clarity and reassurance.                         |
| ├ `mobile-multitasker.md` | A busy user switching between apps on a small screen.                                      |
| ├ `visual-browser.md`     | A visually-driven user who navigates via imagery rather than text.                         |
| └ `efficient-shopper.md`  | A pragmatic user optimizing for speed and simplicity.                                      |

---

## ⚙️ Prerequisites

Before you begin:

1. **An MCP-compatible client** that supports Playwright, such as:

   * Claude Desktop with a Playwright MCP server
   * Any MCP runner connected to Playwright
2. **Install the Playwright MCP server:**

   ```bash
   claude mcp add playwright npx '@playwright/mcp@latest'
   ```
3. **Ensure Chromium** (or your chosen browser) is installed and available to Playwright.

---

## 🚀 Quick Start

1. **Enable Playwright MCP** in your AI client.

   ```bash
   claude mcp add playwright npx '@playwright/mcp@latest'
   ```
2. **Load `CLAUDE.md`** as your system instruction file.
3. **Choose a persona** from the `personas/` folder and paste its contents as the user prompt.
4. **Run the session.** The agent will:

   * Launch Chromium with tracing and video (if supported)
   * Emulate the persona’s mindset and behavior
   * Capture screenshots during key interactions
   * Generate a structured `report.md` with observations and recommendations

💡 **Tip:** If your MCP client supports per-session working directories, set it to this repository root so all reports and artifacts are saved here.

---

## 🧠 How Sessions Work

### System Layer (`CLAUDE.md`)

Defines the high-level testing flow:

* Initialize environment → adopt persona → perform tasks → summarize results
* Enumerates allowed Playwright commands
* Specifies output formats (Markdown report, screenshot paths, etc.)

### Persona Layer (`personas/*.md`)

Describes *who* the user is and *how* they behave:

* **Target site** (e.g., `https://www.automationexercise.com/`)
* **Mindset & behavior profile** (e.g., “browses by category, avoids search”)
* **Mission** (goal and success criteria)

### Output Layer

Each run produces:

* `report.md` — Summary of steps, pain points, strengths, and recommendations
* Screenshots & traces — Saved in `.playwright-mcp/` by default

---

## ✍️ Adding or Editing Personas

1. Copy an existing file from `personas/` and update:

   * **Name & mindset** (e.g., “Detail-oriented researcher”)
   * **Target website**
   * **Mission & success criteria**
   * **Behavior profile** (e.g., “scrolls thoroughly, ignores ads”)
2. Keep instructions **concise and literal** — the agent follows them exactly.
3. Optionally define **viewport or device** (e.g., *iPhone 13 — 375×812*) for mobile simulations.

---

## 🧩 Example Workflow

```bash
# 1. Add Playwright MCP
claude mcp add playwright npx '@playwright/mcp@latest'

# 2. Start a session
# Load CLAUDE.md as system prompt
# Load personas/visual-browser.md as user prompt

# 3. Observe results
#   - report.md (UX findings)
#   - .playwright-mcp/screenshots/
#   - .playwright-mcp/traces/
```
