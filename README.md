# application-configurationsc

## Install Minikube Cluster

  [minikube_setup](https://github.com/Naresh240/kubernetes/blob/main/minikube-setup/README.md)
## Installing flux

```sh
wget https://github.com/fluxcd/flux2/releases/download/v0.27.4/flux_0.27.4_linux_amd64.tar.gz 
tar xvf flux_0.27.4_linux_amd64.tar.gz
mv flux /usr/bin
```

## Create github token

```sh
export GITHUB_TOKEN="provide github token"
```

## Flux Bootstraping

```sh
export GITHUB_USER="naresh240"
export GITHUB_REPO="application-configurations"
export GITHUB_BRANCH="master"
export GITHUB_DIR="./"

flux bootstrap github --owner=$GITHUB_USER --repository=$GITHUB_REPO --branch=$GITHUB_BRANCH --path=$GITHUB_DIR --token $GITHUB_TOKEN
```

## Tell Flux to pull the manifests from Git and upgrade itself with

```sh
flux reconcile source git flux-system
```

## Verify that the controllers have been upgrade with:
```sh
flux check
```
