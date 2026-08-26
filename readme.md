### Deploy Nginx demo application to ArgoCD

```sh
# deploy nginx demo application to ArgoCD
kubectl apply -f nginx-demo.yaml

# verify nginx demo application
kubectl get applications -n argocd

# verify pods & service
kubectl get pods
kubectl get svc nginx-demo
```