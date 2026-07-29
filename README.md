# Project Name

<!-- TODO: Replace with your project description -->

## Agentic Development Workflow

This project uses [GitHub Agentic Workflows (gh-aw)](https://github.github.com/gh-aw/) for automated development with Claude-powered agents.

```mermaid
flowchart TD
    A["Feature Idea<br/>(GitHub Issue)"] -->|"issue labeled<br/>feature-idea"| B["PRD Generation<br/>Agent writes PRD"]
    B -->|"opens PR with PRD"| C{"PRD Review<br/>& Merge"}
    C -->|"PRD merged<br/>to main"| D["Decomposition<br/>Breaks PRD into stories"]
    C -->|"PRD merged<br/>to main"| E["Skill Selection<br/>Fetches coding skills"]
    C -->|"PRD merged<br/>to main"| F["MCP Selection<br/>Configures data sources"]
    D -->|"creates issues<br/>with labels"| G["Implementation Backlog<br/>(GitHub Issues)"]
    E -->|"opens PR adding<br/>skills to .claude/"| H{"Skill & MCP<br/>PR Review"}
    F -->|"opens PR configuring<br/>mcp-servers in workflow"| H
    G -->|"issue labeled<br/>ready-for-implementation"| I["AI Implementation<br/>Agent writes code"]
    H -->|merge| I
    I -->|"opens PR<br/>with code changes"| J{"Code Review"}
    J -->|"PR labeled<br/>needs-validation"| K["Validation<br/>Tests against criteria"]
    K -->|"comments pass/fail<br/>on PR"| J
    J -->|merge| L["Done"]

    style A fill:#4a90d9,color:#fff
    style B fill:#6c5ce7,color:#fff
    style C fill:#fdcb6e,color:#333
    style D fill:#6c5ce7,color:#fff
    style E fill:#6c5ce7,color:#fff
    style F fill:#6c5ce7,color:#fff
    style G fill:#00b894,color:#fff
    style H fill:#fdcb6e,color:#333
    style I fill:#6c5ce7,color:#fff
    style J fill:#fdcb6e,color:#333
    style K fill:#6c5ce7,color:#fff
    style L fill:#00b894,color:#fff
```

### Quick Start

1. Customize `CLAUDE.md` with your project's architecture and conventions
2. Customize `.github/workflows/implementation.md` with your project's paths and commands
3. Compile workflows: `gh aw compile`
4. Create the `feature-idea` label: `gh label create feature-idea --color 0E8A16`
5. Create a feature idea issue and label it `feature-idea`

### Workflow Commands

```bash
gh aw list                  # List all workflows
gh aw run prd-generation    # Generate PRD from a feature idea issue
gh aw run decomposition     # Decompose a PRD into stories
gh aw run skill-selection   # Fetch coding skills for a PRD
gh aw run mcp-selection     # Configure MCP servers for implementation
gh aw run implementation    # Implement a story
gh aw run validation        # Validate an implementation PR
gh aw compile               # Recompile .lock.yml files after editing workflows
```

### Syncing Shared Workflows

Shared workflows are automatically synced weekly from [gh-aw-shared-workflows](https://github.com/RealPage/gh-aw-shared-workflows). To sync manually:

```bash
./scripts/sync-workflows.sh
gh aw compile
```
