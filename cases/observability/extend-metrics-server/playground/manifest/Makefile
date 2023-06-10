# Stage
.PHONY: build
build:
 @kustomize build ./stage

.PHONY: diff
diff:
 source $(creds) && kustomize build ./stage | kubectl diff -f - --kubeconfig=$(kubecfg) 

.PHONY: deploy
deploy:
 source $(creds) && kustomize build ./stage | kubectl apply -f - --kubeconfig=$(kubecfg) | grep -v unchanged