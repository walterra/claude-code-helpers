# claude-code-helpers

Notes on Claude Code setup with sample commands.

I played around with subagents a bit. I'm still missing a real use case for them, I prefer to run parallel Claude Code sessions and use commands instead. I suspect subagents might pollute you system prompt.

## commands/todo.md

This is based on an older version of badlogic's Todo Implementation System: https://github.com/badlogic/claude-commands

I attempted to add some success criteria and more instruction to let Claude Code not consider tasks done when they are obviously not, an issue I same emerging more often after mid August 2025. The updated prompt somewhat helps, but doesn't solve the problem completely. Despite the instructions in the system prompt, Claude Code tends to happily ignore testing or verifying and will consider tasks done when they are not.

## commands/commit.md

A structured workflow for committing staged files only. This command ensures Claude Code follows a disciplined approach to git commits:

- Commits only currently staged files (never uses bulk staging like `git add .`)
- Creates concise one-liner commit messages (60 char max, no semantic prefixes)
- Handles pre-commit hook issues by running maintenance commands automatically
- Leaves unstaged files untouched, even if modified by formatters during the process

## commands/curriculum.md

Creates comprehensive onboarding documentation based on code changes in the current branch. This command generates structured learning materials in `./llm-docs/`:

- Analyzes all files changed/added in the current branch using `git diff main...HEAD`
- Asks targeted questions about audience, focus, detail level, and format preferences
- Extracts technical concepts, frameworks, and architectural patterns
- Creates modular markdown documentation with numbered chapters
- Organizes content from basic to advanced concepts with practical examples and exercises

## commands/post-mortem.md

Analyzes Claude Code chat histories to improve CLAUDE.md and system prompts. This command provides structured analysis of conversation patterns:

- Examines current chat session, file exports, or shared URLs
- Categorizes successful patterns vs. failures and missed opportunities
- Identifies root causes in missing context, unclear instructions, or workflow gaps
- Generates specific recommendations for updating CLAUDE.md and command files
- Requires user confirmation before applying any documentation improvements
