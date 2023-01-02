# Kubernetes commands

```bash
kubectl get pods or pod
# pod name = name of the deployment + replica id + own POD id

kubectl get deployment
kubectl get services
kubectl get replicaset

# create deployment
kubectl create deployment nginx --image=nginx

kubectl get nodes
kubectl get componentstatuses # (controller, scheduler, etcd)

kubectl apply -f nginx.yaml # f is file
kubectl delete -f nginx.yaml

# edit deployment
kubectl edit deployment nginx

# debugging deployment
kubectl logs pod-name

kubectl describe pod-name

kubectl exec -ti pod-name -- /bin/bash

```
