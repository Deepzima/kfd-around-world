# Replace with actual expected context name
# CONTEXT?=my-cluster

# define check
# 	kubectl config current-context | grep $(CONTEXT) || (echo ERROR: wrong cluster && exit 1)
# endef

# To target a single module: "make CMD MODULE=<module_name>"
# If no MODULE is passed, the global kustomization.yaml is used
MODULE="."

.PHONY: build
build:
 @kustomize build $(MODULE)

.PHONY: diff
diff:
 source $(creds) && kustomize build $(MODULE) | kubectl diff -f - 

.PHONY: deploy
deploy:
 source $(creds) && kustomize build $(MODULE) | kubectl apply -f - | grep -v unchanged

.PHONY: dep
dep:
	furyctl vendor -H