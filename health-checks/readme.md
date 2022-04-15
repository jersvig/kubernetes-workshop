# Health checks

## Deploy deployment

```bash
kubectl apply -f ./deployment-probes.yaml
```

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