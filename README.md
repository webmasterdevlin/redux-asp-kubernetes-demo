### ASP.NET Core web application React.js and Redux in Kubernetes

    - terminal must be in admin level to run minikube

Choose HyperV (for Windows), Hyperkit (for MacOS), Virtualbox (for Linux)

```zsh
$ minikube config set driver {hyperv|hyperkit|virtualbox}
```

Start Kubernetes Cluster

```zsh
$ minikube start
```

Basic Addons

```zsh
$ minikube addons enable ingress
$ minikube addons enable metrics-server
```

Get the Minikube IP

```zsh
$ minikube ip
```

Show Kubernetes Dashboard

```zsh
$ minikube dashboard
```

```zsh
$ kubectl apply -f react-asp-in-minikube.yml
```

## OR

```zsh
$ kubectl apply -f seperated-yamls/aspnet-api.yml
```

```zsh
$ kubectl apply -f seperated-yamls/react-client-app.yml
```

```zsh
$ kubectl apply -f seperated-yamls/minikube-ingress.yml
```

    - Edit your computer's /etc/hosts file with an admin access level.
    - {minikube'sIp} hello.world
    - The real hello.world website is blocked while it is being used as the proxy of the minikube's IP address

Send requests

```zsh
$ for ((i=1;i<=200;i++)); do curl http://hello.world/fetch-data; done
```

---

## AKS

Set subscription ID and cluster

```zsh
$ az account set --subscription yourSubscriptionID
$ az aks get-credentials --your-resource-group your-rg --name yourCluster
```

Create a namespace for your ingress resources

```zsh
$ kubectl create namespace ingress-basic
```

Add the official stable repository

```zsh
$ helm repo add stable https://kubernetes-charts.storage.googleapis.com/
```

Use Helm to deploy an NGINX ingress controller

```zsh
$ helm install nginx-ingress stable/nginx-ingress \
 --set controller.replicaCount=2 \
 --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \
 --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux
```

---

### TLS

```zsh
$ kubectl create namespace cert-manager
```

```zsh
helm repo add jetstack https://charts.jetstack.io
helm repo update
```

```zsh
$ kubectl apply --validate=false -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.14/deploy/manifests/00-crds.yaml
```

```zsh
helm install cert-manager \
    --namespace cert-manager \
    --version v0.14.0 \
    jetstack/cert-manager
```

```zsh
$ kubectl get pods --namespace cert-manager
```

```zsh
$ kubectl apply -f cluster-issuer.yaml
```
