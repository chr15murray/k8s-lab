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
k3d cluster create --config k3d-lab.yaml
helmfile apply
```

This installs argocd and sealed-secrets which then deploys everything else. ArgoCD is combined with a Cloudflare Argo 
Tunnel (Name is coincidental) to run over an outbound connection instead of requiring firewall rules, port forwarding etc.  

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

## Sealing secrets

`kubeseal --scope cluster-wide <secret.yaml > sealed-secret.json`
