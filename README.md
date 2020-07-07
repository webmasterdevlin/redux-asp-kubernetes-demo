#### ASP.NET Core web application React.js and Redux in Kubernetes

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
