You are about to commit staged files only.

- 1. Identify staged files using `git diff --cached --name-only`.
- 2. `git commit -m "<message>"` just the currently staged files with a proper one-liner commit message. it must be a one-liner message without any credit information like "generated with" or "co-authored by". 60 max char length. no semantic prefix. IMPORTANT: Analyze the actual changes (use `git show --name-status` or `git diff --cached`) to craft an accurate message that describes what was done - don't default to generic verbs like "add" when files were modified or updated.
- 3. Check if any pre-commit hooks found issues (for example linting or TS errors).

If pre-commit hooks found issues:

- 3.1 Use the repos maintenance commands like `pnpm lint`, `pnpm tsc:check` or similar to fix formatting, linting or type issues automatically.
- 3.2 Fix any remaining issues manually.
- 3.3 If you have to stage files, ONLY stage files you identified in step 1 (identify staged files).
- 3.4 NEVER stage files that are not part of the list created in step 1 (identify staged files).
- 3.5 If a maintenance script modified an unstaged file, leave it unstaged
- 3.6 NEVER use `git add .` or similar bulk staging commands

Example: If only A.ts was originally staged, but the formatter also modified B.ts (which was unstaged), only stage A.ts for the commit. Leave B.ts unstaged.
