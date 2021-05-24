# k8s-lab
Kubernetes Lab Environment

## Getting started

```
minikube start
kubectl apply -f ~/keys/sealed-secrets.key
helmfile apply
```

This installs argocd and sealed-secrets which then deploys everything else. ArgoCD is combined with a Cloudflare Argo 
Tunnel (Name is coincidental) to run over an outbound connection instead of requiring firewall rules, port forwarding etc.  

## Next Steps
Visit [ArgoCD](https://argocd.distrail.io) and login with github credentials. 

## Next Steps - CLI
Login via the CLI (will redirect using and login via the browser)
`argocd login --sso argocd.distrail.io`

## Sealing secrets

`kubeseal --scope cluster-wide <secret.yaml > sealed-secret.json`
