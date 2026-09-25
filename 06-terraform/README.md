# Week 06 — Terraform (IaC)

Terraform is the standard for provisioning cloud infrastructure in code. Interviews test your understanding of state management, module structure, and the plan-apply workflow — because these are where real infrastructure goes wrong. If you have built a platform with Terraform, you know the S3 state key, the DynamoDB lock table name, and exactly what happens if two engineers run `terraform apply` at the same time. Generic answers describe the tool. Specific answers prove you used it.

**Appears in:** mid-to-senior rounds for infrastructure engineer, platform engineer, and DevOps roles. State management and module structure questions are near-universal.

## Discussion

New questions and community answers → **[GitHub Discussions → IaC & Automation Q&A](../../discussions)**

## Questions

| # | Question | Difficulty | Link |
|---|---|---|---|
| 1 | Terraform remote state, backends, and locking — the basics | medium | [Open](questions/01-terraform-state-backends-locking.md) |
| 2 | Terraform remote backend state locking — deep dive | medium | [Open](questions/02-terraform-remote-backend-state-locking.md) |
| 3 | Terraform state locking and consistency — concurrent applies | medium | [Open](questions/03-terraform-state-locking-and-consistency.md) |
| 4 | Terraform remote state, backends, and locking — advanced | medium | [Open](questions/04-terraform-state-locking.md) |
| 5 | How do you manage Terraform state for multiple environments? | medium | [Open](questions/05-manage-state-multiple-environments.md) |
| 6 | How do you review a Terraform change before applying? | easy | [Open](questions/06-review-terraform-change-before-applying.md) |
| 7 | How do you structure Terraform modules for a production platform? | medium | [Open](questions/07-terraform-module-structure.md) |
| 8 | How do you authenticate GitHub Actions to AWS without storing credentials? | medium | [Open](questions/08-github-actions-oidc-aws.md) |
| 9 | What is Terraform drift, and how do you detect and fix it? | medium | [Open](questions/09-terraform-import-and-drift.md) |
