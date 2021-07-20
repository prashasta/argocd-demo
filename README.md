# argocd-demo
```
gcloud container clusters get-credentials pg-cluster --zone us-central1-c
kubectl config get-contexts
```
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
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

argocd login <ARGOCD_SERVER>
argocd account update-password
