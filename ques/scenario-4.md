**Is it possible to send the data between steps in job. if yes, how?**

Yes, it’s absolutely possible to send or share data between steps in the same job in GitHub Actions.
Since all steps in a job run on the same runner (VM), they share the same environment — so you can use several ways to pass data.

🪶 1️⃣ Using Environment Variables (Easiest way)

If you define a variable using the env: keyword or echo it to the special $GITHUB_ENV file, it becomes available in subsequent steps in the same job.
```
jobs:
  share-data:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Create a variable
        run: |
          echo "VERSION=1.0.3" >> $GITHUB_ENV

      - name: Step 2 - Use the variable
        run: |
          echo "Deploying version $VERSION"
```
How it works:

$GITHUB_ENV is a special file used by GitHub Actions.

When you append VAR=value to it, it becomes an environment variable for later steps.

---

2.Using Step Outputs (Structured & Recommended for CI/CD)

When you want to pass specific data (like build IDs, artifact names, tags, etc.), you can use outputs.

Each step can define outputs using the ::set-output syntax (deprecated) or by writing to $GITHUB_OUTPUT (new method).

```
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Generate build ID
        id: buildinfo
        run: |
          echo "build_id=12345" >> $GITHUB_OUTPUT

      - name: Step 2 - Use the build ID
        run: |
          echo "Build ID is: ${{ steps.buildinfo.outputs.build_id }}"
```

Explanation:

The first step has an id: buildinfo.

It writes output key/value (build_id=12345) to $GITHUB_OUTPUT.

Later steps can use it as ${{ steps.buildinfo.outputs.build_id }}.

---

