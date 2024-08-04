# learning_kubernetes
This is a simple project for Kubernetes basics

#### Commands

1. To start Minikube
```bash
minikube start
```
2. Check Version of kubectl
```bash
kubectl version
```
```
Client Version: v1.29.2
Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3
```
3.
```bash
kubectl get po -A
```
```
NAMESPACE     NAME                                      READY   STATUS    RESTARTS      AGE
default       kc-flaskapp-deployment-6d447d6cb7-dt4lm   1/1     Running   0             17m
default       kc-flaskapp-deployment-6d447d6cb7-nft4n   1/1     Running   0             17m
default       kc-flaskapp-deployment-6d447d6cb7-rv26s   1/1     Running   0             17m
kube-system   coredns-7db6d8ff4d-lpz47                  1/1     Running   1 (42m ago)   81m
kube-system   etcd-minikube                             1/1     Running   1 (42m ago)   82m
kube-system   kube-apiserver-minikube                   1/1     Running   1 (42m ago)   82m
kube-system   kube-controller-manager-minikube          1/1     Running   1 (42m ago)   82m
kube-system   kube-proxy-dd2j5                          1/1     Running   1 (42m ago)   81m
kube-system   kube-scheduler-minikube                   1/1     Running   1 (42m ago)   82m
kube-system   storage-provisioner                       1/1     Running   3 (18m ago)   82m
```
4. Apply a deployment in cluster
```bash
kubectl apply -f deployment.yml
```
5. List all pods
```bash
kubectl get pods
```
```
NAME                                      READY   STATUS              RESTARTS   AGE
kc-flaskapp-deployment-6d447d6cb7-dt4lm   0/1     ContainerCreating   0          2m6s
kc-flaskapp-deployment-6d447d6cb7-nft4n   0/1     ContainerCreating   0          2m6s
kc-flaskapp-deployment-6d447d6cb7-rv26s   0/1     ContainerCreating   0          2m6s
```
6 Apply a service in cluster
```bash
kubectl apply -f service.yml
```
7. List all services
```bash
kubectl get services
```
```
NAME                  TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kc-flaskapp-service   NodePort    10.106.33.174   <none>        5000:30005/TCP   8m1s
kubernetes            ClusterIP   10.96.0.1       <none>        443/TCP          74m
```
8. Access Minikube Dashboard
```bash
minikube dashboard
```
```
![image](https://github.com/user-attachments/assets/7b05cdd8-99fb-44bd-9266-2c74c13f0d3a)

```
9. Port Forwarding for Tunneling
```bash
kubectl port-forward service/kc-flaskapp-service 5000:5000
```
```
Forwarding from 127.0.0.1:5000 -> 5000
Handling connection for 5000
Handling connection for 5000
Handling connection for 5000
Handling connection for 5000
Handling connection for 5000
Handling connection for 5000
```
```
![image](https://github.com/user-attachments/assets/8356ca58-3318-4ee5-b264-c62097c6f412)

```
