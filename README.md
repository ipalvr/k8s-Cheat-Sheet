Grep for info on an image
```
kubectl describe deployments.apps deployment_name | grep -I image
```
Create a deployment named "httpd-frontend" using the httpd:2.4-alpine image
```
kubectl create deployment httpd-frontend --image=httpd:2.4-alpine
```
Scale the number of replicas to 3 in the httpd-frontend deployment
```
kubectl scale deployment --replica=3 httpd-frontend
```
Create pod from command line
```
kubectl run redis --image=redis
```
kubectl run redis --image=redis --dry-run=client -o yaml pod.yaml (creates a pod yaml file, doesn't build it)
```
kubectl apply -f pod.yaml (This command will create pod)
```
Get replicaset
```
kubectl get replicaset
```
Deescribe replicaset
```
kubectl describe rs/new-replica-set
```

Scale a replica set
kubectl scale --replicas=5 rs/new-replica-set

Changing namespace context
kubectl config set-context $(kubectl config current-context) --namespace=finance

Specify namespace to list pods
Kubectl get pods --namespace-default

Get pods in all namespaces
kubectl get pods --all=namespaces

List namespaces
Kubectl get ns
Kubctl get ns --no-headers (removes the header row)

Specify namespace to get pods
Kubectl -n namespace  get pods

DNS (pod.namespace.service.cluster.local)
Mysql.connect("db-service.dev.svc.cluster.local")

Services
Create
Kubectl create -f service-definition.yml
Get
Kubectl get services or svc
Describe Services
kubectl describe service or svc servicename

Deployments
Kubectl get deployments

Find image name in a deployment
Kubectl descripe deplyments.apps deployment_name | grep -i image

Create a new service 
Kubectl expose deployment simple-webapp-deployment --name=webapp-service --target-port=8080 --type=NodePort --port=8080 --dry-run=client -o yaml > svc.yaml
Kubectl apply -f svc.yaml

List the kube-system pods
kubectl get pods --namespace kube-system

Get pods for the kube-system namespace
Kubectl -n kube-system get pods

Show prod label in all environments
kubectl get all --selector env=prod

Count number pods in dev environment
kubectl get pods -l env=dev --no-headers | wc -l

Get all items with prod label
kubectl get all -l env=prod --no-headers | wc -l

List multiple labels on a pod
Kubectl get pods -l env=prod,bu=finance,tier=frontend

Create yaml file for pod named bee
Kubectl run bee --image=nginx --restart=Never --dry-run -o yaml > bee.yaml

Show labels
Kubectl get nodes node01 --show-labels

Apply label 
Kubectl label nodes node01 color=blue

Create Deployment
Kubectl create deployment blue --image=nginx

Scale Deployment 
Kubectl scale deployment blue --replicas=6

Produce yaml from an existing deployment
Kubectl get deployments.apps blue -o yaml > blue.yaml
