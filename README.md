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
- Blocking HTTP/I/O operations inside workers
- Shutdown and cancellation behavior
- Exception handling in worker threads
- Scalability and lock contention
- Backpressure and queue growth risks
- Lifetime and ownership issues

Provide findings using the format defined in the agent file and conclude with a Go/No-Go recommendation for merging into main.
```