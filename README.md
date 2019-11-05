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
