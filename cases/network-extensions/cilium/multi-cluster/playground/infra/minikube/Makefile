kubernetes-version?=v1.25.3
cluster-name?=cluster-one
profile?=cluster-one
driver?=parallels
container-runtime?=containerd
memory?=8000
cpu?=3
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

.PHONY: multiton
multi-kube2:
	@singleton cluster-name=cluster-one 
	# @singleton cluster-name=cluster-two 
	CLUSTER1_IP?= minikube ip --profile cluster-one 
	@echo $(CLUSTER1_IP)

	# sudo iptables -I FORWARD -s $(CLUSTER1_IP)/16 -d $(CLUSTER2_IP)/16 -j ACCEPT
	# sudo iptables -I FORWARD -s $(CLUSTER2_IP)/16 -d $(CLUSTER1_IP)/16 -j ACCEPT
    # - --- - MAC WAY :D - --- - #


.PHONY: singleton
setup: minikube-stand-nocni addons

.PHONY: minikube-stand-nocni
minikube-stand-nocni:
	minikube start \
		--profile $(cluster-name) \
        --kubernetes-version $(kubernetes-version) \
        --driver $(driver) \
		--container-runtime $(container-runtime) \
        --memory $(memory) \
        --cpus $(cpu) \
		  --network-plugin=cni \
        --nodes $(nodes) \
        --embed-certs 

.PHONY: addons
addons:
	@echo $(addons)
	minikube profile $(cluster-name)
	minikube addons enable $(addons)