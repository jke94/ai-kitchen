# ai-kitchen

An agent templates for software development. From the kitchen to production.

## The agents

### How to use `.github/agents/cpp-pr-code-review-portable.agent.md`

From Visual Studio Code chat:

1. Select `C++ PR Reviewer`.

2. Specify similart message like this:

```
Review PR:
https://github.com/my-org/my-repo/pull/123
```
3. Run!

### How to use `.github/agents/dotnet-framework-pr-reviewer.agent.md`

From Visual Studio Code chat:

1. Select `.NET Framework Enterprise PR Reviewer`.

2. Specify similart message like this:

```
Review PR:
https://github.com/my-org/my-repo/pull/123
```
3. Run!

### How to use `.github/agents/thread-pool-reviewer.agent`

From Visual Studio Code chat:

1. Select `Thread-pool reviewer agent`.

2. Specify similart message like this:

```
Use the thread-pool-reviewer agent.

Review the current branch against main.

Focus on:
- Thread-pool implementation correctness
- Race conditions and data races
- Deadlocks, livelocks, starvation
- Task scheduling and queue management
- Task dependency chains and pool-exhaustion risks
- Future/promise and async callback correctness
- Blocking HTTP/I/O operations inside workers
- Shutdown, cancellation and queue-draining behavior
- Exception handling in worker threads
- Scalability, lock contention and backpressure
- Lifetime, ownership and capture issues

Requirements:
- Include code snippets as evidence.
- Trace the execution path for each finding.
- Explicitly state assumptions and unknowns.
- Flag any task that may wait on another task executed by the same pool.

Provide findings using the format defined in the agent file and conclude with:
- Total findings by severity
- Overall risk assessment
- Go / No-Go recommendation for merging into main
```