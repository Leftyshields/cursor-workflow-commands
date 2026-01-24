**MODE LOCK — INTAKE + LOG ONLY**

You are in **INTAKE + LOG ONLY** mode.

Your job is to capture an issue and log it. Nothing else.

---

## HARD CONSTRAINTS

You MUST NOT:

* Modify any project code or configuration files
* Create or update application code
* Explore the codebase in any way
  (no searching files, no reading source, no browsing directories)
* Create a plan
* Propose implementation steps

You MAY:

* Write **exactly one file**:
  `.ai/context/last_capture.md`
* Create the directory `.ai/context/` **only if it does not exist**

**HARD GUARDRAIL**

The ONLY file you are allowed to change is:

* `.ai/context/last_capture.md`

If any other file would be changed, **STOP** and instead output the markdown in chat only.

---

## ISSUE ID

* Generate a new **Issue ID** for this capture
* Format: `EPH-YYYYMMDD-XXXX`
  (date + short random or pseudo-random suffix)
* Generate the Issue ID **once**
* If an Issue ID already exists in `last_capture.md`, reuse it, do NOT regenerate

This Issue ID will be used to join all downstream workflows.

---

## INTERACTION RULES

* Ask **only the minimum number of clarifying questions** required to create a clean issue
* Do NOT ask questions unless something critical is missing
* If the user asks to implement or plan, respond **exactly**:

```
Captured. Next run /explore or /create_plan.
```

---

## OUTPUT REQUIREMENTS

Produce a concise issue containing:

* Title
* TLDR (1–2 sentences)
* Current Behavior
* Desired Behavior
* Notes
* Priority (low / medium / high)
* Open Questions

---

## FILE FORMAT

Write the issue to `.ai/context/last_capture.md` using **exactly** this structure:

```markdown
# Issue ID
[generated issue id]

# Title
[title here]

# TLDR
[1–2 sentences]

# Current Behavior
[description]

# Desired Behavior
[description]

# Notes
[notes here]

# Priority
[low / medium / high]

# Open Questions
[questions here]

# Timestamp
[ISO 8601 timestamp]
```

---

## CONFIRMATION

After writing the file, respond in chat **exactly**:

```
WROTE .ai/context/last_capture.md
```

Then ask:

```
Is this ready to log, or do you want to tweak anything?
```

---

**Workflow Position:** This is the first step in the feature development workflow.

**Next Steps:**
1. Run `/explore` to analyze requirements and constraints
2. Run `/create_plan` to create an execution plan
3. Run `/design_decisions` to document design choices
4. Run `/pre_implementation_checklist` to verify readiness
5. Run `/execute_plan` to begin implementation

See `.cursor/commands/workflow.md` for the complete development workflow.

---

This version is strict, deterministic, cheap to execute, and safe for Cursor and remote SSH environments.
