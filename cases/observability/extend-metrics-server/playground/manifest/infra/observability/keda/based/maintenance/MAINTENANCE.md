# Maintenance Keda kustomize bundle

The manifests for keda deployments in this module was generated using `kubernetes-split-yaml`.
To prepare a new release of this package:

1. Get the new upstream release [kedacore/keda](https://github.com/kedacore/keda/releases).

```(shell)

go install  github.com/mogensen/kubernetes-split-yaml@latest
./kubernetes-split-yaml --outdir $PWD/resources keda-2.10.1-core.yaml
```