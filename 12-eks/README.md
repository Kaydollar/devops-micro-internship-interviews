# Week 12 — Amazon EKS

EKS questions appear at mid-to-senior level whenever the role mentions Kubernetes on AWS. The topics that come up most are IRSA (IAM roles for pods), node scaling, and how the AWS Load Balancer Controller provisions ALBs from Ingress resources. If you have set up an EKS cluster with Terraform — including the OIDC provider, managed node groups, and IRSA for each system component — you have a complete, specific answer for every question in this section.

**Appears in:** mid-to-senior rounds for cloud engineer, platform engineer, and DevOps roles where the job description mentions EKS, Kubernetes on AWS, or IRSA.

## Discussion

New questions and community answers → **[GitHub Discussions → Production AWS Platform Q&A](../../discussions)**

## Questions

| # | Question | Difficulty | Link |
|---|---|---|---|
| 1 | What is IRSA and why do you use it? | medium | [Open](questions/01-what-is-irsa-and-why-use-it.md) |
| 2 | How does the ALB Ingress Controller work in EKS? | medium | [Open](questions/02-alb-ingress-controller-in-eks.md) |
| 3 | What is Karpenter and how does it differ from Cluster Autoscaler? | medium | [Open](questions/03-karpenter-vs-cluster-autoscaler.md) |
| 4 | How do you set up an EKS cluster with managed node groups using Terraform? | hard | [Open](questions/04-eks-managed-node-groups-setup.md) |
