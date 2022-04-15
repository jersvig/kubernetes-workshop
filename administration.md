# Health checks

## Probes

* via web calls
* via bash exec script on container (standard return codes)

### Readiness probe
```yml
        readinessProbe:
          httpGet:
            path: /
            port: 8080
          initialDelaySeconds: 15
          periodSeconds: 3
```


### Liveness probe

```yml
        livenessProbe:
          httpGet:
            path: /
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 30
```

# DNS & Service Discovery

Attach to pod and run

```
cat /etc/resolv.conf
```

to see dns settings applied to current pod


# Basic ingress



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
