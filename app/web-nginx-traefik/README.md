# Tests

```bash
kubectl apply -k app/web-nginx-traefik

PUBLIC_IP=`kubectl describe svc/traefik -n ingress | grep 'LoadBalancer Ingress' | awk -F: '{ gsub(/ /,"");print $2 }'`
curl -I -H 'Host: app.ohkillsh.win' http://$PUBLIC_IP
```