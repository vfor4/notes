![[Pasted image 20240121175321.png]]

## API OBJECT
- Node: một server hoặc máy ảo hoặc máy vật lý, bao gồm control plane node và worker node
- Pod: một container hay nhiều container. Smallest K8s wordload object. It is the unit of deployment
	- Cùng scheduled
	- Cùng network
	- Cùng volumes
	![[Pasted image 20240302161901.png]]
- Deployment: dùng để deploy or upgrade Pods
	- rolling update, once the rolling update has completed, Deloyment will show both Replicates A and B, where A is scaled to 0, B is scaled to 3
	- The Deployment keep its prior configuration. If performance of the new B is not satisfactory
	  ![[Pasted image 20240303110624.png]]
- ReplicaSet: tạo hoặc monitor Pods. replication and self-healing
	- distinct in identity - Pod name, IP address, Pod object
- Service: stable network endpoint
	- ServiceType: decide where the service can to be accessed
		- ClusterIp (Default) - scope only within cluster
		- NodePort (30000-32767): mapped to service from all worker nodes
			![[Pasted image 20240304213158.png]]
		- LoadBalancer: delegate the loadblancer to cloud provider
		- ExternalIp: 
		- ExternalName
	- Multi-Port Service: container can listen on more than one port
	
- Ingress: Mange external access to **Services**
- Namespace: Used to group, on some levels isolates resources in a K8s cluster. or we can image it as virtual sub-clusters
- ConfigMap: Store configuration that's used by container. 
- Secret: Store sensitive data
- DeamonSet: Make sure one Pod is runing on each node of nodes in the cluster. To ensure that we have a specific type of Pod running on all Nodes at all the times. Use to collect monitoring data from all Nodes, storage, network, proxy 
- Labels: key-value pairs, controller use labels to logically group objects

![[Pasted image 20240121214612.png]]![[Pasted image 20240123220651.png]]
## KUBERNETES COMMANDS
1. debug
```
kubectl describe pods name-of-pod
```
2. create cluster
```
minikube start --nodes=3 --driver=docker --kubernetes-version=v1.24.4\ 
--container-runtime=cri-o --profile minidock
```
3. create deployment
```
kubectl create deployment mynginx --image=nginx:1.15-alpine
```
4. scale replicaset
```
kubectl scale deploy mynginx --replicas=3
```
5. show rollout history
```
kubectl rollout history deploy mynginx
```
6. rolling update
```
kubectl set image deployment mynginx nginx=nginx:1.16-alpine
```
8. undo revision
```
kubectl rollout undo deployment mynginx --to-revision=1
```
10. check if our service expose
```
minikube service --all
```
11. edit service
```
kubectl edit svc service-name
```
12. get pod by label
```
kubectl get pods -l label-name
```
13. delete deployemtns
```
kubectl delete deployments deploy-name
```
15. f
16. 

## LOAD BALANCE
Kube-proxy with iptable implement the load-balancing. The endpoint will be randomly selected out of the replicas. Use <span style="color:#92d050">traffice policies</span> to get better outcomes. 2 types: Cluster, Local
## SERVICE DISCOVERY
- Environment Variable
	![[Pasted image 20240304211730.png]]
- DNS
	- it format my-svc.my-namespace.svc.cluster.local
	- service which the same namespace find other service just by thier name
	- this is the most common and recommended solution

## HOW TO DEPLOY APPS ON K8S
## LIVENESS AND READINESS PROBES
- Be careful liveness and readiness overlap
- If container in the Pod is dead (not live anymore), kubelet are gonna restart it
- Liveness can be set: Command, Http request, Tcp
![[Pasted image 20240305213653.png]]

## VOLUMES
- plenty of volume types
- to mange well these types, we can use PersistentVolume
![[Pasted image 20240311212709.png]]
## CONFIGMAP API
- create ConfigMap
```
kubectl create configmap my-config \
  --from-literal=key1=value1 \  
  --from-literal=key2=value2
``` 
- display ConfigMap details
```
kubectl get configmaps my-config -o yaml
```
- we can create ConfigMap from manifest file
- create from properties
```
kubectl create configmap permission-config \ 
--from-file=<path/to/>permission-reset.properties
```
- Use ConfigMaps Inside Pods: As Environment Variables
- Use ConfigMaps Inside Pods: As Volumes
## SECRET API
- create 
```
kubectl create secret generic my-password \  
  --from-literal=password=mysqlpassword
```
- create from manifest:
	- data (need to be encoded by base64)
	- stringDate: raw string
- use secret
	- :))) easy lemon 
## INGESS
For the LoadBalancer we may not want to use it for every services. Manage NodePort. 
Ingress represent another layer of abstraction, deployed in front of the Service Api resources. unified method of managing access to our application

> [!NOTE] k8s.io
> An Ingress is a collection of rules that allow inbound connections to reach the cluster Services

![[Pasted image 20240312210736.png]]
#xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
![[Pasted image 20240312211211.png]]

## INGRESS CONTROLLER
An Ingress **defines** what needs to be done, while the Ingress Controller **actively does it**.
- kubernetes.io/ingress.class: "nginx"** (for an nginx ingress controller).