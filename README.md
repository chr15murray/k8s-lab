# k8s-lab
Kubernetes Lab Environment

This repo builds the basis of the lab then [k8s-lab-apps](https://github.com/distrail-io/k8s-lab-apps) is used in a gitops
fashion for application management using argocd. Key tools are:
- ArgoCD - GitOps, App Of Apps setup for component install
- Sealed Secrets - Used for initial bootstrapping of the cluster. 
- Istio - My service mesh of choice
- cloudflare argo - Used to 'publish' argocd even from behind NAT


## Getting started

```
# Create the Cluster
k3d cluster create --config k3d/k3d-lab.yaml

# Add the External Secrets Namespace and secret
kubectl apply -f bootstrap/manifests/external-secrets-namespace.yaml
kubectl apply -f ~/keys/external-secrets-gcp-secret.yaml -n external-secrets

# Install External Secrets
helmfile -f external-secrets/helmfile.yaml apply

# Deploy ArgoCD
kubectl kustomize bootstrap/kustomize/ | kubectl apply -f -
```

## Cleanup

Once complete just delete the cluster.
```
k3d cluster delete lab
```

## Next Steps
Visit [ArgoCD](https://argocd.distrail.io) and login with github credentials. 

## Next Steps - CLI
Login via the CLI (will redirect using and login via the browser)
`argocd login --sso argocd.distrail.io`

