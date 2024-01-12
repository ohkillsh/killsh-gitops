# Install

- [Argo CD Operator Manual](https://argo-cd.readthedocs.io/en/stable/operator-manual/core/)
  
```bash
export ARGOCD_VERSION=<desired argo cd release version (e.g. v2.7.0)>
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/$ARGOCD_VERSION/manifests/core-install.yaml

kubectl apply -k https://github.com/argoproj/argo-cd/manifests/crds\?ref\=stable


# retrieve initial password 
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

argocd proj create cluster-addons

argocd cluster add arn:aws:eks:eu-central-1:1234567890:cluster/dev-eks-k8s-local --name dev-eks-k8s-local --label environment=dev

https://freedium.cfd/https://medium.com/@mprzygrodzki/argocd-applicationsset-with-helm-72bb6362d494
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
