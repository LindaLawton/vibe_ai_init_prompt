# Gemini Developer Workflow

## Core Mandates
1. **Explicit Authorization:** Never start work on an issue unless explicitly instructed by the user. Do not preemptively implement fixes based on observations or task lists.
2. **Clean Slate:** Always ensure the local repository is clean before starting new work (`git status`).

## Issue Resolution Process
When authorized to work on an issue, follow these steps strictly:

### 1. Branching
- Create a new, descriptively named branch for the issue before making any changes.
- Example: `git checkout -b fix/issue-123-storage-hooks`

### 2. Implementation & Testing
- Implement the requested changes.
- **Verification (AI):** Write and run automated tests to verify the changes locally. The implementation is not complete until it is empirically proven to work.
- **Verification (User):** If possible and applicable, provide clear instructions for the user to manually verify the changes.

### 3. Committing
- Before commiting ensure that all unit tests in the project run without failure.  If they fail informe the user do not fix unless asked to.
- Commit the changes locally using **Conventional Commits** format.
  - Examples: prefex commit messages with [AI] Message example: `fix: resolve memory leak in video processing (#123)`, `feat: add gcs cleanup hooks (#26)`.
- Push the branch to the remote repository.

### 4. Merging & Documentation
- Merge the branch into the main/master branch only when requested.
- Add a detailed comment to the corresponding GitHub Issue describing:
    - What was changed.
    - Why the change was made (the technical rationale).
    - How the change was tested and verified.
- Close the issue if the work fully resolves it.

### 5. Cleanup
- Delete the feature branch locally: `git branch -d <branch_name>`
- Delete the feature branch remotely on GitHub: `git push origin --delete <branch_name>`
- Ensure you have fetched and pruned the remote references: `git fetch --prune`
- 
### 6. Operational Rules
Contextual Awareness: Before starting any work, always read handover.md to understand the current state of the codebase and pending tasks.
- Why-Comments: When writing code, always include comments that reference the relevant GitHub Issue number (e.g., // Ref Issue #35: Updated validation logic).
- Strict Boundaries: * Do not start fixing new issues without explicit user permission.
- If a tool or script fails repeatedly, stop and report it; do not enter a loop.
- NEVER execute interactive shell commands or scripts that require terminal input. If a script needs input, provide the command and ask me to run it.
- Automatic Trigger: Whenever we finish a major task or at the conclusion of our conversation, ask me: "Would you like me to sync our progress to handover.md before we finish?"

### 7. The Handover Protocol Prompt
  You are to maintain a high-fidelity record of our progress to ensure seamless session continuity. At the end of every session, or whenever I request     a "status sync," you are responsible for updating a file named handover.md.

- File Structure: handover.md
You must format the file using the following Markdown points structure as follows should be in GitHub Flavored Markdown:

  1. Session Handoff - [YYYY-MM-DD]: Current date.
  2. Completed Today: A detailed bulleted list of technical accomplishments. Include specific file names, database schema changes (types, nullability), and logic   3. updates (e.g., Pydantic V2 migrations).
  4. Status of Batch: Current status of GitHub Issues (Open/Closed/Created).
  5. Next Steps: The immediate top 3 actions for the next session.
  6. Important Memories: Critical operational constraints (e.g., "Do not run interactive scripts," "Check with user before fixing bugs").


