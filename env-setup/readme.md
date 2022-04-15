# Dev env setup

## Get microk8s cluster configuration

1. ssh to master node

2. run

    >`microk8s config > microk8s.config`
    

## Setup local `kubectl`

1. copy `microk8s.config` from master kubernetes node to local dev machine

2. add to local `.bashrc` file:

    > export KUBECONFIG="/path/to/microk8s.config"

## Setup vscode

1. install Kubernetes plugin

    > [VS Code marketplace / Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-kubernetes-tools)

2. Add to vscode settings in `vs-kubernetes` key:
    ```json
    "vs-kubernetes": {
        "vs-kubernetes.knownKubeconfigs": [
            "/path/to/microk8s.config"
        ],
        "vs-kubernetes.kubeconfig": "/path/to/microk8s.config"
    }
    ```

## Other admin dev tools

* [Kubernetes Lens](https://k8slens.dev/)