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
2. Create Application with Manual Sync
3. Sync App
4. Access App
5. Auto Sync   
6. Change replica count in src and commit
7. Check cluster   
8. Delete App


```
kubectl port-forward svc/nginx -n default 8880:80
```

argocd login <ARGOCD_SERVER>
argocd account update-password
