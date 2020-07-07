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

```zsh
$ kubectl apply -f aspnet-api.yml
```

```zsh
$ kubectl apply -f react-client-app.yml
```

```zsh
$ kubectl apply -f ingress.yml
```

    - Edit your computer's /etc/hosts file with an admin access level.
    - {minikube'sIp} hello.world
    - The real hello.world website is blocked while it is being used as the proxy of the minikube's IP address
