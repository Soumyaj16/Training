# Three-tier EKS example

Minimal example of frontend, backend, and Postgres to deploy on EKS and manage with ArgoCD.

## Workflow

1. Build and push Docker images for frontend and backend to your container registry (ECR, Docker Hub, etc.).
2. Update image references in `k8s/frontend-deployment.yaml` and `k8s/backend-deployment.yaml`.
3. Commit this repo to a Git repo and point the ArgoCD `argocd-application.yaml` `spec.source.repoURL` and `path` to it.
4. Create the `three-tier` namespace, then apply or let ArgoCD sync the application.

Notes:
- This example uses a simple Postgres Deployment + PVC for demonstration. For production, use a managed DB (RDS/Aurora) or a StatefulSet with proper backups/HA.
- Replace placeholders such as `<REGISTRY>/frontend:tag` and `<REGISTRY>/backend:tag`.
