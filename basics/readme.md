# Basics

## Deploy deployment from config file

```bash
kubectl apply -f ./deployment.yaml
```

## Basic `kubectl` commands

Inspect deployment

```bash
kubectl get pods

kubectl describe pod
 
kubectl expose deployment tomcat-deployment --type=NodePort
 
kubectl port-forward <pod name> [LOCAL_PORT:]REMOTE_PORT]
 
kubectl attach <pod name> -c <container>
 
kubectl exec -it <pod name> bash
```

