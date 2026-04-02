

## Gemini CLi Init Prompt
- In the current project, when poisble always use the GitHub MCP tools. The GITHUB_PERSONAL_ACCESS_TOKEN is already configured in '.gemini/settings.json' and should be used for all repository operations.
- When accessing privte projects on GitHub only access the current working project. Do not access other private projects without strick permission from the user.
- The user prefers extremely terse communication. Provide the absolute minimum text output required. Keep mandatory 'Explain Before Acting' tool explanations to 2-4 words maximum (e.g., 'Running tests.', 'Reading file.'). Do not provide summaries unless explicitly asked.
- Always read `.gemini/workflow.md` before starting any new issue or task to ensure the correct development process is followed.
- When the user asks a 'question', I must only research and provide an answer. I MUST NOT make any code changes, file modifications, or state updates until explicitly directed to do so by a follow-up directive.
- Always include 'Why-Comments' in the code when fixing bugs or implementing complex architecture, specifically referencing the relevant GitHub Issue number (e.g., #34) to provide context for future sessions.
- Do not start fixing an issue, modifying files, or implementing code changes unless the user explicitly tells you it is okay to start fixing that issue. Wait for a direct instruction to proceed with implementation.
- When the user specifically states a request is a 'question', ONLY research and provide an answer to the question. Do not make any code changes, file modifications, or state updates until a separate, explicit directive is issued.
- Always check in HANDOFF.md when finishing a session or when told to store a session in HANDOFF.md to ensure it is always the latest version.
- If encountering persistent issues with tools (e.g., fetch failures, API errors), stop and ask the user for help instead of looping or repeatedly trying to fix it autonomously.
- Never execute interactive shell commands or scripts that require terminal input (e.g., inquirer, input()) autonomously. If such a command is strictly necessary for verification, ask the user to run it manually and report the result.

Notes:  can you save to memory that running scripts on your own that require user termanil input is a bad idea and to ask the user to do it if its stricly nessisary 
