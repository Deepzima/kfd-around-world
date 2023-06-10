kubernetes-version?=v1.26.3
cluster-name?=cluster-one
profile?=cluster-one
driver?=hyperkit
container-runtime?=docker
memory?=4096
cpu?=2
cni?=calico
nodes?=1
addons?=ingress


.PHONY: delete
delete:
	minikube delete --profile $(profile) 
	minikube cache delete

.PHONY: start
start:
	minikube start --profile $(profile) 

.PHONY: stop
stop:
	minikube stop --profile $(profile) 

.PHONY: setup
setup: minikube-stand addons

.PHONY: minikube-stand
minikube-stand:
	minikube start \
		--profile $(cluster-name) \
        --kubernetes-version $(kubernetes-version) \
        --driver $(driver) \
		--container-runtime $(container-runtime) \
        --memory $(memory) \
        --cpus $(cpu) \
		--cni $(cni) \
        --nodes $(nodes) \
        --embed-certs 

.PHONY: addons
addons:
	@echo $(addons)
	# minikube addons enable $(addons)