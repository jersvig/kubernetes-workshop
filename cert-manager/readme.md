# Installing `cert-manager`

[DOCS SOURCE]([https://](https://getbetterdevops.io/k8s-ingress-with-letsencrypt/))


## 1. Install helm

```bash
sudo snap install helm --classic
```

## 2. Install `cert-manager` via `helm`

Run commands

```
helm repo add jetstack https://charts.jetstack.io
```
```
helm repo update
```
```
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --set installCRDs=true
```
Expected output

>```
>NAME: cert-manager
>LAST DEPLOYED: Tue Oct 18 12:22:19 2022
>NAMESPACE: cert-manager
>STATUS: deployed
>REVISION: 1
>TEST SUITE: None
>NOTES:
>cert-manager v1.10.0 has been deployed successfully!
>```