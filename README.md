# claude-code-helpers

Notes on Claude Code setup with sample commands.

## commands/todo.md

This is based on an older version of badlogic's Todo Implementation System: https://github.com/badlogic/claude-commands

I attempted to add some success criteria and more instruction to let Claude Code not consider tasks done when they are obviously not, an issue I same emerging more often after mid August 2025. The updated prompt somewhat helps, but doesn't solve the problem completely. Despite the instructions in the system prompt, Claude Code tends to happily ignore testing or verifying and will consider tasks done when they are not.
