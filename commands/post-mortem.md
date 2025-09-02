---
description: Analyze Claude Code chat history to improve CLAUDE.md and system prompts
allowed-tools: Read, Write, Edit, WebFetch, TodoWrite
---

Analyze Claude Code chat histories to identify successes, failures, and improvement opportunities. Generate actionable recommendations for updating CLAUDE.md and system prompt files to prevent similar issues.

If no arguments provided: Analyze the current chat session

Arguments can contain:

- Path to chat export file (JSON, markdown, or text format) OR URL to shared chat export
- Optional additional context, focus areas, or specific concerns

Examples:

- `/post-mortem` (analyzes current chat)
- `/post-mortem ~/Downloads/chat-export.json`
- `/post-mortem https://claude.ai/chat/abc123 focus on build process issues`
- `/post-mortem ./failed-session.md Claude kept missing test setup`

Actual arguments provided:

==== ARGUMENTS START

$ARGUMENTS

==== ARGUMENTS END

## Process

### Phase 1: ANALYSIS

1. **Load and analyze chat**:

   - If no arguments: Analyze the current conversation history and interactions
   - If file path provided: Use Read tool to load chat export
   - If URL provided: Use WebFetch tool to fetch chat export
   - Use any additional context provided to guide analysis focus
   - Parse the conversation flow and identify key interactions
   - Extract tool and command usage patterns and decision points
   - Note any error messages, confusion, or repeated attempts

2. **Categorize interactions**:
   - **Successful patterns**: What worked well and why
   - **Failed patterns**: What went wrong and root causes
   - **Missed opportunities**: Where Claude could have been more effective
   - **User friction points**: Where the user had to provide additional guidance

### Phase 2: ASSESSMENT

1. **Command usage**:

   - Identify Claude Code custom commands used
   - Locate and read the command markdown files in ./.claude/commands or ~/.claude/commands
   - Treat the command markdown files as system prompt files to be assessed and possibly improved

2. **Identify root causes**:

   - Missing context in CLAUDE.md and other system prompt files
   - Unclear or ambiguous instructions
   - Missing commands or workflow guidance
   - Tool selection issues
   - Architecture understanding gaps

3. **Pattern analysis**:

   - Recurring mistakes or confusion
   - Successful strategies that should be reinforced
   - Dependencies that weren't clear
   - Workflow steps that were skipped or misunderstood

### Phase 3: RECOMMENDATIONS

1. **CLAUDE.md improvements**:

   - Missing architectural context to add
   - Commands that need clearer documentation
   - Workflow patterns to emphasize
   - Common pitfalls to warn about
   - Examples that would clarify usage

2. **System prompt / command enhancements**:
   - Additional constraints needed
   - Process clarifications
   - Tool usage guidelines
   - Context that should be proactively provided

### Phase 4: IMPLEMENTATION PLAN

1. **Present findings**:

   - Summary of what went well
   - Key issues identified
   - Specific recommendations with rationale
   - Proposed changes to CLAUDE.md and other files

2. **User confirmation**:

   - STOP: "Review these findings and recommendations. Proceed with updating files? (y/n)"
   - Allow user to modify or reject specific recommendations

3. **Apply improvements**:
   - Update CLAUDE.md with approved changes
   - Modify other system prompt files (e.g. commands) as needed

## Workflow Examples

**Current chat analysis:**
User: `/post-mortem`

Processing:

1. No arguments provided - analyze current conversation
2. Review current chat history and tool usage patterns
3. Identify any issues or missed opportunities in current session
4. Present recommendations for CLAUDE.md improvements
5. Get user confirmation before updating files

**External chat analysis:**
User: `/post-mortem ~/Downloads/chat-export.json Claude struggled with our build process`

Processing:

1. Identify arguments as file path `~/Downloads/chat-export.json` + context `Claude struggled with our build process`
2. Use Read tool to load chat export
3. Focus analysis on build-related interactions
4. Identify missing build command documentation in CLAUDE.md
5. Present recommendations for CLAUDE.md improvements
6. Get user confirmation before updating files

## Output Checklist

- **Analysis report**: What went well vs. what went wrong
- **Root cause analysis**: Why issues occurred
- **Actionable recommendations**: Specific file changes to prevent recurrence
- **Updated documentation**: Improved CLAUDE.md and system prompts
