Create a manual QA checklist for this feature.

Include:
- Happy path
- Common edge cases
- Failure states
- Visual / UX checks

Format as a simple checklist that a human can follow.

Do not write automated tests here.
This is for human validation only.

---

**Workflow Position:** Run this after `/code_review` (automated review).

**Previous Step:** `/code_review` - Automated security and quality review

**Next Steps:**
1. Fix any issues found during QA
2. Run `/peer_review` for human code review (for complex changes)
3. Address review feedback
4. Deploy the feature

See `.cursor/commands/workflow.md` for the complete development workflow.
