# GitHub Discussions — Setup Guide

This file documents the Discussion categories to create when enabling Discussions on this repo.

## How to enable Discussions

1. Go to the repo on GitHub
2. **Settings → General → Features**
3. Check **Discussions** → Save
4. Go to the **Discussions** tab
5. Click **Edit categories** (pencil icon, top right)
6. Delete the default categories GitHub creates
7. Add the categories below in order

---

## Categories to create

### 1. Announcements
- **Type:** Announcement
- **Description:** New weeks, major updates, monthly highlights. Maintainer posts only.
- **Emoji:** 📣
- **Note:** Only maintainers can open threads here. Community can react but not reply. Use for: new week releases, monthly top-answer highlights, repo milestones.

---

### 2. Foundations Q&A
- **Type:** Q&A
- **Description:** Weeks 00–03 — Networking, Linux, Git, DevOps lifecycle.
- **Emoji:** 🌐
- **Covers:** DNS, OSI model, TCP/IP, Linux commands, file permissions, Git branching, merge vs rebase, CI/CD concepts.
- **Note:** Q&A type allows upvoting answers and marking one as the accepted answer. The accepted answer shows a preview at the top of the thread.

---

### 3. Cloud Platforms Q&A
- **Type:** Q&A
- **Description:** Weeks 04–05 — AWS and Azure interview questions.
- **Emoji:** ☁️
- **Covers:** IAM, VPC, EC2, S3, Lambda, Azure AD, Azure networking, resource groups.

---

### 4. IaC & Automation Q&A
- **Type:** Q&A
- **Description:** Weeks 06–08 — Terraform, Ansible, CI/CD pipelines.
- **Emoji:** 🏗️
- **Covers:** Terraform state, modules, providers, Ansible playbooks, roles, Azure DevOps pipelines, GitHub Actions.

---

### 5. Containers & Kubernetes Q&A
- **Type:** Q&A
- **Description:** Weeks 09–10 — Docker and Kubernetes.
- **Emoji:** 🐳
- **Covers:** Dockerfile best practices, multi-stage builds, pods, deployments, services, ingress, RBAC, HPA, rolling vs blue-green vs canary.

---

### 6. Observability Q&A
- **Type:** Q&A
- **Description:** Week 11 — Prometheus, Grafana, logging, tracing.
- **Emoji:** 📊
- **Covers:** Three pillars (metrics, logs, traces), Prometheus scraping, PromQL, Grafana dashboards, FluentBit, Zipkin, OpenTelemetry.

---

### 7. Production AWS Platform Q&A
- **Type:** Q&A
- **Description:** Production-grade AWS platform engineering — EKS, Helm, ArgoCD, Karpenter, ECR, RDS, Secrets Manager.
- **Emoji:** 🚀
- **Covers:** EKS cluster setup, IRSA, Karpenter node autoscaling, Helm chart structure, ArgoCD GitOps pattern, rollbacks via Git revert, AWS Secrets Manager, External Secrets Operator, ALB Ingress, ACM certificates.
- **Note:** This category is seeded from the DevOps with Claude Code course (Udemy). Questions here are production-level, typically mid to senior difficulty.

---

### 8. Share Your Interview Experience
- **Type:** Open-ended
- **Description:** Just had an interview? Share what you were asked, what went well, and what caught you off guard.
- **Emoji:** 💬
- **Note:** This is the most important category for community growth. Students post raw experiences here — no formatting required, no PR needed. Maintainers watch this category to spot questions worth promoting to markdown files. Apply the `interview-reported` label to threads that describe a real interview question.

---

### 9. Polls
- **Type:** Poll
- **Description:** Vote on what topics to add next, which tools you use, how you're preparing.
- **Emoji:** 📊
- **Example polls to create:**
  - "Which cloud provider does your target company use?"
  - "What difficulty level do you want more of?"
  - "Which week do you want expanded first?"
  - "Are you preparing for junior, mid, or senior roles?"

---

### 10. Ideas & Feedback
- **Type:** Open-ended
- **Description:** Suggest new content, report gaps, or give feedback on existing answers.
- **Emoji:** 💡

---

## Pinned discussions to create after setup

Create these threads immediately after enabling Discussions — pin them so they appear at the top:

### Pin 1: Welcome & How This Works
Open in **General / Ideas & Feedback**. Write:
> Welcome. This is how the community works: post interview questions in Discussions, upvote the answers you found useful, and mark the best answer when you see one. The top answers get turned into permanent markdown files via Pull Request. No setup needed to participate — just a GitHub account.

### Pin 2: Interview Experience Thread (rolling)
Open in **Share Your Interview Experience**. Write:
> Drop your interview questions here. Company name optional. Just tell us: what were you asked, what did you say, what did they actually want to hear? Every question you share helps the next person.

---

## Labels to create

Go to **Issues → Labels** and add:

| Label name | Color | Description |
|---|---|---|
| `interview-reported` | `#0075ca` | Someone was actually asked this in a real interview |
| `needs-example` | `#e4e669` | Answer exists but lacks a real-world example |
| `verified` | `#0e8a16` | Reviewed and approved by a maintainer |
| `good first issue` | `#7057ff` | Easy entry point for new contributors |
| `help wanted` | `#008672` | Needs a better answer |
| `type:question` | `#d93f0b` | A new question submission |
| `type:improvement` | `#fbca04` | Improving an existing answer |

---

## Slack / Teams integration (optional)

To get notified in Slack when someone posts to Discussions:

```
/github subscribe pravinmishraaws/devops-micro-internship-interviews discussions
```

Run this in your Slack channel after installing the GitHub Slack app.
