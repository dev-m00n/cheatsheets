# Kind cheatsheet

## Creating cluster
Easist way to start. 
```bash
$ kind create cluster # It's same with $ kind create cluster --name kind
```

### Create cluster with configuration
```bash
$ kind create cluster --config path/my_config_file.yml
```
See more config detail [here](./config_detail.md)  
#### Samples
- [Multinode cluster](./sample/multinode_basic.yaml)

#### Example
```bash
$ kind create cluster --config kind/sample/multinode_basic.yaml
Creating cluster "multinode.local.cluster" ...
 ✓ Ensuring node image (kindest/node:v1.24.0) 🖼
 ✓ Preparing nodes 📦 📦 📦 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
 ✓ Joining worker nodes 🚜
Set kubectl context to "kind-multinode.local.cluster"
You can now use your cluster with:

kubectl cluster-info --context kind-multinode.local.cluster

Have a question, bug, or feature request? Let us know! https://kind.sigs.k8s.io/#community 🙂

$ kubectl config get-contexts
CURRENT   NAME                           CLUSTER                        AUTHINFO                       NAMESPACE
*         kind-multinode.local.cluster   kind-multinode.local.cluster   kind-multinode.local.cluster

$ kubectl cluster-info --context kind-multinode.local.cluster
Kubernetes control plane is running at https://127.0.0.1:57463
CoreDNS is running at https://127.0.0.1:57463/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
```

## Listing cluster
```bash
$ kind get clusters
kind
multinode.local.cluster
```

## Deleting cluster
```bash
$ kind delete cluster --name kind # Delete specific cluster
Deleting cluster "kind" ...

$ kind delete clusters kind multinode.local.cluster # Delete multiple clusters
Deleted clusters: ["kind" "multinode.local.cluster"]
```

## Dump all logs in cluster to specific path
```bash
$ kind export logs --name multinode.local.cluster some/log/path
```