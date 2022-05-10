# Persistent Volume

## Example configuration

```yml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: local-pv-1
spec:
  capacity:
    storage: 30Gi
  volumeMode: Filesystem
  accessModes:
  - ReadWriteOnce
  storageClassName: microk8s-hostpath
  persistentVolumeReclaimPolicy: Delete
  local:
    path: /local_volume/v1
  nodeAffinity:
    required:
      nodeSelectorTerms:
      - matchExpressions:
        - key: kubernetes.io/hostname
          operator: In
          values:
          - microkube1
```


## Volume access modes

* `ReadWriteOnce`
> the volume can be mounted as read-write by a single node. ReadWriteOnce access mode still can 
> allow multiple pods to access the volume when the pods are running on the same node.

* `ReadOnlyMany`
> the volume can be mounted as read-only by many nodes.

* `ReadWriteMany`
> the volume can be mounted as read-write by many nodes.

* `ReadWriteOncePod`
> the volume can be mounted as read-write by a single Pod. Use ReadWriteOncePod access mode if you want to ensure that only one pod across whole cluster can read that PVC or write to it. This is only supported for CSI volumes and Kubernetes version 1.22+


# Persistent Volume Claim

## Example configuration

```yml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
  labels:
    app: wordpress
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: microk8s-hostpath
  resources:
    requests:
      storage: 20Gi
```

# Consuption of persistent volume claim

```yml
kind: Deployment
metadata:
  name: wordpress-mysql
  labels:
    app: wordpress
spec:
  selector:
    matchLabels:
      app: wordpress
      tier: mysql
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: wordpress
        tier: mysql
    spec:
      containers:
      - image: mysql:5.6
        name: mysql
        env:
        - name: MYSQL_ROOT_PASSWORD
          value: PASSWORDS_IN_PLAIN_TEXT_ARE_BAD_WE_WILL_SHOW_SOMETHING_MORE_SECURE_LATER
        ports:
        - containerPort: 3306
          name: mysql
        volumeMounts:
        - name: mysql-persistent-storage
          mountPath: /var/lib/mysql
          subPath: mysql
      volumes:
      - name: mysql-persistent-storage
        persistentVolumeClaim:
          claimName: mysql-pv-claim
```