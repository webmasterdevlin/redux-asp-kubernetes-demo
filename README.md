#### ASP.NET Core web application React.js and Redux in Kubernetes

    - terminal must be in admin level to run minikube

```zsh
$ minikube config set driver {hyperv|hyperkit|virtualbox}
```

```zsh
$ minikube start
```

```zsh
$ minikube addons enable ingress
```

```zsh
$ minikube ip
```

```zsh
$ minikube addons enable metrics-server
$ minikube dashboard
```
