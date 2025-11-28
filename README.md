# TODO Microservices Full Setup (Demo)

This repository is a **complete demo** of a microservices TODO app and includes:
- 3 backend microservices (Flask) for Add / Get / Delete tasks
- 1 static UI (vanilla JS) served via nginx
- Dockerfiles for each component
- Kubernetes manifests for Deployments, Services, Namespaces, Ingress (with TLS placeholders)
- cert-manager ClusterIssuer example for Let's Encrypt
- ArgoCD Application manifests to deploy each microservice from repo
- Terraform sample (in `infra/`) to create AKS + ACR (minimal example)
- GitHub Actions workflow to build & push images to ACR (skeleton)

This demo is intended for learning and can be adapted to production workflows.

## Quick structure
```
/AddTaskTodoMicroservice
/GetTasksTodoMicroservice
/DeleteTaskTodoMicroservice
/MicroTodoUI
/infra
/argocd
.github/workflows
README.md
```

## How to run locally (docker-compose NOT included)
You can build and run each service locally with Docker:

```bash
# Build
docker build -t todo-add:local ./AddTaskTodoMicroservice
docker build -t todo-get:local ./GetTasksTodoMicroservice
docker build -t todo-delete:local ./DeleteTaskTodoMicroservice
docker build -t todo-ui:local ./MicroTodoUI

# Run (example)
docker run -p 8001:8000 todo-add:local
docker run -p 8002:8000 todo-get:local
docker run -p 8003:8000 todo-delete:local
docker run -p 8080:80 todo-ui:local
```

## Kubernetes / ArgoCD / ACR / AKS
See the `README_K8S.md` inside the repo for deployment steps including:
- Terraform infra
- Install ingress-nginx
- Install cert-manager
- Create DNS A records
- Build & push images to ACR
- Create ArgoCD Applications and sync

---

## License
MIT
