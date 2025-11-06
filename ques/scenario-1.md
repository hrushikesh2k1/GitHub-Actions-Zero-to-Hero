**what is the workflow in Github and what are the components?**
A workflow is an automated process defined in your GitHub repository that runs one or more jobs when a certain event happens (like a push, pull request, or schedule).

It’s defined in a YAML file located under:
```
.github/workflows/
```

Example:
```
.github/workflows/ci.yml
```
⚙️ Key Components of a Workflow

A workflow YAML file is made up of several main components:

Component	Description	Example

---
name	  The name of the workflow (appears in GitHub Actions UI)	name: Build and Deploy
---
on	The event that triggers the workflow	on: [push, pull_request]
---
jobs	A group of tasks to run	jobs: build:
---
runs-on	The type of virtual machine to use	runs-on: ubuntu-latest
---
steps	The list of commands or actions to run	steps:
---
uses	Reusable GitHub action (from marketplace)	uses: actions/checkout@v3
---
run	Shell command to execute	run: npm install
---
env	Environment variables for the workflow	env: { NODE_ENV: production }
---
secrets	Secure values (from GitHub Secrets)	${{ secrets.AZURE_CREDENTIALS }}
