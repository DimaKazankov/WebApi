# GitOps Directory

This directory contains a simple nginx application deployed using GitOps principles with ArgoCD and Gitea.

## Structure

- manifest/          - Kubernetes manifests (source of truth in Git)
  - deployment.yaml
  - service.yaml
  - ingress.yaml
- bootstrap.yaml     - ArgoCD Application pointing to this repo in Gitea
- .gitops-config.yaml

## First-time setup

```bash
gitops setup    # create minikube cluster, install ArgoCD + Gitea
gitops deploy   # push manifests to Gitea, register ArgoCD app
```

## Ongoing workflow

Edit manifests, then push — ArgoCD syncs automatically via webhook:

```bash
# edit manifest/deployment.yaml ...
git add manifest/
git commit -m "bump replicas to 3"
git push
# ArgoCD syncs within ~5 seconds
```
