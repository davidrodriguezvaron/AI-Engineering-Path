# Claude Code: DeepLearning.AI Notes

Notes from the DeepLearning.AI course on Claude Code: A Highly Agentic Coding Assistant

---

## 🧠 Managing Project Memory

### `/init`

Scans your codebase and creates a `CLAUDE.md` file in your project directory.

- `CLAUDE.md` guides Claude through your codebase, pointing out important commands, architecture, and coding style.
- It is automatically included in the context each time you launch Claude Code.

### `#` (Quick Memory)

Use `#` to quickly add memory or instructions. This is especially useful if you notice Claude Code repeating an error.

- **Example 1 (Environment):** `#use uv to run python files or add any dependencies`
- **Example 2 (Context):** Inform Claude about database schemas or specific logic:
  - `#The vector database has two collections: course_catalog and course_content`

---

## 🛠️ Commands Summary

| Command     | Description                                                  |
| :---------- | :----------------------------------------------------------- |
| `/clear`    | Clears current conversation history.                         |
| `/compact`  | Summarizes current conversation history to save tokens.      |
| `ESC`       | Interrupt Claude to redirect or correct it.                  |
| `ESC ESC`   | Rewind the conversation to an earlier point in time.         |
| `@`         | Mention files (e.g., `@README.md`) to include their content. |
| `/mcp`      | Manage MCP connections and check available servers/tools.    |
| `/hooks`    | Create hooks that execute based on certain events.           |
| `/commands` | Execute custom commands previously created.                  |

> [!TIP]
> You can run regular bash commands by prefixing them with `!` (e.g., `!ls -la`). Type `exit` to quit.

---

## ⌨️ Shortcuts & Interaction

| Action               | Shortcut                                                          |
| :------------------- | :---------------------------------------------------------------- |
| **Switch Mode**      | `Shift + Tab` (Toggle between _Planning_ and _Auto-accept_ mode). |
| **Screenshot (Mac)** | `Cmd + Shift + Ctrl + 4`                                          |
| **Screenshot (Win)** | `Win + Shift + S`                                                 |
| **Paste Screenshot** | `Ctrl + V` (Note: Support varies by OS).                          |

---

## 🚀 Advanced Features

- **Extended Thinking Mode**: For complex architecture or debugging, trigger with "think".
  - **Levels**: `think` < `think hard` < `think harder` < `ultrathink`.
- **Subagents (`Task` tool)**: Explicitly ask Claude to use subagents for brainstorming or multi-step investigation.
- **Worktrees**: Use Git worktrees to work on multiple features simultaneously without conflicts.
- **Platform Integration**: Integrate directly with GitHub to invoke Claude outside the CLI.

---

## 🧩 Skills

Skills let Claude Code load specialized expertise only when needed. This helps keep the context window efficient even when you have many skills installed.

### Progressive Disclosure

To protect the context window, skills are loaded in layers:

| Layer                                            | When Loaded           |
| :----------------------------------------------- | :-------------------- |
| **Metadata** (YAML: name, description)           | Always loaded         |
| **Instructions** (main `SKILL.md` content)       | Loaded when triggered |
| **Resources** (reference files, scripts, assets) | Loaded as needed      |

### Dynamic Loading Mental Model

- **Tools on Demand**: Skills can include scripts as tools that are used only when needed.
- **Progressive Exposure**: Detailed reference material stays one level deep from `SKILL.md` (e.g., `references/doc.md`) so Claude only reads them if the task requires high-depth knowledge.

### Skills vs. Others

| Feature     | MCP                                      | Skills                                      |
| :---------- | :--------------------------------------- | :------------------------------------------ |
| **Purpose** | Connects to external systems (DBs, APIs) | Teaches the agent what to do with that data |
| **Analogy** | Providing **Access**                     | Providing **Expertise**                     |

| Feature     | Tools                                | Skills                          |
| :---------- | :----------------------------------- | :------------------------------ |
| **Purpose** | Essential core capabilities          | Specialized knowledge/expertise |
| **Context** | Definitions always in context window | Loaded dynamically "on demand"  |

| Feature       | Subagents                           | Skills                                         |
| :------------ | :---------------------------------- | :--------------------------------------------- |
| **Purpose**   | Isolated context & tool permissions | Knowledge injected into main agent or subagent |
| **Operation** | Delegation to an independent worker | Informing _how_ work should be done            |

### `SKILL.md` Structure & Best Practices

#### Frontmatter

- **Required**: `name` (lowercase, numbers, hyphens; matches folder) and `description` (tells Claude _when_ to use it).
- **Optional**: `license`, `compatibility`, `metadata`, `allowed-tools` (experimental), `model`, `disable-model-invocation`, `user-invocable`, `argument-hint`, `context: fork` (runs skill in isolated subagent).

#### Body Content

No format restrictions, but use these recommended sections:

- Step-by-step instructions.
- Input/Output format & examples.
- Common edge cases.

#### Directory Layout

- `/assets`: Templates, diagrams, schemas, or lookup data.
- `/references`: Supporting docs. Keep individual files focused; add a TOC if >100 lines.
- `/scripts`: Executable helpers. Document dependencies and error handling clearly.

### Practical Guidance

- Keep `SKILL.md` under 500 lines; move detail to `/references`.
- Use forward slashes `/` in paths (cross-platform compatibility).
- **Evaluation / Unit Testing**: Define test cases in a JSON structure including:
  - `skills`: Which skills to test.
  - `queries`: Test prompts (e.g., "Generate questions from this file...").
  - `files`: Input files to use.
  - `expected_behavior`: List of success criteria (e.g., "Follows correct output structure").

### Using Skills with Subagents

1. **Explicit Injection**: Subagents don't inherit skills automatically. List them in the subagent's `skills` field.
2. **Context Forking**: Set `context: fork` in the skill's frontmatter to force it to run in a subagent (optionally specifying an `agent` like `Explore`).
