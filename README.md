Grep for info on an image
```
kubectl describe deployments.apps deployment_name | grep -I image
```
Create a deployment named "httpd-frontend" using the httpd:2.4-alpine image
```
kubectl create deployment httpd-frontend --image=httpd:2.4-alpine
```
Create a deployment named blue with the nginx image and 3 replicas
```
kubectl create deployment blue --image=nginx --replicas=3
```
Edit a depoyment
```
kubectl edit deployment blue
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
```
kubectl scale --replicas=5 rs/new-replica-set
```
Changing namespace context
```
kubectl config set-context $(kubectl config current-context) --namespace=finance
```
```
kubectl config set-context --current --namespace=twistlock 
```
Specify namespace to list pods
```
kubectl get pods --namespace-default
```
Get pods in all namespaces
```
kubectl get pods --all=namespaces
```
List namespaces
```
kubectl get ns
```
List namespaces (no headers)
```
kubctl get ns --no-headers 
```
Specify namespace to get pods
```
kubectl -n namespace  get pods
```
Create a Service
```
kubectl create -f service-definition.yml
```
Get Service info
```
kubectl get services or svc
```
Describe Services
```
kubectl describe service or svc servicename
```
Deployments
```
kubectl get deployments
```
Find image name in a deployment
```
kubectl descripe deplyments.apps deployment_name | grep -i image
```
Create a new service (command) 
```
Kubectl expose deployment simple-webapp-deployment --name=webapp-service --target-port=8080 --type=NodePort --port=8080 --dry-run=client -o yaml > svc.yaml
```
Create a new service (file)
```
kubectl apply -f svc.yaml
```
List the kube-system pods
```
kubectl get pods --namespace kube-system
```
Get pods for the kube-system namespace
```
kubectl -n kube-system get pods
```
Show prod label in all environments
```
kubectl get all --selector env=prod
```
Count number pods in dev environment
```
kubectl get pods -l env=dev --no-headers | wc -l
```
Get all items with prod label
```
kubectl get all -l env=prod --no-headers | wc -l
```
List multiple labels on a pod
```
kubectl get pods -l env=prod,bu=finance,tier=frontend
```
Create yaml file for pod named bee
```
kubectl run bee --image=nginx --restart=Never --dry-run -o yaml > bee.yaml`
```
Show labels
```
kubectl get nodes node01 --show-labels
```
Apply label 
```
kubectl label nodes node01 color=blue
```
Create Deployment
```
kubectl create deployment blue --image=nginx
```
Create Deployment - Dry Run \ yaml
```
kubectl create deployment red --image=nginx --dry-run -o yaml > red.yaml
```
Scale Deployment 
```
kubectl scale deployment blue --replicas=6
```
Produce yaml from an existing deployment
```
kubectl get deployments.apps blue -o yaml > blue.yaml
```
Create yaml file from a pod
```
kubectl get pods elephant -o yaml > pod.yaml
```
Set Affinity - Edit a Deployment
```
kubectl get deployment.apps blue -o yaml > blue.yaml
```
Add Affinity Config - (Under template > spec)
```
affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: color
            operator: In
            values:
            - blue          
```
Delete previous deployment and create new with the yaml file
```
kubectl apply -f blue.yaml
```
Daemonsets
```
kubectl get ds --all-namespaces
```
Create yaml file, then edit and changed items to create a Daemonset
```
kubectl create deployment elasticsearch --image=k8s.gcr.io/fluentd-elasticsearch:1.20 --dry-run=client -o yaml > elastic.yaml
```
Get logs from a pod
```
kubectl logs webapp-1
```
View containers on pod to view logging
```
kubectl logs webapp-2 -c
```
Stream events on a pod (One container)
```
kubectl logs -f event-simulator-pod
```
Stream events on a pod (Specific container)
```
kubectl logs -f event-simulator-pod event-simulator
```
Rolling Updats and Rollbacks
Create
```
kubectl create -f deployment-definition.yml
```
Get
```
kubectl get deployments
```
Update
```
kubectl apply -f deployment-definition.yml
```
```
kubectl set image deployment/myapp-deployment nginx=nginx:1.9.1
```
Status
```
kubectl rollout status deployment/myapp-deployment
```
```
kubectl rollout history deployment/myapp-deployment
```
Rollback
```
kubectl rollout undo deployment/myapp-deployment
```
Edit Deployment
```
kubectl edit deployments.app frontend
```
Create Config Map
```
kubectl create cm webapp-config-map --from-literal=APP_COLOR=darkblue
```
Explain yaml for pods (Available for other services as well
```
kubectl explain pods
```
Get static pod info
```
cat /var/lib/kubelet/config.yaml
```





            
