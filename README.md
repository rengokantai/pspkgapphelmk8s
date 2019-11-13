# pspkgapphelmk8s

## 4. Installing
### Demo: Installing Kubernetes
```
curl -o minikube https://
chomd +x minikube
sudo cp minikube /usr/local/bin/minikube
minikube version
```
```
minikube addons enable ingress
minikube ip
```
```
curl -LO kubectl
chomd +x kubectl
kubectl version --short
```

### Demo:Installing Helm and tiller
```
kubectl config view
helm init
```
### 4 Configuring Helm Security
```
kubectl create namespace lab
helm init --service-account tiller --tiller-namespace lab
```

```
helm create test
helm install test --tiller-namespace=lab --namespace=lab
```

### 5 Demo: Running Tiller Locally
```
kubectl get configmaps --namespace=kube-system
```
### 6 Cleaning Helm
```
helm list
helm delete calling-horse --purge
rm -rf /home/m/.helm
```

## 6. Customizing Charts with Helm Templates
### 3 Playing with helm template
```
values.yaml
other-file.yaml // helm install -f file
variables //helm install -- set foo=bar
```

## 7. Managing Dependencies
### 1 Packging a Chart
```
helm package chart_name
```
And:
- Compress chart folder in a .tar.gz archive
- Add a version number to the archive

### 2 Publishing Charts in a Repository
```
helm repo index .
helm package --sign
helm verify chart.gz
helm install --verify
```
multiple packaging
```
helm package 1 2 3
ls ~/.helm/repository/local
```
retrieve repo list
```
helm repo list
```
start local server
```
helm serve
```
##### 3:23 remove
```
helm repo add myrepo http://
helm repo remove myrepo
```
check
```
x-www-browser heep://127.0.0.1/8879
```
### 4 Defining Dependencies
```
dependencies:
  - name: backend
    version: ~1.2.2
    repository: http://
  - name: frontend
    version: ^1.2.0
    repository: http://127.0.0.1:8879/charts
```

##### 2:54
update
```
helm dependency update guestbook
helm dependency list guestbook
```
generate lock file
```
helm dependency build guestbook
```

### 5 Adding Conditions and Tags
Note: conditions will override tags
```
dependencies:
  - name: backend
    version:
    repository:
    condition:
    tags:
      - api
```
values.yaml
```
backend:
  enabled: true
tags:
  api: true
```
set command
```
helm install guestbook --set database.enabled=true
```
### 6 Demo: Managing Dependencies
```
helm dependency update guestbook
ls guestbook/charts
```


## 8. Using Existing Helm Charts
### 1 Using Existing Helm Charts
```
helm repo list
helm search keyword
helm inspect chart_name
helm inspect chart chart_name
helm inspect values chart_name
helm fetch chart_name
helm dependency update chart_name
```


