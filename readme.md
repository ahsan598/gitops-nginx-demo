# Deploy Nginx Application via ArgoCD

**1.  Deploy Nginx demo application to ArgoCD**
```sh
# Provision Isolated Namespaces
kubectl create namespace dev

# deploy nginx demo application to ArgoCD
kubectl apply -f apps/nginx-app.yaml

# verify nginx demo application
kubectl get application nginx-app -n argocd

# 3. Verify deployed pods & service in dev namespace
kubectl get deployment nginx-app -n dev
kubectl get pods -n dev -l app=nginx-app
kubectl get svc nginx-app -n dev
```
![nginx-app](/assets/nginx-pods.jpg)

![argocd-deploy](/assets/argocd-deploy.jpg)

**2. Test Local Application Access**
```sh
# Access the Nginx demo application directly via the exposed NodePort endpoint
curl -I http://localhost:30080
```
![app-verify](/assets/nginx-app.jpg)

**3. Delete Application via Argo CD**
```sh
# Delete the Argo CD Application resource
kubectl delete -f apps/nginx-app.yaml

# Verify pods & service are terminated
kubectl get pods -n dev
kubectl get svc -n dev
```
