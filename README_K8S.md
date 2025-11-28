# K8s / ArgoCD / TLS Quickstart (summary)

1. Ensure AKS credentials present: `az aks get-credentials -g <rg> -n <aks>`
2. Install ingress-nginx:
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.1/deploy/static/provider/cloud/deploy.yaml
3. Install cert-manager:
   kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.14.4/cert-manager.yaml
4. Apply ClusterIssuer (argocd/cluster-issuer.yaml) with your email
5. Build & push images to ACR or registry
6. Update manifests image tags if needed and push to repo
7. Create ArgoCD applications or let ArgoCD track folders
8. Add DNS A records pointing to ingress external IP
9. Check `kubectl get certificate -A` and `kubectl describe certificate -n <ns> <name>`
