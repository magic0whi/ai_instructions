# Custom AI Assistant Guidelines (Proteus Workflow)

## 1. Environment & Execution (NixOS / Custom Shells)
- **Nix-First Fallback:** If standard commands (like `python`, `pip`, etc.) result in a "command not found" error, DO NOT give up. Immediately attempt to execute the command inside the project's Nix shell environment using `nom develop` or `nix develop` (e.g., `nom develop /srv/sync_work/dev_flake#python --command ...`).
- **Temporary Files:** NEVER clutter the project workspace with temporary testing scripts, bash files, or intermediate text files. Always write temporary files to `/tmp/gemini/` for easy cleanup.
- **Smart Navigation:** Leverage the user's preferred modern CLI tools like `zoxide` (e.g., `cd $(zoxide query <target>)`) when constructing complex shell commands.
- **Custom Aliases:** The user may utilize custom bash or git aliases (e.g. `git dc`). NEVER assume a command is invalid or a typo; always attempt to execute it exactly as requested to verify its behavior before responding.
- Always use the native 'replace' or 'write_file' tools to edit files directly, rather than writing and executing Python scripts or shell commands to modify file contents.

## 2. Configuration & File Editing
- **Preserve Data Formatting:** When modifying JSON, YAML, or configuration files (using tools like `jq` or Python), strictly maintain the original data formatting. Specifically, preserve Scientific Notation (e.g., `1e-06` instead of `0.000001`) and avoid introducing unnecessary structural changes. Use `sed` for surgical replacements if JSON parsers aggressively reformat the output.
- **No-Dependency Preference:** When providing bash scripts or command-line solutions, prefer standard, built-in Unix tools (`curl`, `awk`, `sed`, `grep`) over requiring the user to install new packages (like `gh`), unless explicitly asked.
- Never automatically run git add or git commit unless explicitly instructed to do so by the user.
- **Code Style & Formatting:** Refrain from running automatic formatters (like `nix fmt` or `alejandra`). The core code style philosophy is to **minimize the total number of code lines** by maximizing the use of horizontal space.
  - Keep comments wrapped to a maximum of **80 columns**.
  - Keep code wrapped to a maximum of **120 columns**.
  - Rather than automatically reformatting, provide suggestions if you see opportunities to safely condense code lines or if these column limits are violated.
