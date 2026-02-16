# Epiphoric Development Workflow

This document outlines the recommended workflow for implementing features in Epiphoric.

---

## 🔄 Complete Feature Development Workflow

### Phase 1: Planning & Design

1. **Capture the Issue** (`/capture_issue`)
   - Document the problem, current behavior, desired behavior
   - Assign issue ID and priority
   
   **Next:** Run `/explore` to analyze requirements

2. **Explore Requirements** (`/explore`)
   - Analyze the problem in detail
   - Define success criteria
   - Identify constraints and risks
   - List open questions
   
   **Next:** Run `/create_plan` to create execution plan

3. **Create Execution Plan** (`/create_plan`)
   - Generate detailed implementation plan
   - Include field mappings (if data transformations)
   - Include format conversions (if needed)
   - Include local dev parity checks (if API endpoints)
   
   **Next:** Run `/design_decisions` to document design choices

4. **Document Design Decisions** (`/design_decisions`)
   - Answer all open questions from planning
   - Define field update strategies
   - Specify rendering approaches (if formatted content)
   - Document integration points
   
   **Next:** Run `/pre_implementation_checklist` to verify readiness

5. **Pre-Implementation Checklist** (`/pre_implementation_checklist`)
   - Verify design decisions exist
   - Verify field mappings are documented
   - Verify format conversions are specified
   - Verify local dev parity plan (if needed)
   - Verify rendering strategy (if needed)
   
   **Next:** Run `/execute_plan` to begin implementation

---

### Phase 2: Implementation

6. **Execute Plan** (`/execute_plan`)
   - Follow the execution plan step-by-step
   - Reference design decisions for guidance
   - Update both `functions/index.js` AND `server.js` for new endpoints
   - Use functional state updates when updating state based on props/state
   - Implement format conversions as documented
   
   **Optional:** Run `/tdd` for complex logic (test-driven development)
   
   **Next:** Run `/code_review` for automated review, then `/qa_checklist` for manual testing

---

### Phase 3: Quality Assurance

7. **Code Review** (`/code_review`) — *standard*
   - Automated security check, correctness, architecture, code quality, performance
   - Review specified scope (file, recent changes, or feature)
   
   **Next:** Fix any issues found, then run `/security_scan` (optional) or `/qa_checklist`

8. **Security Scan** (`/security_scan`) — *optional*
   - Dedicated pass: secrets, dependencies, input safety, auth, data at rest, encryption, proprietary/IP
   - Use when handling sensitive data, before release, or for compliance; complements code_review
   
   **Next:** Fix critical/high findings, then run `/qa_checklist`

9. **QA Checklist** (`/qa_checklist`) — *standard*
   - Manual testing checklist: happy path, edge cases, error handling, visual/UX
   - Human validation only (no automated tests)
   
   **Next:** Fix any issues found, then run `/peer_review` (optional)

10. **Peer Review** (`/peer_review`) — *optional*
   - Human code review for complex or high-impact changes
   - Evaluate suggestions critically; accept or reject with rationale
   
   **Next:** Address review feedback, then proceed to deployment

---

### Phase 4: Deployment & Reflection

11. **Deploy**
    - Test in staging (if available)
    - Deploy to production
    - Monitor for issues
   
    **Next:** Run `/postmortem` to reflect on the process

12. **Postmortem** (`/postmortem`) — *standard*
    - Analyze friction points, rework, missing docs
    - Document lessons learned; propose workflow/doc updates
    
    **Next:** Run `/project_wrap_up` (optional) or start next feature

13. **Project Wrap-up** (`/project_wrap_up`) — *optional*
    - Final handover: security audit, context synthesis, onboarding docs, next-op briefing
    - Use when handing off, releasing, or preparing for the next contributor or AI agent
    
    **Next:** Start next feature or hand off

---

## 🚀 Quick Start Workflow

For smaller changes or bug fixes:

1. `/capture_issue` - Document the issue
2. `/execute_plan` - Implement the fix
3. `/code_review` - Automated review
4. `/security_scan` - Optional, if the change touches auth, secrets, or sensitive data
5. `/peer_review` - Review changes (optional for trivial fixes)
6. Deploy

---

## 📋 Standard vs optional steps

| Step | Type | What it does |
|------|------|----------------|
| `/capture_issue` | Standard | Log the problem, current/desired behavior, priority; get issue ID |
| `/explore` | Standard | Deep-dive requirements, constraints, risks; persist exploration snapshot |
| `/create_plan` | Standard | Turn exploration into atomic implementation steps |
| `/design_decisions` | Standard | Lock design choices, field mappings, integration points before coding |
| `/pre_implementation_checklist` | Standard | Confirm plan and design are complete; gate before coding |
| `/execute_plan` | Standard | Implement step-by-step using plan and design decisions |
| `/tdd` | Optional | Red–green–refactor for complex logic during implementation |
| `/code_review` | Standard | Automated review: security, correctness, architecture, quality, performance |
| `/security_scan` | Optional | Dedicated security pass: secrets, deps, auth, data at rest, encryption, proprietary/IP |
| `/qa_checklist` | Standard | Human manual-test checklist (happy path, edge cases, UX) |
| `/peer_review` | Optional | Human review of changes; accept/reject feedback with rationale |
| `/postmortem` | Standard | Reflect on friction and rework; improve process and docs |
| `/project_wrap_up` | Optional | Handover: security audit, onboarding docs, next-op briefing |
| `/learning_opportunity` | Optional | Capture insights anytime |
| `/show_context` | Utility | Show current context files |
| `/workflow` | Utility | Show this workflow |

**Standard** = recommended for every feature or bugfix. **Optional** = use when scope, risk, or handover justifies it.

---

## ⚠️ Common Mistakes to Avoid

1. **Skipping Design Decisions** - Always run `/design_decisions` before implementation
2. **Forgetting Local Dev Parity** - Always update both `functions/index.js` and `server.js`
3. **Stale Closures** - Use functional state updates when updating state based on props/state
4. **Missing Format Conversions** - Document and implement all format conversions
5. **Skipping Pre-Implementation Checklist** - Verify all requirements before coding

---

## 📚 Related Documentation

- [Data Format Reference](docs/DATA_FORMAT_REFERENCE.md) - Data structure specs
- [React Patterns](docs/REACT_PATTERNS.md) - React best practices
- [API Endpoints](docs/API_ENDPOINTS.md) - Backend API docs
- [Setup Guide](docs/SETUP.md) - Development setup

---

**Last Updated:** 2025-02-04
