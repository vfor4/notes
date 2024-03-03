![[Pasted image 20240121175321.png]]

#### API OBJECT
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
10. 

