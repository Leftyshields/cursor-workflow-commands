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

7. **Code Review** (`/code_review`)
   - Automated security check
   - Correctness verification
   - Architecture review
   - Code quality scan
   - Performance check
   
   **Next:** Fix any issues found, then run `/qa_checklist`

8. **QA Checklist** (`/qa_checklist`)
   - Manual testing checklist
   - Happy path scenarios
   - Edge cases
   - Error handling
   - Visual/UX checks
   
   **Next:** Fix any issues found, then run `/peer_review`

9. **Peer Review** (`/peer_review`)
   - Human code review (for complex changes)
   - Evaluate suggestions critically
   - Accept or reject with rationale
   
   **Next:** Address review feedback, then proceed to deployment

---

### Phase 4: Deployment & Reflection

10. **Deploy**
    - Test in staging (if available)
    - Deploy to production
    - Monitor for issues
   
    **Next:** Run `/postmortem` to reflect on the process

11. **Postmortem** (`/postmortem`)
    - Analyze friction points
    - Identify rework
    - Document lessons learned
    - Update workflows and documentation
    
    **Next:** Start next feature with improved process

---

## 🚀 Quick Start Workflow

For smaller changes or bug fixes:

1. `/capture_issue` - Document the issue
2. `/execute_plan` - Implement the fix
3. `/peer_review` - Review changes
4. Deploy

---

## 📋 Command Reference

| Command | Purpose | When to Run |
|---------|---------|-------------|
| `/capture_issue` | Document the problem | Start of new feature |
| `/explore` | Analyze requirements | After capturing issue |
| `/create_plan` | Create execution plan | After exploration |
| `/design_decisions` | Document design choices | After planning, before implementation |
| `/pre_implementation_checklist` | Verify readiness | Before starting implementation |
| `/execute_plan` | Implement feature | After checklist complete |
| `/tdd` | Test-driven development | During implementation (complex logic) |
| `/code_review` | Automated code review | After implementation, before QA |
| `/qa_checklist` | Manual testing guide | After code review |
| `/peer_review` | Human code review | After QA (complex changes) |
| `/postmortem` | Process reflection | After deployment |
| `/learning_opportunity` | Document learning | Anytime insights occur |

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

**Last Updated:** 2026-01-19
