# Installation

## Prerequisites

- `direnv`
- Docker
- Correct version of kubectl
- Correct version of kind
  - [Kind](https://kind.sigs.k8s.io) is for running local Kubernetes
  - Download from [kind releases](https://github.com/kubernetes-sigs/kind/releases)

## Installation

- Set KUBE_VERSION=1.27.0
- Download the $KUBE_VERSION of `kubectl` executable into `./bin`, make it executable
- Verify version with `kubectl version --client`
- Download `kind` executable into `./bin`
- Create a cluster with `kind create cluster --config ./my-cluster.yaml`

## Development

- Check the cluster(s): `kind get clusters`
- Create kubernetes objects (in default namespace): `kubectl create -f ./my-objects.yml`
- Check the objects created: `kubectl get all`
- Check the pods created: `kubectl get pods -o wide`
- Go in to nginx pod: `kubectl exec -it nginx-pod -- /bin/bash`
- Delete all clusters: `kind delete clusters --all`


## Access service

- Deploy pods: `kubectl create -f ./deploy.yaml`
- Create service: `kubectl create -f ./svc.yaml`
- Wait for pods to be ready: `kubectl get pods -w`
- Check what nodes the pods belong to: `kubectl get pods -o wide`
- Get the node ips: `kubectl get nodes -o wide`
- Get the service nodePort: `kubectl get svc`
- Access the created service: `curl http://<node-ip>:<node-port>`
