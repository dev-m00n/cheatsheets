# Kind configuration cheatsheet
```yaml
# Only 2 Required fields
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4

# Optional fields from here
name: someGreatClusterName

## Configure nodes, mandatory if you want to have multi-node k8s cluster
nodes:
  ### Each role has own configuration by role
- role: control-plane # Role is mandatory if you configure nodes

  # Optional fields for this role from here
  
  ## Node image name, You are even able to make your node image and specify here
  image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55

  ## Mount Host path to node. Mac/Windows user need to check Preferences -> Resources -> File Sharing in Docker desktop
  extraMounts:
  - hostPath: /path/to/my/files/
    containerPath: /files 
    readOnly: true
    selinuxRelabel: false
    propagation: HostToContainer # None(default), HostToContainer or Bidirectional. What is propagation? See https://kubernetes.io/docs/concepts/storage/volumes/#mount-propagation

  ## Port mapping from Host to Node
  extraPortMappings:
  - containerPort: 80
    hostPort: 8080
    listenAddress: "127.0.0.1" # Default: 0.0.0.0
    protocol: TCP # TCP(default), UDP or SCTP
- role: worker # You can specify above configuration in worker node
- role: worker
- role: worker
```