# Week 14 — ArgoCD & GitOps

GitOps questions test whether you understand the delivery model — not just the tools. The key insight is that Git is the source of truth: the cluster state should always match what is in the repo, and any change goes through a commit. ArgoCD implements this by watching the repo and reconciling continuously. Interviewers want to know how you handle the dev/prod split (auto-sync vs manual gate), how a rollback works in GitOps, and how the image tag flows from CI to deployment.

**Appears in:** mid-to-senior rounds for any role that mentions GitOps, ArgoCD, continuous delivery, or declarative deployment. Fast-growing category — expect more of these questions in every interview.

## Discussion

New questions and community answers → **[GitHub Discussions → Production AWS Platform Q&A](../../discussions)**

## Questions

| # | Question | Difficulty | Link |
|---|---|---|---|
| 1 | Explain GitOps — how does ArgoCD implement it? | medium | [Open](questions/01-explain-gitops-how-argocd-implements-it.md) |
| 2 | How do you roll back a deployment in a GitOps setup? | medium | [Open](questions/02-how-to-rollback-deployment-gitops.md) |
| 3 | How do you configure ArgoCD sync policies differently for dev and prod? | medium | [Open](questions/03-argocd-sync-policies-dev-vs-prod.md) |
| 4 | How does the image tag update flow work in a GitOps pipeline? | medium | [Open](questions/04-gitops-image-tag-update-workflow.md) |
| 5 | How do you roll back a broken deployment in a GitOps workflow? | medium | [Open](questions/05-argocd-rollback-in-gitops.md) |
