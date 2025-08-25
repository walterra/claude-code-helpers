# Create curriculum based on current branch

Analyse the code and docs created/modified in the current branch.

Create a comprehensive onboarding guide for a new developer to learn about the code of this branch. Use your todo tools to manage progress.

## User Questions

Before creating the curriculum, ask the user:

- What is the target audience? (Junior developer, experienced developer new to the codebase, reference for someone who knows the codebase well, specific role like frontend/backend/devops)
- What should be the primary focus? (Architecture overview, specific features, testing practices, deployment, etc.)
- What level of detail is needed? (High-level overview, deep technical dive, or balanced approach)
- Are there specific technologies or concepts you want emphasized?
- What format would work best? (Step-by-step tutorial, reference guide, interactive workshop, or mixed approach)
- How much time should the curriculum take to complete? (Hours, days, weeks)

## Detailed Instructions

### 1. Read the Code

- Analyze all files changed/added in the current branch
- Use `git diff main...HEAD` to see changes since branching from main
- Review each modified file to understand functionality and purpose
- Identify key components, modules, and their relationships

### 2. Identify Tech Topics

- Extract technical concepts, frameworks, and libraries used
- Note architectural patterns and design principles
- Identify APIs, data structures, and key algorithms
- Document dependencies and external integrations
- List testing approaches and development practices

### 3. Create Table of Contents

- Organize topics from basic to advanced concepts
- Structure learning path logically (dependencies first)
- Group related concepts together
- Include practical examples
- Add estimated learning time for each section

### 4. Create Documentation for Each ToC Item

- Write clear explanations for each technical concept
- Include code examples from the actual codebase
- Provide context on why each technology/pattern was chosen
- Add troubleshooting tips and common gotchas
- Link to external resources for deeper learning
- Include hands-on exercises to reinforce learning

## File Structure

The curriculum should be organized as markdown documents in `./llm-docs/<slug>/` with the following structure:

- **Directory Structure**: Create a directory under `./llm-docs/` using a descriptive slug (e.g., `./llm-docs/feature-authentication/` or `./llm-docs/api-refactor/`)

- **Introduction and Table of Contents**: Create a single `00-introduction.md` file that includes:

  - Overview of the curriculum
  - Learning objectives
  - Prerequisites
  - Complete table of contents with links to chapters
  - Estimated completion time

- **Individual Chapters**: Each chapter should be its own markdown document:

  - Use numbered prefixes for logical ordering (e.g., `01-overview.md`, `02-setup.md`)
  - Each file should focus on a single major topic or concept
  - Include clear headings and subheadings for easy navigation
  - Cross-reference other chapters when relevant using relative links

- **Naming Convention**: Use descriptive, kebab-case filenames that reflect the chapter content:
  - `00-introduction.md` - Introduction and table of contents
  - `01-architecture-overview.md` - High-level system architecture
  - `02-development-setup.md` - Local development environment
  - `03-core-concepts.md` - Fundamental concepts and patterns
  - And so on...

**Example structure:**

```
./llm-docs/user-authentication/
├── 00-introduction.md
├── 01-architecture-overview.md
├── 02-setup-and-dependencies.md
├── 03-core-authentication-flow.md
└── 04-testing-and-deployment.md
```

This modular approach allows for:

- Easy maintenance and updates
- Flexible learning paths
- Better organization for different skill levels
- Reusable content across different audiences
