# AI IDE Workflow Commands

A structured set of prompt commands for feature development in AI-powered IDEs.

Battle-tested commands that guide you through the full development lifecycle: from capturing issues to post-deployment reflection.

**Works with:** Cursor, Claude Code, Windsurf, VS Code (+ AI extensions), and other AI IDEs.

![License](https://img.shields.io/badge/License-MIT-blue)

---

## Why Use This?

Most AI-assisted coding is ad-hoc. You ask for code, get code, move on. This works for small tasks but falls apart for larger features:

- Requirements get lost
- Design decisions aren't documented
- Code reviews are inconsistent
- Lessons learned vanish

These commands provide **structure without bureaucracy**. Each command is a prompt template that guides the AI (and you) through a specific phase of development.

---

## The Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 1: PLANNING                            │
├─────────────────────────────────────────────────────────────────┤
│  /capture_issue → /explore → /create_plan → /design_decisions   │
│                              ↓                                  │
│                    /pre_implementation_checklist                │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                   PHASE 2: IMPLEMENTATION                       │
├─────────────────────────────────────────────────────────────────┤
│                       /execute_plan                             │
│                            ↓                                    │
│               /tdd (optional, for complex logic)                │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                   PHASE 3: QUALITY ASSURANCE                    │
├─────────────────────────────────────────────────────────────────┤
│            /code_review → /qa_checklist → /peer_review          │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                   PHASE 4: REFLECTION                           │
├─────────────────────────────────────────────────────────────────┤
│                         /postmortem                             │
└─────────────────────────────────────────────────────────────────┘
```

---

## Installation

First, clone this repo:

```bash
git clone https://github.com/Leftyshields/cursor-workflow-commands.git
cd cursor-workflow-commands
```

Then follow the instructions for your IDE:

---

### Cursor IDE

Cursor natively supports slash commands via `.cursor/commands/` directory.

**Per-project installation:**
```bash
# Copy to your project
cp -r commands/ /path/to/your/project/.cursor/commands/

# Create context directory
mkdir -p /path/to/your/project/.ai/context/
```

**Global installation (all projects):**
```bash
cp -r commands/ ~/.cursor/commands/
```

**Usage:** Type `/capture_issue` in the chat panel.

---

### Claude Code (Anthropic CLI)

Claude Code uses `.claude/commands/` for slash commands.

**Per-project installation:**
```bash
# Copy to your project
cp -r commands/ /path/to/your/project/.claude/commands/

# Create context directory
mkdir -p /path/to/your/project/.ai/context/
```

**Global installation:**
```bash
cp -r commands/ ~/.claude/commands/
```

**Usage:** Type `/capture_issue` in Claude Code.

---

### Windsurf (Codeium)

Windsurf uses `.windsurf/commands/` for custom commands.

**Per-project installation:**
```bash
# Copy to your project
cp -r commands/ /path/to/your/project/.windsurf/commands/

# Create context directory
mkdir -p /path/to/your/project/.ai/context/
```

**Global installation:**
```bash
cp -r commands/ ~/.windsurf/commands/
```

**Usage:** Type `/capture_issue` in Windsurf chat.

---

### VS Code (with Continue, Copilot Chat, or other AI extensions)

VS Code AI extensions typically don't have native slash command support, but you can use these commands as **prompt templates**.

**Option A: Manual prompt files**
```bash
# Create a prompts directory in your project
mkdir -p /path/to/your/project/.prompts/
cp -r commands/ /path/to/your/project/.prompts/

# Create context directory
mkdir -p /path/to/your/project/.ai/context/
```

Then copy/paste the prompt content when needed, or reference with `@.prompts/capture_issue.md`.

**Option B: Continue extension (recommended)**

If using [Continue](https://continue.dev/), add commands to your `~/.continue/config.json`:

```json
{
  "slashCommands": [
    {
      "name": "capture_issue",
      "description": "Document the problem",
      "prompt": "... (paste content from capture_issue.md)"
    }
  ]
}
```

Or use the file-based approach:
```bash
cp -r commands/ ~/.continue/commands/
```

**Option C: GitHub Copilot Chat**

For Copilot Chat, use commands as reference files:
1. Open the command file (e.g., `capture_issue.md`)
2. In Copilot Chat, type: `@workspace #file:capture_issue.md Follow these instructions`

---

### Other AI IDEs

Most AI IDEs follow similar patterns. Look for:

- **Commands directory**: `.{ide-name}/commands/` or `~/.{ide-name}/commands/`
- **Custom prompts**: Check IDE documentation for prompt template support
- **Fallback**: Use as reference files and copy/paste when needed

**Common locations:**
| IDE | Commands Directory |
|-----|-------------------|
| Cursor | `.cursor/commands/` |
| Claude Code | `.claude/commands/` |
| Windsurf | `.windsurf/commands/` |
| Zed | `.zed/prompts/` |
| Continue | `~/.continue/commands/` |

---

### Context Directory Setup

All installations should include the context directory for persistence:

```bash
mkdir -p /path/to/your/project/.ai/context/
```

Add to `.gitignore` if you don't want to commit context files:
```bash
echo ".ai/context/" >> .gitignore
```

---

## Commands Reference

### Phase 1: Planning & Design

| Command | Purpose |
|---------|---------|
| `/capture_issue` | Document the problem, current behavior, desired behavior |
| `/explore` | Deep-dive into requirements, constraints, risks |
| `/create_plan` | Generate atomic execution steps |
| `/design_decisions` | Document design choices before coding |
| `/pre_implementation_checklist` | Verify readiness before implementation |

### Phase 2: Implementation

| Command | Purpose |
|---------|---------|
| `/execute_plan` | Follow the plan step-by-step |
| `/tdd` | Test-driven development (Red-Green-Refactor cycle) |

### Phase 3: Quality Assurance

| Command | Purpose |
|---------|---------|
| `/code_review` | Automated security and quality review |
| `/qa_checklist` | Generate manual testing checklist |
| `/peer_review` | Structured human code review |

### Phase 4: Reflection

| Command | Purpose |
|---------|---------|
| `/postmortem` | Analyze friction, document lessons learned |
| `/learning_opportunity` | Capture insights anytime |

### Utility

| Command | Purpose |
|---------|---------|
| `/show_context` | Display current context files |
| `/workflow` | Show the complete workflow |

---

## Context Persistence

Commands persist context to `.ai/context/` for continuity across sessions:

```
your-project/
├── .cursor/              # Cursor IDE
│   └── commands/
├── .claude/              # Claude Code
│   └── commands/
├── .windsurf/            # Windsurf
│   └── commands/
├── .ai/
│   └── context/          # ← Context persists here (shared across IDEs)
│       ├── last_capture.md
│       ├── last_explore.md
│       ├── execution_plan.md
│       └── design_decisions.md
└── src/
```

**Why this matters:**
- `/explore` can reference what `/capture_issue` documented
- `/execute_plan` knows what `/create_plan` decided
- `/postmortem` can analyze the full journey
- Context works across IDE switches (same `.ai/context/` directory)

---

## Quick Start Examples

### New Feature (Full Workflow)

```
/capture_issue    # "Add user authentication"
/explore          # Analyze requirements, identify OAuth vs password
/create_plan      # Generate implementation steps
/design_decisions # Document JWT vs session choice
/execute_plan     # Build it step by step
/code_review      # Automated security check
/qa_checklist     # Manual testing guide
/postmortem       # What did we learn?
```

### Bug Fix (Quick Workflow)

```
/capture_issue    # Document the bug
/execute_plan     # Fix it
/code_review      # Review the fix
```

### Complex Logic (TDD)

```
/execute_plan     # Start implementation
/tdd              # Switch to TDD for the algorithm
# ... Red-Green-Refactor cycles ...
/code_review      # Review when done
```

---

## Customization

These are markdown files. Edit them to fit your workflow:

- **Add project-specific patterns**: Your tech stack, conventions
- **Modify checklists**: Add/remove items in `/code_review`
- **Change context paths**: Use different directories
- **Add new commands**: Copy an existing one as a template

### Example: Adding a `/deploy` command

Create `commands/deploy.md` in your IDE's commands directory:

```markdown
# Deployment Checklist

Before deploying, verify:
- [ ] All tests pass
- [ ] /code_review completed
- [ ] Version bumped
- [ ] Changelog updated

Deployment steps:
1. Run `npm run build`
2. Run `npm run deploy`
3. Verify production health check
4. Monitor for errors (15 min)
```

---

## Philosophy

1. **Structure, not bureaucracy** - Commands guide but don't constrain
2. **Context is king** - Persist decisions so nothing gets lost
3. **AI as partner** - Let AI handle the checklist, you make decisions
4. **Learn from friction** - Postmortems improve the process itself

---

## Contributing

Contributions welcome! Ideas:

- Language/framework-specific command variants
- Additional workflow commands
- Improved prompts
- Documentation

---

## License

MIT - Use freely, modify as needed, contribute back if you can.

---

## Acknowledgments

Inspired by [Zevi Arnovitz's appearance on Lenny's Podcast](https://www.youtube.com/watch?v=1em64iUFt3U), where he discussed structured approaches to AI-assisted development. His insights on treating AI as a collaborative partner with clear processes shaped this workflow.

Also inspired by:
- Structured development practices (TDD, code review checklists)
- The realization that AI coding assistants work dramatically better with clear context and processes
- [everything-claude-code](https://github.com/affaan-m/everything-claude-code) for command patterns
