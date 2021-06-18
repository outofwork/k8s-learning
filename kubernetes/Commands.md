Kubernetes Study:

	kubectl get all
	kubectl create -f helloworld.yaml
	kubectl expose deployment helloworld --type=NodePort

Delete:

	kubectl delete service helloworld
	kubectl delete deployment helloworld
	kubectl delete replicaset helloworld-66f646b9bb

	kubeclt delete service --all

	kubectl get namespace
		NAME              STATUS   AGE
		default           Active   67m
		kube-node-lease   Active   67m
		kube-public       Active   67m
		kube-system       Active   67m


Labels:

	kubectl get pods --show-labels

	kubectl label pod/<pod-name> app=labelApp --overwrite   // app=labelApp is the label, change as per your

	Search with Labels:
		kubectl get pods --selector env=production --show-labels

Service:

	kubectl get service/helloworld -o yaml

Health Check:

	kubectl describe

Update Pod:

	kubectl create -f helloworld.yaml --record=true
	kubectl set image deployment/navbar-deployment helloworld=karthequian/helloworld:blue
	kubectl get rs
	kubectl rollout undo deployment/navbar-deployment

DEBUG:

	kubectl logs <pod-name>
	kubectl describe

CONFIG_MAP:  - configMapkeyRef to be added in yaml file.

	kubectl create configmap logger --from-literal=log_level=debug

	kubectl get configmap
		NAME               DATA   AGE
		kube-root-ca.crt   1      162m
		logger             1      7s

	kubectl get configmaps logger
	kubectl get configmap/logger -o yaml

SECRETS:

	kubectl create secret generic apikey  --from-literal=api_key=123123
	kubectl get secrets
	kubectl get secret/apikey -o yaml

JOBS:

	kubectl get jobs
	kubectl get cronjobs

DAEMONSETS:

	kubectl get daemonsets

Cluster Command:

	minikube service helloworld
	minikube addons list
	minikube addons enable dashboard
