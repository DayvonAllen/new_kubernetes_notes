## Kubernetes
- It's a container orchestrator
- `container orchestration` - make many servers or nodes act like one.
  - designed to automate change and monitor the state of things and ensure that everything is the state that you expect it to be.
  - If change rate and amount of servers are a huge concern then you should consider `container orchestration`.
- `state` - data created and used by your application which must not be lost. 
---

## Basic Terms
- `Kubernetes`(or `k8s`) - the whole orchestration system.
- `Kubectl`(official pronunciation: `cube control`) - CLI used for configuring k8s and managing apps.
- `Node`(or `worker`) - a single server in the k8s cluster.
- `kube proxy` - belongs to `nodes` and controls the networking.
- `Kubelet` - k8s agent running on nodes that allow the nodes to talk back to the k8s master or control plane.
- `Control Plane`(or `master`) - is a set of containers that manage the cluster.
  - Includes `API server`, `scheduler`, `controller manager`(make sure the state is correct), etcd, coreDNS and more.
  - Each container in the `control plane` does one thing and does it well, for example one will be the `controller manager`
    - another will be the `scheduler` etc.
- `Pod` - one or more containers running together on one `Node`.
  - Basic unit of deployment. Containers are always in pods.
- `Controller` - used for creating/updating pods and other objects. 
  - There are many types of controllers:
    - `Deployment`
    - `ReplicaSet`
    - `StatefulSet`
    - `DaemonSet`
    - `Job`
    - `CronJob`
    - and many more...
- `Service` - network endpoint to connect to a pod.
  - A persistent endpoint in a cluster so everything else can access the specific DNS and port.
- `Namespace` - filtered group of objects in clusters, limits scope. Virtual clusters
- `Secrets`
- `ConfigMaps`
- `CoreDNS` - allows us to resolve services by name.
- Service Types:
  - `Cluster IP`(default) - only pods in the cluster can reach this endpoint(there isn't any outside traffic)
  - `NodePort` - can access the pod through their IP on a certain port.
  - `LoadBalancer`(LB) - controls a LoadBalancer endpoint external to the cluster.
    - Only available when infrastructure provider gives you an LB(AWS, GCP, Azure etc.).
  - `ExternalName` - Adds CNAME DNS record to CoreDNS only(used when your cluster wants to talk to outside services.)
  - `Ingress` - load balances for HTTP requests.
    - `Nginx` - popular `ingress` controller for k8s.
    - `Traefik` - `go`  implementation of an `ingress` controller for k8s.
- `manifest` - describes an API object(deployment, job, secret) 
  - Each manifest needs four parts:
    - `apiVersion` - resource api version
    - `kind` - k8s resource
    - `metadata` - only the name is required but other stuff can be added. 
      - `Labels` - for identifying a resource
      - `annotations` - for complex configuration.
    - `spec` - where most of the important stuff goes.
---