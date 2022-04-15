# Ingress basics


## Deploy services

1. deploy mysql

>```
>kubectl apply -f mysql-deployment.yml
>```

2. deploy wordpress

>```
>kubectl apply -f wordpress-deployment.yml
>```

3. deploy echo

>```
>kubectl apply -f whoami-deployment.yml
>```

## Edit local `/etc/hosts`

add lines

```
192.168.241.190 	wp.micro.com
192.168.241.190		echo.micro.com
```

## Enable ingress

Run:

```
kubectl apply -f ingress.yml
```