# Extend metrics server capabilites

With this case, we try how use Keda with `custom` and `extended` metrics

## Scenario

As usual, our best committer [Acme Corp.](https://it.wikipedia.org/wiki/Acme_Corporation) has realized a new web solution for all their customers, to manage all data collected from their jobs(mainly complaints).

## Requirement

We have to make a ~~fictional~~ classic production environment where the acme should deploy their solution based on Kubernetes FKD and patch it to extend the monitoring for Keda.

## Prerequisites

- We have to know how use [Minikube](https://kubernetes.io/docs/tutorials/hello-minikube/),[Furyctl](https://github.com/sighupio/furyctl) and [Kustomize](https://kustomize.io/).
- We have to know how use [Keda](https://keda.sh/docs/2.10/concepts/) and [Prometheus operator](https://prometheus-operator.dev/).

- You can get the version of the toos from the file `.tool-version` or using [asdf](https://asdf-vm.com/)

## Design

- TBD

## Structure

Due to the complexity of the infrastructure, the manifest files which describe the Kubernetes cluster resources are organized in modules as follows:

```(shell)
extended-metrics-server
  ├── playground
  │     ├── infra
  │     └── manifests
  └── vendors
```

### Makefile

The aim of Makefile files is to wrap in a unique command useful and frequent operations related to a Kubernetes module or to a full environment:

```(makefile)
creds = ../../secrets/vars.sh
kubecfg = ../../secrets/kubeconfig

# Stage
.PHONY: build
stage-build:
 @kustomize build ./stage

.PHONY: diff
diff:
 source $(creds) && kustomize build ./stage | kubectl diff -f - --kubeconfig=$(kubecfg) 

.PHONY: deploy
deploy:
 source $(creds) && kustomize build ./stage | kubectl apply -f - --kubeconfig=$(kubecfg) | grep -v unchanged
```
