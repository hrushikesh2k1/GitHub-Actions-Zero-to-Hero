***“Your GitHub Actions workflow performance has decreased — jobs are running slower than before.
What measures would you take to improve performance?” ***

Step 1: Identify the Root Cause

First, you show analytical thinking — don’t jump to fixes.

You’d say:

“Before making changes, I’ll analyze where exactly the slowdown is happening — is it in build, testing, deployment, or due to queue time?”

Actions:

Check GitHub Actions Insights → Workflow Duration Trend

Identify if all workflows are slow or only one.

Note if the slowdown began after a specific commit or dependency change.

Review Logs

Check which step or job consistently takes longer.

Compare timestamps between runs.

Check Runner Queue Time

If jobs are waiting for runners, it could mean limited concurrency or runner exhaustion.

Check Resource Utilization

---

1. Use Dependency Caching

“Dependencies like npm install, pip install, or Maven downloads often take time.
Caching them saves several minutes per build.”

---

2. Use Matrix Builds or Parallel Jobs

“If we’re running tests for multiple environments or microservices,
I’d split them into parallel jobs using matrix strategy.”

---

3. Use Self-Hosted Runners

“If jobs are waiting in queue or require high CPU/memory (for example, builds or Terraform plans),
I’d set up self-hosted runners in Azure.”

---



GitHub-hosted runners have limited CPU/memory (e.g., 2-core, 7GB).

Heavy builds or tests can cause delays.
