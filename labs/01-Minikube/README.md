# Deploy Minukube environment

## Minikube setup  

### MacOS

Using Brew 

```
$ brew cask install minikube
```

or 

```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 \
  && sudo install minikube-darwin-amd64 /usr/local/bin/minikube
```

### Linux

```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
   && sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### Windows 

Using Chocolatey

```
$ choco install minikube
```

or [direct download](https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe)


## Hypervisor setup (Virtualbox 5.2 or later)

```
$ minikube config set vm-driver virtualbox
$ minikube config set memory 4096
$ minikube start --vm-driver=virtualbox
```

More at [Minikube website](https://minikube.sigs.k8s.io/docs/start/)

## Test the installation

Start Minikube

```
$ minikube start
```
Schedule your first Pod

```
$ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080
```

Expose the Pod to the external world

```
$ kubectl expose deployment hello-minikube --type=NodePort
```

minikube makes it easy to open this exposed endpoint in your browser:

```
$ minikube service hello-minikube

|-----------|----------------|-----------------------------|
| NAMESPACE |      NAME      |             URL             |
|-----------|----------------|-----------------------------|
| default   | hello-minikube | http://192.168.99.101:32223 |
|-----------|----------------|-----------------------------|
🎉  Opening kubernetes service  default/hello-minikube in default browser...
```