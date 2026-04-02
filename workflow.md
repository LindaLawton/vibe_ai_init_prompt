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
- Verification: Run all unit tests.
  - If the NEW changes cause a failure: You are authorized to fix your own code until the tests pass. The task is not "Done" until your specific implementation is empirically proven to work.
  - If EXISTING/UNRELATED tests fail: Stop immediately. Do not attempt to fix legacy code or unrelated modules. Inform the user of the regression and wait for instructions.

### 3. Committing
- Once all tests (new and existing) pass, or once the user has acknowledged and bypassed an unrelated failure:
- Commit the changes locally using Conventional Commits format.
  - Prefix messages with [AI]. Example: fix: resolve memory leak in video processing (#123).
  - Push the branch to the remote repository.

### 4. Merging & Documentation
- Merge the branch into the main branch only when requested.
- Add a detailed comment to the corresponding GitHub Issue describing:
  - Scope Summary: A brief summary of the impact (e.g., Changed 3 files: +45/-12 lines).
  - What was changed: High-level list of modifications.
  - Technical Rationale: Why the change was made.
  - Verification: How the change was tested.
- Issue Closure Protocol: Do not close a GitHub issue autonomously.
  - When the work is complete, perform a "Resolution Check": cross-reference the original issue requirements against the final implementation and test results.
  - Report to the user: "The work appears to fully resolve Issue #[Number]. Would you like me to close it now?"
  - If the user explicitly instructs you to close the issue, proceed even if you believe there are pending edge cases, but leave a brief note in the issue comments regarding any unresolved observations.

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
- Before writing the 'Status of Batch' in handover.md, always run git branch -a and git status to confirm which issues have corresponding remote branches.

### 7. The Handover Protocol Prompt
  You are to maintain a high-fidelity record of our progress to ensure seamless session continuity. At the end of every session, or whenever I request     a "status sync," you are responsible for updating a file named handover.md.

- File Structure: handover.md
You must format the file using the following Markdown points structure as follows should be in GitHub Flavored Markdown:

  1. Session Handoff - [YYYY-MM-DD]: Current date.
  2. Completed Today: A detailed bulleted list of technical accomplishments. Include specific file names, database schema changes (types, nullability), and logic updates (e.g., Pydantic V2 migrations).
  4. Status of Batch: Current status of active Issues (Open/Closed/Created). This must be verified against the locally checked-out branches or the configured version control system (e.g., GitHub API/CLI) to ensure the handoff reflects the true state of the repository.
  5. Next Steps: Provide the immediate top 3–5 actions for the next session. These must be formatted as a GFM Task List (e.g., - [ ] Task Description) so progress can be tracked.
  6. Important Memories: Critical operational constraints (e.g., "Do not run interactive scripts," "Check with user before fixing bugs").


