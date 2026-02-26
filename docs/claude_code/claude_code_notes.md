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
