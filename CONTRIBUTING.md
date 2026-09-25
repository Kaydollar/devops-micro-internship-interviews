# Contributing Guide

Thanks for helping build this community resource! Every improvement helps future learners.
**Goal:** high-quality, searchable interview Q&A—organized by week—with consistent metadata.

---

## Contents

1. [Prerequisites](#prerequisites)
2. [First-Time Setup (once)](#first-time-setup-once)  
    • Step 1 — Fork & Authenticate  
    • Step 2 — Clone Your Fork Locally  
    • Step 3 — Install deps & Pre-commit Hook  
3. [Your First PR (end-to-end)](#your-first-pr-end-to-end)
4. [Every PR: Quick Checklist](#every-pr-quick-checklist)
5. [Keeping Your Fork in Sync](#keeping-your-fork-in-sync)
6. [Answer Structure & Frontmatter](#answer-structure--frontmatter)
7. [Commit & PR Conventions](#commit--pr-conventions)
8. [Reviews, Governance & FAQ](#reviews-governance--faq)

---

## Prerequisites

* Git (with **SSH** or HTTPS set up)
* **Python 3.11+**
* Bash (Git Bash on Windows is fine)

> Why: Contributors run two scripts locally to validate metadata and rebuild the index.

> Don’t edit .github/** or scripts/**.
> If you need something changed there, open an issue or propose the change under meta/proposals/ and maintainers will 
> apply it.

---

## First-Time Setup (once)

### Step 1 — Fork & Authenticate

1. **Fork** the repo:
   [https://github.com/pravinmishraaws/devops-micro-internship-interviews](https://github.com/pravinmishraaws/devops-micro-internship-interviews.git)

2. **Authenticate Git**
   **SSH (recommended):**

   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

   Add `~/.ssh/id_ed25519.pub` to GitHub → **Settings → SSH and GPG keys**.

   Force SSH for GitHub (avoids HTTPS prompts):

   ```bash
   git config --global url."git@github.com:".insteadOf "https://github.com/"
   ```

   **HTTPS (alternative):**

   ```bash
   git config --global credential.helper cache
   ```

3. **Test**:

   ```bash
   ssh -T git@github.com
   ```

   Expected: greeting from GitHub.

---

### Step 2 — Clone Your Fork Locally

```bash
git clone git@github.com:yourusername/devops-micro-internship-interviews.git
cd devops-micro-internship-interviews
git remote -v
```

Add the original repo as `upstream`:

```bash
git remote add upstream https://github.com/pravinmishraaws/devops-micro-internship-interviews.git

# Now, check remote again
git remote -v
```

> Why: You’ll pull updates from `upstream` and push your work to `origin` (your fork).

---

### Step 3 — Install Deps & Pre-commit Hook

Create a virtualenv and install deps:

**macOS / Linux**

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r scripts/requirements.txt
```

**Windows (PowerShell)**

```powershell
py -m venv .venv
. .\.venv\Scripts\Activate.ps1
pip install -r scripts\requirements.txt
```

#### (Recommended) One-shot setup script

[Mac, Linux user ] Create `scripts/setup.sh` (commit this file to repo) and include the pre-commit hook installer:

```bash
#!/usr/bin/env bash
set -euo pipefail

# Create venv if missing
if [ ! -d ".venv" ]; then
  python -m venv .venv
fi

# Activate venv (POSIX shells)
# shellcheck source=/dev/null
source .venv/bin/activate || true

# Fallback for Git Bash on Windows
if [ ! -n "${VIRTUAL_ENV-}" ] && [ -f ".venv/Scripts/activate" ]; then
  # shellcheck disable=SC1091
  . .venv/Scripts/activate
fi

pip install -r scripts/requirements.txt

# Install pre-commit hook
HOOK_PATH=".git/hooks/pre-commit"
echo "Setting up pre-commit hook..."
cat > "$HOOK_PATH" <<'EOF'
#!/bin/bash
echo "🧹 Running pre-commit validation..."
python scripts/validate_frontmatter.py || exit 1
python scripts/build_index.py || exit 1
echo "✅ Validation passed!"
EOF
chmod +x "$HOOK_PATH"
echo "✅ Pre-commit hook installed successfully!"
```

[ Windows User ] helper (scripts/setup.ps1) for PowerShell users:

```bash
$ErrorActionPreference = "Stop"

if (-not (Test-Path ".venv")) {
  py -m venv .venv
}

. .\.venv\Scripts\Activate.ps1
pip install -r scripts\requirements.txt

$hookPath = ".git/hooks/pre-commit"
@"
#!/bin/bash
echo "🧹 Running pre-commit validation..."
python scripts/validate_frontmatter.py || exit 1
python scripts/build_index.py || exit 1
echo "✅ Validation passed!"
"@ | Out-File -FilePath $hookPath -Encoding ascii -NoNewline
bash -lc "chmod +x $hookPath"
Write-Host "✅ Pre-commit hook installed successfully!"
```

Run it once:

```bash
bash scripts/setup.sh
```

> Now **every commit** will auto-run:
> `python scripts/validate_frontmatter.py` and `python scripts/build_index.py` and block bad commits.

---

## Your First PR (end-to-end)

1. **Sync main (fast-forward only)**

```bash
git fetch upstream
git checkout main
git pull --ff-only upstream main
```

2. **Create a feature branch**

```bash
git checkout -b add-kebab-title
```

3. **Add your question**

* Path: `<topic>/questions/`
* File: `##-kebab-title.md` — use the next sequential number in that topic (check how many files exist)
* Include frontmatter and sections (see below)

4. **Run validators manually (optional)**

```bash
python _internal/scripts/validate_frontmatter.py && python _internal/scripts/build_index.py
```

5. **Commit** (pre-commit will auto-validate)

```bash
git add <topic>/questions/##-kebab-title.md
git commit -m "question(06-terraform/07): add how to structure modules"
```

6. **Push & open PR**

```bash
git push -u origin add-kebab-title
```

On GitHub → **Compare & pull request**.
Base: `pravinmishraaws/main` • Compare: `yourusername/add-kebab-title`

7. **Fill PR description**

* What you added, which week, validation passed, any notes

---

## Every PR: Quick Checklist

* [ ] **One question per file** → `<topic>/questions/##-kebab-title.md` (next sequential number in that topic)
* [ ] **Frontmatter** includes: `id, title, difficulty, week, topics, tags, author, reviewed`
* [ ] **Structure**: Short Answer → Deep Dive → Pitfalls → References
* [ ] **Run locally** (auto via pre-commit) or manually:

  ```bash
  python _internal/scripts/validate_frontmatter.py && python _internal/scripts/build_index.py
  ```
* [ ] **Rebase on main** before pushing
* [ ] **Cite sources**; avoid plagiarism

> Why: CI runs the same checks—passing locally saves reviewers’ time.

---

## Keeping Your Fork in Sync

**Before you start or when PRs merge:**

```bash
git fetch upstream
git checkout main
git pull --ff-only upstream main
git checkout add-kebab-title
git rebase main
# If conflicts: fix -> git add <files> -> git rebase --continue
# If you rewrote history: 
git push --force-with-lease origin add-kebab-title
```

> Why: Linear history keeps diffs clean and reviews fast.

---

## Answer Structure & Frontmatter

### Frontmatter (copy/paste)

```yaml
---
id: 1
title: OSI vs TCP/IP — what’s the practical difference?
difficulty: entry         # one of: entry | easy | medium | hard | expert
week: 00
topics: [networking, models]
tags: [networking, osi, tcpip]
author: yourgithubusername
reviewed: false
---
```

**Tip:** `id` is the sequential number matching the `##-` prefix of the filename. If your file is `04-my-question.md`, then `id: 4`.

### Recommended sections

```markdown
## Short Answer
2–4 sentences an interviewer could accept.

## Deep Dive
Context, trade-offs, examples, diagrams if helpful, commands.

## Pitfalls
Common mistakes and how to avoid them.

## References
- Official docs
- High-quality blogs, RFCs, whitepapers
```

---

## Commit & PR Conventions

**Conventional Commit** examples:

```
question(04-aws/05): add IAM role vs user
docs: improve contributing guide
chore: fix build index path
```

**PR title**:

```
question(04-aws/05): add IAM role vs user with pitfalls and references
```

**PR description**:

* What changed (week, file)
* Validation passed locally
* Any reviewer notes

---

## Reviews, Governance & FAQ

**Reviews & Governance**

* PRs require **CODEOWNERS** approval for the week you changed
* CI enforces metadata/formatting; blocked PRs must be fixed and re-pushed
* High-quality answers are later marked `reviewed: true`

**Common Pitfalls**

| Issue                        | Fix                                             |
| ---------------------------- | ----------------------------------------------- |
| `id` doesn’t match file name | Rename file or update `id` to match             |
| Missing frontmatter field    | Copy template again; run validator              |
| Multiple questions in one PR | Split into separate PRs                         |
| Failing CI                   | Run both scripts locally; read the error output |

**FAQ**

* *Can I update an existing answer?* Yes—explain the change in your PR.
* *Can I submit multiple questions in one PR?* Prefer **one per PR**.
* *Do I need SSH?* Recommended. HTTPS works with cached credentials.

**Code of Conduct**
Be respectful and constructive. Disagreements are fine—disrespect isn’t.

---

### Thanks!

Your contributions help hundreds of learners practice confidently. 🙌
