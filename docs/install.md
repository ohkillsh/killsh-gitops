# Install

- [Argo CD Operator Manual](https://argo-cd.readthedocs.io/en/stable/operator-manual/core/)
  
```bash
export ARGOCD_VERSION=<desired argo cd release version (e.g. v2.7.0)>
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/$ARGOCD_VERSION/manifests/core-install.yaml

kubectl apply -k https://github.com/argoproj/argo-cd/manifests/crds\?ref\=stable

argocd proj create cluster-addons
```

## NGINX

- SSL Termination at Ingress Controller

    kubectl apply -f docs/ingress-nginx.yaml

## Testing

Testando o Argo CD

```bash
kubectl apply -f cluster-config/environments/testing/config.yaml 
kubectl describe applicationset.argoproj.io/cluster-addons-application-set -n argocd
```
