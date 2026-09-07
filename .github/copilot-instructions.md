# Copilot instructions — ai-kitchen

Purpose: Agent templates for branch comparison, architecture analysis, and PR review helpers located in `.github/agents/`.

Key points:
- Check each agent's header (`Execution Prerequisites`, `Required Input Contract`) before running.
- Base any review or suggestion only on repository evidence (diffs, files, tests).
- Do not assume the current repository is the PR target; use `gh` or PR metadata.
- Respect LICENSE (MIT) and avoid introducing conflicting dependencies.

## Agents

### [Comparator and descriptor of changes between branches](.github/agents/comparator-and-descriptor-of-changes-between-branches.agent.md)

- Enumerates logical changes introduced by one branch compared with a base branch, defaulting to `main`.
- Accepts one branch, or a branch and an explicit base branch.
- Uses Git metadata and diffs, groups related modifications, and reports observable outcomes in English.
- Produces a concise summary and one to ten prioritized change items; reports `No changes relative to the base branch.` when appropriate.
- Can create `branch-changes.md` when the user requests a report file.

### [C++ PR Reviewer](.github/agents/cpp-pr-code-review-portable.agent.md)

- Performs evidence-based reviews of C++ Pull Requests, with emphasis on correctness, memory safety, concurrency, performance, architecture, security, and testing.
- Requires a uniquely identified Pull Request supplied as a full URL, `owner/repository#PR_NUMBER`, or repository plus PR number.
- Requires an installed and authenticated GitHub CLI (`gh`) and treats GitHub PR metadata as authoritative.
- Reviews the target repository fetched from the Pull Request rather than assuming the current repository is the target.
- Classifies findings as confirmed issues, plausible risks, or questions, with evidence and confidence.

### [.NET Framework Enterprise PR Reviewer](.github/agents/dotnet-framework-pr-reviewer.agent.md)

- Performs principal-level reviews of .NET Framework Pull Requests covering C#, ASP.NET, WCF, Windows Services, Entity Framework 6, ADO.NET, SQL Server, IIS, security, performance, and deployment.
- Requires a uniquely identified Pull Request supplied as a full URL, `owner/repository#PR_NUMBER`, or repository plus PR number.
- Uses GitHub CLI metadata and explicitly fetches the target repository and branches; it must not infer the target from the current directory.
- Evaluates business behavior, architecture, correctness, web security, database access, async/concurrency, resource management, performance, and configuration.
- Classifies findings as confirmed issues, plausible risks, or questions and includes severity, confidence, evidence, impact, and a suggested fix.

### [Senior Project Analyzer](.github/agents/senior-project-analyzer.agent.md)

- Analyzes existing C/C++ projects as a senior architect and code reviewer before proposing changes.
- Inspects project structure, build context, compilation settings, modules, dependencies, APIs, architecture, ownership, maintainability, and technical debt.
- Requires evidence-based conclusions, distinguishes facts from observations, problems, and recommendations, and explicitly states uncertainty.
- Records strengths as well as risks, including boundaries, cohesion, coupling, RAII, lifetime, error handling, and testability.
- Does not modify source code unless the user explicitly requests it.

### [Thread-pool reviewer agent](.github/agents/thread-pool-reviewer.agent.md)

- Reviews the current branch against `main` for a C++ migration from one thread per instance to a fixed-size thread pool.
- Focuses on races, lifetime and synchronization issues, deadlocks, starvation, queue behavior, backpressure, blocking I/O, scalability, and task dependencies.
- Verifies shutdown invariants including task acceptance, queue draining, cancellation, worker joins, and object lifetime.
- Also checks exception handling, worker recovery, lost tasks, observability, and operational behavior under sustained load.
- Reports prioritized findings with severity, evidence, execution-path reasoning, risk, and concrete recommendations, followed by a merge recommendation.

### [VS Code Agent: Git Branch Review Expert (C++)](.github/agents/vscode-git-branch-review-cpp.agent.md)

- Compares a proposed branch with the repository's default branch (`main` or `master`) before integration.
- Requires Git-based evidence from the merge-base diff, branch commits, changed-file summary, rename detection, and relevant submodule or binary changes.
- Reviews only changes introduced by the proposed branch, prioritizing ownership and lifetime, concurrency, architecture, ABI/API compatibility, tests, correctness, and performance.
- Requires every finding to include the affected file, change reference, technical explanation, impact, recommendation, and severity.
- Reports ABI/API impact, test and regression risk, relevant architectural risks, positive aspects, and an integration risk score from 0 to 100.
- Produces a concise review with findings ordered by severity and recommends `APPROVE`, `APPROVE WITH COMMENTS`, or `CHANGES REQUIRED`.

See README.md and the files under .github/agents/ for full details.
