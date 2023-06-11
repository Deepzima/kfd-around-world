# Network Extensions Cases

Wants to show how extend network capabilities of a Kubernetes cluster using cilium from [Networking Module](https://github.com/sighupio/fury-kubernetes-networkinf) of [KFD](https://github.com/sighupio/fury-distribution),
That means you can find patch or elements may are unusual or unconventional for a standard [KFD](https://github.com/sighupio/fury-distribution).

## Main cases:

- `cilium/multi-cluster`: the idea beind it's doing multi-cluster capabilities using `cilium` from `networking` module plus all features from [cilium-release-1.13](https://isovalent.com/blog/post/cilium-release-113/).
- `cilium/gateway`: the idea beind it's using the new gateway API implementation using `cilium` from `networking` module plus supported cases `traffing-splitting` etc.
- `istio/multi-cluster`: the idea beind it's doing multi-cluster capabilities using `istio` from `service-mesh` module and particular patches we can do in a production environment.
- `istio/advance-traffic-management`: the idea beind it's try to build an implementantion where we can add `filters` implementation,`envoy hardening`, `Zone aware routing` etcetc patching `istio` from `service-mesh` module.
