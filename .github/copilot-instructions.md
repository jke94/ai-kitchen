# Copilot instructions — ai-kitchen (minimal)

Purpose: Agent templates for PR review helpers located in .github/agents/.

Key points:
- Check each agent's header (`Execution Prerequisites`, `Required Input Contract`) before running.
- Base any review or suggestion only on repository evidence (diffs, files, tests).
- Do not assume the current repository is the PR target; use `gh` or PR metadata.
- Respect LICENSE (MIT) and avoid introducing conflicting dependencies.

Included agents (examples):
- C++ PR Reviewer
- .NET Framework PR Reviewer

See README.md and the files under .github/agents/ for full details.
