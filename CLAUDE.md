# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of Claude Code helpers and sample commands, containing:

- Custom commands for Claude Code workflow optimization
- Todo implementation system based on badlogic's approach with enhancements
- Git commit helpers with structured workflows

## Key Commands and Workflows

### Todo Implementation System (`commands/todo.md`)

A structured workflow system for implementing tasks with isolated work directories and completion tracking. Key principles:

- Tasks are worked on in isolation in `spec/todos/work/[task-name]/` directories
- Completion tracking happens in `spec/todos/done/`
- **CRITICAL**: Never mark tasks as complete unless ALL success criteria are verifiably met
- **NEVER COMMIT OR PUSH**: The agent must never run `git commit` or `git push` - only users handle git operations
- Follow the complete Phase 0-4 workflow (Setup → Select → Refine → Implement → Complete)

Critical workflow phases:

1. **Phase 0 (Setup)**: Read `spec/todo.md` and `spec/project-description.md`, handle existing tasks
2. **Phase 1 (Select)**: Present numbered todos, initialize work folder with agent PID
3. **Phase 2 (Refine)**: Define description, success criteria, and implementation plan with user approval
4. **Phase 3 (Implement)**: Execute plan with checkboxes, run checks, validate with user tests
5. **Phase 4 (Complete)**: Verify ALL criteria met before marking complete

Success criteria must include:

- Functional requirements
- Quality checks (lint, typecheck, tests)
- User validation steps
- Documentation updates

### Git Commit Workflow (`commands/commit.md`)

Structured approach for committing staged files:

1. Identify staged files with `git diff --cached --name-only`
2. Commit with one-liner message (60 char max, no semantic prefix, no credit info)
3. Handle pre-commit hook issues by running maintenance commands
4. **NEVER** use `git add .` or bulk staging - only stage originally staged files
5. Leave unstaged files (even if modified by formatters) unstaged

## Architecture Notes

### Directory Structure

- `commands/` - Contains workflow command definitions
  - `todo.md` - Todo implementation system (enhanced version addressing completion verification issues)
  - `commit.md` - Git commit workflow helpers

### Key Patterns

- Workflow isolation using dedicated directories
- Agent PID tracking for concurrent work prevention
- Comprehensive success criteria validation before task completion
- User-controlled git operations (no automated commits/pushes)

## Development Notes

- The todo system addresses issues with Claude Code prematurely marking tasks complete
- Enhanced with more rigorous success criteria and verification steps
- Based on badlogic's Todo Implementation System but with additional safeguards
