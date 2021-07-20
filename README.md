# Common Setup
1. Create GKE cluster in mw-ace-v2 project using gcp console (use preemptible machines)
```
gcloud container clusters get-credentials pg-cluster --zone us-central1-c
kubectl config get-contexts
kubectl get nodes
kubectl get all -n default
```

# kustomize demo
```
brew install kustomize
```

```
cd kustomize-basic
kustomize build .
kubectl apply -k .
kubectl delete -k .
```

```
cd ../kustomize-demo/ 
kustomize build overlays/dev
kustomize build overlays/prod

kubectl apply -k overlays/dev
kubectl delete -k overlays/dev

kubectl apply -k overlays/prod
kubectl delete -k overlays/prod
```


# argocd demo
```
brew install argocd
```

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get all -n argocd
```

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

```
kubectl port-forward svc/argocd-server -n argocd 8443:443
```

1. Create Repository
2. Create Application with Manual Sync (using manifests directory)
3. Sync App
4. Access App
5. Delete Pod   
6. Auto Sync   
7. Change replica count in src and commit
8. Check cluster   
9. Delete App


```
kubectl port-forward svc/nginx -n default 8080:80
```

# Combined demo
1. Create Application with Manual Sync (using kustomize-demo/overlays/prod directory)
2. Sync App
3. Check cluster
4. Delete App

[comment]: <> (argocd login <ARGOCD_SERVER>)

[comment]: <> (argocd account update-password)
