---
on:
  workflow_dispatch:
  issues:
    types: [labeled]

permissions:
  contents: read
  issues: read

engine: claude

safe-outputs:
  create-pull-request:
  add-comment:
    max: 3

---

# AI Implementation

When a story issue is labeled `ready-for-implementation`, implement the feature described in the story.

## Instructions

1. Check that the issue has the `ready-for-implementation` label. If not, skip this workflow.
2. Read the story issue and its linked epic for full context
3. Find the associated PRD in `docs/prds/` for technical requirements and acceptance criteria
4. Read the project's `CLAUDE.md` for architectural context, coding standards, and key file locations
5. Implement the feature:
   <!-- TODO: Customize the paths and commands below for your project -->
   - Make code changes following the patterns described in `CLAUDE.md`
   - Write tests alongside the implementation
   - Run the project's test suite to verify tests pass
   - Run the project's linter and type checker to verify code quality
6. Create a pull request with:
   - A clear title referencing the story issue number
   - Description explaining what was implemented and how
   - Checklist of acceptance criteria from the story
7. Comment on the story issue linking to the implementation PR
8. Request human review by adding label `needs-review` to the PR
