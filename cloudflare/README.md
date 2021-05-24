# Argo-tunnel


This [repo](https://github.com/cloudflare/helm-charts/tree/master/charts/argo-tunnel) was found unmaintained so a new chart was created using the docker image from:
- [dockerhub](https://hub.docker.com/r/cloudflare/cloudflared)
- [github](https://github.com/cloudflare/cloudflared)

Cert created and then converted to a sealed secret.

```
cat << 
apiVersion: bitnami.com/v1alpha1
kind: SealedSecret
metadata:
  name: cloudflare-cert
  namespace: temp
spec:
  encryptedData:
    foo: AgBy3i4OJSWK+PiTySYZZA9rO43cGDEq.....

```
