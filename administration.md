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


## Wordpress example

1. deploy mysql
2. deploy wordpress

### enable ingress metallb on node

microk8s enable metallb:10.64.140.43-10.64.140.49

METALLB