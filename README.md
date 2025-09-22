# argocd-poc

Prepare:

```console
minikube delete
minikube start
```

Install:

```console
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Install CLI:

```console
wget https://github.com/argoproj/argo-cd/releases/download/v3.1.6/argocd-linux-amd64 -O ~/bin/argocd
chmod +x ~/bin/argocd
```

Change `argocd-server` service to `NodePort`. Then:

```console
minikube service argocd-server -n argocd --url
```

Get login credentials:

```console
argocd admin initial-password -n argocd
```

Bootstrap gitops:

```console
kubectl apply -f root-argocd-app.yml
```
