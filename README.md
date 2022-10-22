## Kubernetes Notes

### Workflow and componenets in kubernetes

`Worker Node`:
  - `Container Runtime`: For containers to run.
  - `Kubelet`: For interacting with container and Node.
  - `Kube Proxy`: Forwards requests from services to pod. So the request get forwarded to the next nearest healthy pod.

`Master Node`:
  - `API Server`: Cluster gateway (UI/CLI) which gets initial request or queries. (Request -> API server -> Validate -> Forward to other processes).
  - `Scheduler`: (Request -> API server -> Validate -> Scheduler \[decides where to put the pod (on which node)\] -> Kubelet (Execute)). Scheduler just decides on which node new pod should be scheduled. Kubelet get the request from scheduler and execute the request.
  - `Controller Manager`: Detect cluster state changes like crashing of pods. (controller manager -> scheduler).
  - `etcd`: Key value store of cluster state. It is the cluster brain. It store cluster health, available resources, state change, it do not store application data.

***Deployment -> Replicaset -> Pod -> Container***

## Commands  
#### Get Status of different k8s components
- `kubectl get nodes | pod | services | replicaset | deployment`

#### CRUD Commands
##### *Create a deployment*
- `kubectl create deployment <deployment name> --image=<IMAGE> [--dry-run] [options]`
  > `kubectl create deployment nginx-deployment --image=nginx`

##### *Edit a deployment*
- `kubectl edit deployment <deployment name>`
  > `kubectl edit deployment nginx-deployment`

##### *Delete deployment*
- `kubectl delete deployment <deployment name>`

#### Debugging Pods
##### *Get additional information about pod*
- `kubectl describe pod <pod name>`

##### *Get pod logs*
- `kubectl logs <pod name>` 

##### *Login into a pod*
- `kubectl exec -it <pod name> -- bin/bash`

#### Apply/Delete configuration
- `kubectl apply -f <YAML FILE>`
- `kubectl delete -f <YAML FILE>`

#### Configuration File:
```
1. Metadata.
2. Specification.
3. Status (Automatically adds by k8s)/
```

